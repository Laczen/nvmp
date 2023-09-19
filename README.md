<!--
  Copyright (c) 2022 Laczen

  SPDX-License-Identifier: Apache-2.0
-->
# NVMP - non volatile memory and partitions

Unified library for working with non volatile memory and their partitions in
zephyr. The library provides 3 basic routines: read, write and erase that can
be utilized on several kinds of non volatile memory e.g. eeprom, retained_mem,
flash, ... more to come.

This library can be used to:
a. Work with images on non volatile memory,
b. Work with shared data between a bootloader and firmware,
c. Simplify storage solutions like littlefs, fatfs, ... to work on any type of
   non volatile memory,

# Documentation

The API for nvmp is documented in the header file
[nvmp.h](./zephyr/include/zephyr/subsys/nvmp/nvmp.h).

# Zephyr module

The non volatile memory and partitions library is provided as a zephyr module
for easy integration in the zephyr build environment. To enable nvmp as a zephyr
module the submanifest file (`zephyr/submanifests/example.yaml`) can be altered:

```
# Example manifest file you can include into the main west.yml file.
#
# To make this work, copy this file's contents to a new file,
# 'example.yaml', in the same directory.
#
# Then change the 'name' and 'url' below and run 'west update'.
#
# Your module will be added to the local workspace and kept in sync
# every time you run 'west update'.
#
# If you want to fetch a particular commit rather than the main
# branch, change the 'revision' line accordingly.

manifest:
  projects:
    - name: nvmp
      url: https://github.com/Laczen/nvmp
      revision: main
```

After the project has been added calling `west update` ads the nvmp directory to
the zephyr workspace. If your workspace is called `zephyr_project` tests can be
found under `zephyr_project/nvmp/zephyr/tests/subsys/nvmp`.`
