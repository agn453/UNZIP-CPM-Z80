# UNZIP for CP/M Z80

This is UNZIP for CP/M in Zilog Z80 assembler.

**LATEST NEWS:**  Further speed optimisations.

The latest release is V1.5-4 (CP/M) or V1.8-6 (Z-system) and may be
downloaded in CP/M library file format from -

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip154.lbr

or

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip186.lbr

Simeon Cran's version (UNZIPZ) for Z-system has also been updated as V0.4-1
and is available from -

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzipz04.lbr

Support has been added for the Deflate algorithm (since V1.5-2 and V1.8-2)
so that decompression of archives created with MS-DOS PKzip 2.04g
and Info-ZIP (the open-source version of ZIP that's used by
Unix/Linux and included with Microsoft Windows and macOS)
can now be extracted.

(Older versions of the CP/M UNZIP program can _only_ be used to unpack
ZIP files whose contents have been compressed or stored by PKZip for
MS-DOS Version 1.x.)


## Bug Fixes and Enhancements

In reverse chronological order.

### December 9, 2020

Lars Nelson has been busy!  He's updated Simeon Cran's UNZIPZ to include
the optimised bit manipulation and the table-based CRC routines by Russell
Marks to give a significant speed improvement (estimated 45% faster than
the UNZIPZ V0.3-4 version).  This latest version is designated V0.4-1
and can be downloaded from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzipz04.lbr

Also, Lars has updated the Z-system version to produce a .ZIP file
contents listing in a format that includes compressed/uncompressed
file size, compression method, modification time-stamp and the 32-bit CRC.

This version V1.8-6 can be downloaded from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip186.lbr


### November 30, 2020

Lars Nelson has migrated the updates into Simeon Cran's UNZIPZ version
so that it also now supports the UnDeflate algorithm.  The source files
and a prebuilt CP/M .COM file have been included in the unzip folder.
This new version has been designated at V0.3-2.  As usual you can grab
these files in the CP/M library file from -

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzipz03.lbr


### November 18, 2020

Lars Nelson has incorporated file datestamping to set each extracted
file's date on CP/M formatted disks with Time-Stamps enabled.  This should work
with DateStamper, ZSDOS, CP/M Plus (and ZPM3) and MP/M.

The Z-System aware version number has been bumped to V1.8-5.

There's one remaining issue involving the calculation of a cyclic redundancy
check (CRC) value for files that are not being extracted (i.e. listing contents
of a .ZIP file).  In the older V1.5-2 (and later revisions) Martin removed
the CRC calculation when listing a .ZIP file's contents.
Lars has tried to restore this code in V1.8-5 but it is calculating the
wrong value for files not being extracted.  As a work-around, these skipped
files are now being treated as "Stored" files for now.

You can grab this latest version in a CP/M format library file from -

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip185.lbr


### November 11, 2020

Lars Nelson has fixed an UnDeflate issue as well as added code to strip
pathnames from filenames and clear bit 7 of filename characters.
This version builds with the supplied UNZIP184.SUB (for ZSM4 and DR LINK)
or SLR184.SUB (using SLR Z80ASM and SLRNK).

Once again, I've updated the source and library file (still at v1.8-4)
so fetch a new copy if you've an older version.

Also a later Z-System version of ZIPDIR has been added.  Download from
[ZIPDIR14](https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/zipdir14.lbr)


### November 4, 2020

Lars has fixed the "zero-length file CRC error" for the Z-system v1.8-4
version.  Updated UNZIP184.Z80, the binary and library for this version only.
Also included an updated version of
[ZIPDIR](https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/zipdir.lbr)
to correctly report .ZIP file entries compressed with the Deflate method.


### October 31, 2020

Lars Nelson has ported the v1.5-4 updates to the Z-system version (with
the exception of the >255 character filename check).  As usual, the 
individual files are in the unzip folder or grab the v1.8-4 version
in a CP/M .LBR file from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip184.lbr

I've also included the Z-system libraries in their original binary distribution
format .LBR files (should you wish to rebuild from source code).  They are

* [LIBS45A.LBR](https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/LIBS45A.LBR) - the
library containing .REL versions of SYSLIB, Z3LIB and DSLIB in both
Microsoft M80/DR LINK and SLRNK file formats.

* [LBRHL45A.LBR](https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/LBRHL45A.LBR) - the
help files for LIBS45A.LBR

* [ZSLIB36.LBR](https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/ZSLIB36.LBR) - the
supplemental routines for programmers.

For testing, I re-linked UNZIP184.COM natively under Z3PLUS Vers. 1.02
(the Z-system variant for CP/M-Plus) using the ZSM4 assembler and Digital
Research's LINK using the submit file UNZIP184.SUB.


### October 30, 2020

Lars Nelson has ported the v1.5-2 bug fixes and UnDeflate enhancements
to the Z-system (ZCPR 3.x) branch, resulting in v1.8-2.

Based on initial testing, this version (using a 2K buffer and Z-system
libraries) has better performance than v1.5-2 (and later).

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip182.lbr


### October 18, 2020

Some further speed optimisations by Russell Marks.

* Further slight optimisations to bit-readers,

* Backport some unzip 1.8 changes (buffer-overrun fixes, bit 7 strip on
output filenames, less frequent ^C checking, and low-memory message),
and add various comments.

* Use self-modifying code with an unrolled end loop in rdbybits,
and add a "rd1bit" macro, for about a 12% speed improvement
on overall extraction time compared to version 1.5-3.

* Fix long-filename buffer overrun, for filenames longer than
255 characters.

* Backport Howard Goldstein's buffer-overrun fixes from
unzip 1.8 - previously, a 255-byte buffer was repeatedly used
to read up-to-65535-byte inputs.

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip154.lbr


### October 15, 2020

Russell Marks has contributed speed optimisations to the UnDeflate
algorithm to significantly boost performance (by more than 30%).

* A new routine rdbybits now processes eight or fewer bits.

* Checks whether the TPA size is large enough for UNZIP's tables

* Use a table-based CRC algorithm.  This increases the CP/M
binary size by about 1Kbyte.

I've bumped the version number to 1.5-3 and the latest
updated sourcefile as *UNZIP153.Z80*.  The source and CP/M binary
are also available in a CP/M format library file from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip153.lbr


### September 2020

Martin has posted some more updates and added support to decompress
ZIP file entries compressed with the Deflate algorithm.

The changelog is -

* Fix extraction of zero-length files.

* Skip to the next file header if the compression method is unknown

* Fix readbits when a full word (16 bits) is read - in preparation
for implementing the unDeflate algorithm.

* Fix mis-ordering of variables.  Code makes the assumption
that "bitbuf" is the byte before "bleft".

* Allow the relocation of the input buffer.

* Make the output buffer size dynamic.

* Implement the UnDeflate algorithm - based on the work by
Keir Fraser's HiTech-C code at
https://github.com/keirf/Amiga-Stuff/blob/master/inflate/degzip_portable.c

You'll find the updated sourcefile as *UNZIP152.Z80* which you
can also get in a CP/M format library file from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip152.lbr


### June 2020

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

The new Z80 CP/M executable has been built using Hector Peraza's ZSM4
assembler(1) and Digital Research's LINK as *UNZIP151.COM* using the
following commands -

```
zsm4 =unzip151.z80
link unzip151
```

A new library file (without compressed entries) containing the fixes
is _unzip151.lbr_ and can be downloaded from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip151.lbr


Also, the new Z-system (ZCPR 3.x) UNZIP Version 1.8-1 is in the
library _unzip181.lbr_ and can be downloaded from

https://raw.githubusercontent.com/agn453/UNZIP-CPM-Z80/master/unzip/unzip181.lbr

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


## Background

Files have been extracted from the following distribution archives -

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


## Notes

Other Zilog Z80 assemblers/linkers can also be used (e.g. SLR Z80ASM/SLRNK
or even Microsoft M80/L80) - however, they may create
a .COM file with data segment storage included.

Also, there are other UNZIP programs for CP/M that use the same
unpacking code derived from the Version 1.2 source-code.  They
are _not fixed_.

--

(1) The source-code, documentation and executable for the
ZSM4 Z80/Z180/Z280 Macro Assembler may be obtained from
https://github.com/hperaza/ZSM4
