Introduction
------------
This is a sample project to show how to build roms for use with rBoot and how to
perform an OTA update. You can use rboot-ota.c & rboot-ota.h to add OTA support
to your own projects. There is also some commented out code in rboot_ota_start
that shows how to write non-rom files to arbitrary location on flash (e.g. for
data or embedded filesystems).
This version of the sample uses the rBoot big flash mode, which is suitable for
devices with larger flash chips, such as the ESP12.

To compile
----------
1) If you haven't already compiled rBoot do that first, with big flash enabled.
2) You will also need a compiled copy of esptool2.
3) Symlink or copy rboot.h, rboot-api.h, rboot-api.c and rboot-bigflash.c in to
   this directory.
4) Edit the Makefile to set the paths to the SDK and esptool2.
5) Set WIFI_SSID & WIFI_PWD as env vars or in the makefile.
6) Set OTA server details in rboot-ota.h
7) Flash, as below.
8) Connect a terminal and type 'help'.

All the above are available from GitHub: https://github.com/raburton

Once built simply flash with something like this:
  esptool.py --port COM2 write_flash -fs 32m 0x00000 rboot.bin 0x02000 rom.bin

Tested with SDK v2.2 on an ESP12 with 4mb flash.
