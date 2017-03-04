# my-kernel

### this is a stuend's fool action


### kernel.asm
This file is to guide computer to find kernel's enter

### kernel.c
This file is the kernel itself.

### Compiling
> 1. nasm -f elf32 kernel.asm -o kasm.o
> 2. gcc -m32 -c kernel.c -o kc.o
> 3. ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o

### Set up
1. Put the exec file kernel to dictory /boot on the superadmin
2. Then rename it by format "kernel-<version>"
3. Then set up grub:

To GRUB, modifing /boot/grub/grub.cfg, add information
> title myKernel
>	root (hd0,0)
>	kernel /boot/kernel-<version> ro

To GRUB2, modifing /boot/grub/grub2.cfg ,add information
> menuentry 'kernel <version>' {
>		set root='hd0, msdos1'
>		mutiboot /boot/kernel-<version> ro
>}
