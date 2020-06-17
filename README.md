# UNZIP-CPM-Z80
UNZIP for CP/M Z80
==================

This is UNZIP for CP/M in Zilog Z80 assembler.

The files have been extracted from the distribution archive
UNZIP15.LBR from the Public Domain software library originally
distributed on 1-Jun-1991 as Version 1.5.

It incorporates modifications by Howard Goldstein on 1-Jun-1991
plus those by Bruce Morgan on 16-May-1991 (Version 1.4) and Gene
Pizzetta on 12-May-1991 (version 1.3); and includes the original
Version 1.2 source-code by David Goodenough dated 3-Jul-1990.

Recently Martin posted two bug fixes to the unshrink and unimplode
routines in the comp.os.cpm USENET group that fix two long outstanding
bugs (Jun-2020).

I've incorporated Martin's fixes into a new sourcefile *UNZIP151.Z80*

For a discussion of the fixes - please see refer to the following
postings at the Google Groups archive of the comp.os.cpm newsgroup -

* Un-shrink fix https://groups.google.com/forum/#!topic/comp.os.cpm/B0A4x59SX44

* Un-implode fix https://groups.google.com/forum/#!topic/comp.os.cpm/rpjA1Q6RtDc

A new Z80 CP/M executable has been built using Hector Peraza's ZSM4
assembler(1) and Digital Research's LINK as *UNZIP151.COM* using the
following commands -

```
zsm4 unzip151,unzip151=unzip151.z80
link unzip151
```

--

(1) The source-code, documentation and executable for the
ZSM4 Z80/Z180/Z280 Macro Assembler may be obtained from
https://github.com/hperaza/ZSM4
