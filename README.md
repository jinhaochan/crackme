# crackme

Solutions and write ups to crack files from https://crackinglessons.com/

Assembly code reference: https://css.csail.mit.edu/6.858/2014/readings/i386/c17.htm

Generic info
---

`eax` stores the return value of a function call

`al` uses the first byte of a register

`ah` uses the 2nd byte of the register

`ax` uses the first 2 bytes of a register

`eax` uses all 4 bytes of a register

| 0000 0001 0010 0011 0100 0101 0110 0111 | ------> EAX

|                     0100 0101 0110 0111 | ------> AX

|                               0110 0111 | ------> AL

|                     0100 0101           | ------> AH
