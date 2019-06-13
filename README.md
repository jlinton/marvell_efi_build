# marvell_efi_build
scripts to clone and build the marvell uefi firmware

There is also a binary artifact built with the linaro
gcc 6.2 cross compiler and a few bugs tweaked/fixed.

That can be booted from a SD card by setting the mcbin jumpers
for SD boot:
 http://wiki.macchiatobin.net/tiki-index.php?page=MACCHIATObin+Interface+list#Boot_Selection

Then assure a partition table like the following exists on the SD card:

 Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1        4096    69631    65536   32M 83 Linux
/dev/sdd2       69632 15523839 15454208  7.4G 83 Linux

(the size and offsets of the first partition are important)

Then copy the image to the first partition like:

dd if=trusted-firmware-a/build/a80x0_mcbin/debug/flash-image.bin of=/dev/sdb1 conv=fdatasync

Where /dev/sdb1 in the example is the sd partition 1.

