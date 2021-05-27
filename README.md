# crackme

Solutions and write ups to crack files from https://crackinglessons.com/

Assembly code reference: https://css.csail.mit.edu/6.858/2014/readings/i386/c17.htm

Generic info
---

### Function return value storage
<hr>

`eax` stores the return value of a function call

### Bytes of registers
<hr>

`al` uses the first byte of a register

`ah` uses the 2nd byte of the register

`ax` uses the first 2 bytes of a register

`eax` uses all 4 bytes of a register

| 0000 0001 0010 0011 0100 0101 0110 0111 | ------> EAX

|                     0100 0101 0110 0111 | ------> AX

|                               0110 0111 | ------> AL

|                     0100 0101           | ------> AH

`byte` = 1 byte

`word` = 2 bytes

`dword` = 4 bytes

### NOP and jumps
<hr>

Typically we can remove or go around code logics by `nop-ping` the code, or changing the logic of the jumps `jmp`, `je`, `jg`, `jl`

When we see a conditional jump, most likely there is a `test` or `cmp` above that sets the Zero Flag to a value which tells it to jump or not


