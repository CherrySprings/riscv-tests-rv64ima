# Linux Kernel for CherrySprings Project

1. Generate kernel binary

    ```bash
    $ riscv64-unknown-linux-gnu-objcopy -O binary linux.elf linux.bin
    ```

1. Dump disassembly

    ```bash
    $ riscv64-unknown-linux-gnu-objdump -d linux.elf > linux.dump
    ```

## Note

As OpenSBI loads the kernel to start address `0x80200000`, for all the address in `System.map`, the actual address in `linux.dump` needs to be substracted by an offset `0x200000`. For example, in `linux.dump` the address `0x80c06050` corresponds to `0x80a06050` in `System.map`, which is in the range of the function `set_satp_mode`.
