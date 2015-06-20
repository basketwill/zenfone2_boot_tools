intel-boot-tools
================

original source
http://forum.xda-developers.com/showthread.php?t=1972589
https://github.com/turl/razr-i-boot-tools

Taken source from
https://github.com/shakalaca/ZenFone-boot-tools

Just run "make" to build the tools, the usage is really simple

Code:

	$ ./pack_intel

	Usage: ./pack_intel original-image bzImage ramdisk output.img

	example: ./pack_intel ./recovery.img zImage ramdisk.cpio.gz new-recovery.img 

From left to right, an already existing boot image (to copy bootstub from, it could be built from source on the future), the kernel, the gzipped cpio ramdisk and the output filename

Code:

	$ ./unpack_intel

	Usage: ./unpack_intel original-imgage bzImage-out ramdisk-out.cpio.gz

	example: ./unpack_intel ./recovery.img zImage ramdisk.cpio.gz 


From left to right, the image you want to unpack, and the destination files for bzImage and ramdisk. You can then unpack the ramdisk with something like

Code:
```bash
$ mkdir ramdisk-unpack

$ cd ramdisk-unpack

$ zcat ../ramdisk.cpio.gz|cpio -i


And then repack it with something like
Code:

	cd ramdisk-unpack 

	$ find . | cpio -o -H newc | gzip > ../newramdisk.cpio.gz

