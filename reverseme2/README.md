reverseme2
---

In this program, we need to find out what the correct serial number is to activate the program

When we look at the strings, its trying to open a file called `Keyfile.dat`

![image](https://user-images.githubusercontent.com/7328587/119849184-0012a980-bf3f-11eb-8cfb-df790211e380.png)

The code then compares the length of the string with a value `0x10`, which is 16. This means the serial must be 16 characters exactly

![image](https://user-images.githubusercontent.com/7328587/119849657-64356d80-bf3f-11eb-8081-d306ca6fbb1d.png)

Next is a loop, which keeps going until it see a `0`, which indicates end of file.

We see that it also counts the number of times the letter `G` appears, and if it does, it increments `esi`, if not it skips over it

![image](https://user-images.githubusercontent.com/7328587/119850059-c55d4100-bf3f-11eb-88e2-ceed5ccd9c31.png)

We also see that at the end of the loop, it compares `esi` with `0x08`. If the value in `esi` is less than 8, it jumps to print `Keyfile is not valid. Sorry`

This means that the serial number must be 16 characters long, and must contain at least 8 `G` characters

