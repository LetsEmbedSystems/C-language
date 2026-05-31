# C-language

# To generate assembly to binary
riscv64-unknown-elf-gcc -O0 -ggdb -nostdlib -march=rv32i -mabi=ilp32 -Wl,-Tm.ld m.s -o main.elf 

# To emulate on QEMU machine
qemu-system-riscv32 -S -M virt -nographic -bios none -kernel main.elf -gdb tcp::1234 


# To execute gdb
gdb-multiarch main.elf -ex "target remote localhost:1234" -ex "break _start" -ex "continue" -q

# To generate binary file
riscv64-unknown-elf-objcopy -O binary main.elf main.bin

# To read the binary instaructions
xxd -e -c 4 -g 4 main.bin

# RISC-V instruction Decoder
https://luplab.gitlab.io/rvcodecjs/

# To Install GDB-dashboard
# command 1: Just place .gdbinit in your home directory 
wget -P ~ https://github.com/cyrus-and/gdb-dashboard/raw/master/.gdbinit
    
# command 2: Optionally install Pygments to enable syntax highlighting
pip install pygments
