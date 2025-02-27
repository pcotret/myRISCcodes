This repository contains some simple RISC-V assembly and C programs demonstrating multithreading, system calls, and arithmetic operations. I'll provide how did I do the compilation and the execution.
# myRISCcodes

#file addit.c in addition folder
riscv64-linux-gnu-gcc -o addit addit.c
qemu-riscv64 -L /usr/riscv64-linux-gnu ./addit

#addp.s in additionassembly folder
riscv64-unknown-elf-as -o addp.o addp.s
riscv64-unknown-elf-ld -o addp addp.o
qemu-riscv64 ./addp
echo $?

# file thread_pool.c in threadpool folder 
riscv64-linux-gnu-gcc -o thread_pool thread_pool.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./thread_pool

#file cond_example in threadsconsommateur
riscv64-linux-gnu-gcc -o cond_example cond_example.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./cond_example

#file program.s
riscv64-unknown-elf-as -o program.o program.s
riscv64-unknown-elf-ld -o program program.o
qemu-riscv64 ./program

#file threads.c 
riscv64-linux-gnu-gcc -o threads threads.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./threads


#Required Tools & Installation
To compile and run the RISC-V programs, i used:

RISC-V Cross-Compiler (riscv64-unknown-elf-gcc and riscv64-linux-gnu-gcc)
QEMU for RISC-V (to run the compiled programs)

#mamed@mamed-MS-7C95:~$ riscv64-unknown-elf-gcc --version
riscv64-unknown-elf-gcc (13.2.0-11ubuntu1+12) 13.2.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

#mamed@mamed-MS-7C95:~$ riscv64-linux-gnu-gcc --version
riscv64-linux-gnu-gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

#mamed@mamed-MS-7C95:~$ qemu-riscv64 --version
qemu-riscv64 version 8.2.2 (Debian 1:8.2.2+ds-0ubuntu1.5)
Copyright (c) 2003-2023 Fabrice Bellard and the QEMU Project developers

#mamed@mamed-MS-7C95:~$ qemu-system-riscv64 -machine help
Supported machines are:
microchip-icicle-kit Microchip PolarFire SoC Icicle Kit
none                 empty machine
shakti_c             RISC-V Board compatible with Shakti SDK
sifive_e             RISC-V Board compatible with SiFive E SDK
sifive_u             RISC-V Board compatible with SiFive U SDK
spike                RISC-V Spike board (default)
virt                 RISC-V VirtIO board

