Чтобы запустить ядро наберите в консоли:qemu-system-i386 -kernel kernel

Команды сборки
nasm -f elf32 kernel.asm -o kasm.o
gcc -m32 -c kernel.c -o kc.o
ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o
Если вы получаете следующее сообщение об ошибке:

kc.o: In function `idt_init':
kernel.c:(.text+0x129): undefined reference to `__stack_chk_fail'
компилируйте с помощью -fno-stack-protector опции:

gcc -fno-stack-protector -m32 -c kernel.c -o kc.o

Тест на эмуляторе
qemu-system-i386 -kernel kernel

