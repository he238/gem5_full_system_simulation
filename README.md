# gem5_full_system_simulation

This is gem5 full system simulation disk image and linux kernel. 
You can use it for free (But please give me a star on git if works). 
Tested with gem5 v22. Letme know if there is any issue with it.

https://drive.google.com/file/d/1m0Z-7U8-OyQcqqzYFWZ6hgWVUsZrHaEK/view?usp=sharing

util/gem5img.py mount ubuntu-14.04.img mnt
sudo /bin/mount -o bind /sys mnt/sys
sudo /bin/mount -o bind /dev mnt/dev
sudo /bin/mount -o bind /proc mnt/proc

sudo /usr/sbin/chroot mnt /bin/bash

sudo /bin/umount mnt/sys
sudo /bin/umount mnt/proc
sudo /bin/umount mnt/dev
sudo ../util/gem5img.py umount mnt

sudo build/X86/gem5.opt configs/example/fs.py --cpu-type=X86KvmCPU --disk-image disks/x86-ubuntu-18.04-img  --kernel ./binaries/vmlinux-4.4.186 --mem-size=32GB --checkpoint-at-end
build/X86/gem5.opt configs/example/fs.py --cpu-type=X86O3CPU --caches --disk-image disks/x86-ubuntu-18.04-img --kernel ./binaries/vmlinux-4.4.186 --mem-size=32GB 

scons -j32 ./build/X86/gem5.opt

sudo qemu-system-x86_64 -hda x86-ubuntu-18.04-img -m 1024 -enable-kvm 
gem5
12345
 
 
