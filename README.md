# UNZIP-CPM-Z80
UNZIP for CP/M Z80
==================

This is UNZIP for CP/M in Zilog Z80 assembler.

It can _only_ be used to unpack ZIP files whose contents have been
compressed by PKZip for MS-DOS Version 1.x.

Files Stored without compression can always be extracted.

It DOES NOT support the memory-intensive Deflate algorithm implemented
by PKzip 2.04g and Info-ZIP (the open-source version of ZIP that's
used by Unix/Linux and included with Microsoft Windows and macOS).


Background
----------

The files have been extracted from the following distribution archives.

* UNZIP15.LBR from the Public Domain software library originally
distributed on 1-Jun-1991 as Version 1.5. I obtained this from
the Walnut Creek CP/M Software CD-ROM at

http://www.classiccmp.org/cpmarchives/cpm/Software/WalnutCD/cpm/utils/arc-lbr/unzip15.lbr

Version 1.5 incorporates modifications by Howard Goldstein on 1-Jun-1991
plus those by Bruce Morgan on 16-May-1991 (Version 1.4) and Gene
Pizzetta on 12-May-1991 (version 1.3); and includes the original
Version 1.2 source-code by David Goodenough dated 3-Jul-1990.

* UNZIP18.LBR has further modifications by Howard Goldstein for
Z-system (ZCPR 3.x) with improved file I/O performance and buffering. It
was obtained from

http://www.classiccmp.org/cpmarchives/cpm/Software/WalnutCD/jsage/znode3/uploads/unzip18.lbr


Bug Fixes
---------

Recently Martin posted two bug fixes to the unshrink and unimplode
routines in the comp.os.cpm USENET group that fix two long outstanding
bugs (1-Jun-2020 and 15-Jun-2020).

I've incorporated Martin's fixes into a new sourcefile *UNZIP151.Z80*
and also updated the original sourcecode for Version 1.2 into a renamed
file *UNZIP121.Z80*

I've also updated the Z-system Version 1.8 into a renamed source file
*UNZIP181.Z80* and rebuilt the corresponding .COM file using the
Z-system libraries extracted from LIBS45A.LBR and ZSLIB36.LBR

For a discussion of the fixes - please refer to the following
postings at the Google Groups archive of the comp.os.cpm newsgroup -

* Un-shrink fix https://groups.google.com/forum/#!topic/comp.os.cpm/B0A4x59SX44

* Un-implode fix https://groups.google.com/forum/#!topic/comp.os.cpm/rpjA1Q6RtDc

Latest Release
--------------

A new Z80 CP/M executable has been built using Hector Peraza's ZSM4
assembler(1) and Digital Research's LINK as *UNZIP151.COM* using the
following commands -

```
zsm4 =unzip151.z80
link unzip151
```

A new library file (without compressed entries) containing the fixes
is _unzip151.lbr_ and can be downloaded from

https://github.com/agn453/UNZIP-CPM-Z80/blob/master/unzip/unzip151.lbr


Also, the new Z-system (ZCPR 3.x) UNZIP Version 1.8-1 is in the
library _unzip181.lbr_ and can be downloaded from

https://github.com/agn453/UNZIP-CPM-Z80/blob/master/unzip/unzip181.lbr

The Z-system version has been built using the submit file (also included
as _UNZIP181.SUB_) -

```
; Build new version of UNZIP181 using SLR Z80ASM and SLRNK
; using Z-System libraries from LIBS45A.LBR and ZSLIB36.LBR
;
z80asm unzip181/6
; Load ASEG after CSEG - verify CSEG size is 0d7b
; and use ASEG at 0d7b + 0100 +1 to be sure
slrnk /a:0e7c,/p:100,unzip181,unzip181/n/e
```


Notes
-----

Other Zilog Z80 assemblers/linkers can also be used (e.g. SLR Z80ASM/SLRNK
or even Microsoft M80/L80) - however, they may create
a .COM file with data segment storage included.

Also, there are other UNZIP programs for CP/M that use the same
unpacking code derived from the Version 1.2 source-code.  They
are _not fixed_.  A specific example is Simeon Cran's UNZIPZ 

--

(1) The source-code, documentation and executable for the
ZSM4 Z80/Z180/Z280 Macro Assembler may be obtained from
https://github.com/hperaza/ZSM4
