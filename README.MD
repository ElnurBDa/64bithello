```asm
; Hello World Program in ASM 64-bit
; Author: ElnurBDa
;
; To run it:
; 1. Compile
;    nasm -f elf64 hello.asm -o hello.o
; 2. Link
;    ld hello.o -o hello
; 3. Run
;    ./hello

section .data
    hello db 'Hello, Elnur my Lord!', 0xA

section .text
    global _start

_start:
    ; Write to stdout
    mov rax, 0x04       ; syscall number for write
    mov rbx, 0x01       ; file descriptor for stdout
    mov rcx, hello      ; pointer to the string
    mov rdx, 30         ; a little more than length of the string (30 bytes)
    int 0x80            ; call the kernel

    ; Exit
    mov rax, 0x01       ; syscall number for exit
    xor rbx, rbx        ; exit code 0
    int 0x80            ; call the kernel
```
