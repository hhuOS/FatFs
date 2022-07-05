# FatFs (Generic FAT Filesystem Module)

This repository contains the FatFs library, developed by ChaN ([Website](http://elm-chan.org/fsw/ff/00index_e.html)), for use in hhuOS.
The source code has not been changed in any way, except for ffconf.h, which contains the following changes:

```bash
# Disable real time clock functionality
sed -i "s/#define FF_FS_NORTC		0/#define FF_FS_NORTC		1/g" "ff/source/ffconf.h"
# Set code page to 437 (U.S.)
sed -i "s/#define FF_CODE_PAGE	932/#define FF_CODE_PAGE	437/g" "ff/source/ffconf.h"
# Enable LFN support
sed -i "s/#define FF_USE_LFN		0/#define FF_USE_LFN		1/g" "ff/source/ffconf.h"
# Enable f_mkfs() function
sed -i "s/#define FF_USE_MKFS		0/#define FF_USE_MKFS		1/g" "ff/source/ffconf.h"
# Set the amount of volumes to 10 (maximum)
sed -i "s/#define FF_VOLUMES		1/#define FF_VOLUMES		10/g" "ff/source/ffconf.h"
```

## FatFs Module Source Files R0.14b

### FILES

| File          | Description                                                               |
|---------------|---------------------------------------------------------------------------|
| 00readme.txt  | This file.                                                                |
| 00history.txt | Revision history.                                                         |
| ff.c          | FatFs module.                                                             |
| ffconf.h      | Configuration file of FatFs module.                                       |
| ff.h          | Common include file for FatFs and application module.                     |
| diskio.h      | Common include file for FatFs and disk I/O module.                        |
| diskio.c      | An example of glue function to attach existing disk I/O module to FatFs.  |
| ffunicode.c   | Optional Unicode utility functions.                                       |
| ffsystem.c    | An example of optional O/S related functions.                             |

  Low level disk I/O module is not included in this archive because the FatFs
  module is only a generic file system layer and it does not depend on any specific
  storage device. You need to provide a low level disk I/O module written to
  control the storage device that attached to the target system.

