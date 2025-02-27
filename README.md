# myRISCcodes

This repository contains some simple RISC-V assembly and C programs demonstrating multithreading, system calls, and arithmetic operations. I'll provide how did I do the compilation and the execution.

# Required Tools & Installation
To compile and run the RISC-V programs, i used:

- RISC-V Cross-Compiler (riscv64-unknown-elf-gcc and riscv64-linux-gnu-gcc)
- QEMU for RISC-V (to run the compiled programs)

```bash
#mamed@mamed-MS-7C95:~$ riscv64-unknown-elf-gcc --version
riscv64-unknown-elf-gcc (13.2.0-11ubuntu1+12) 13.2.0
#mamed@mamed-MS-7C95:~$ riscv64-linux-gnu-gcc --version
riscv64-linux-gnu-gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
#mamed@mamed-MS-7C95:~$ qemu-riscv64 --version
qemu-riscv64 version 8.2.2 (Debian 1:8.2.2+ds-0ubuntu1.5)
```

# Example codes

```bash
cd addition
riscv64-linux-gnu-gcc -o addit addit.c
qemu-riscv64 -L /usr/riscv64-linux-gnu ./addit
```

```bash
cd additionassembly
riscv64-unknown-elf-as -o addp.o addp.s
riscv64-unknown-elf-ld -o addp addp.o
qemu-riscv64 ./addp
echo $?
```

```bash
cd thread_pool
riscv64-linux-gnu-gcc -o thread_pool thread_pool.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./thread_pool
```

```bash
cd thread_consommateur
riscv64-linux-gnu-gcc -o cond_example cond_example.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./cond_example
```

```bash
cd program
riscv64-unknown-elf-as -o program.o program.s
riscv64-unknown-elf-ld -o program program.o
qemu-riscv64 ./program
```

```bash
cd threads
riscv64-linux-gnu-gcc -o threads threads.c -lpthread
qemu-riscv64 -L /usr/riscv64-linux-gnu ./threads
```

