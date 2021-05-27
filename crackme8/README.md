crackme8
---

In this program we learn how to set hardware breakpoints, and make modifications in the memory space

To set the string to be "REGISTERED", we need this jump to not be taken 

![image](https://user-images.githubusercontent.com/7328587/119840736-d30ec880-bf37-11eb-8e8c-f28fb0551249.png)

We can do that by changing the `je` on line `0040386D` to `nop`, or we can modify the contents in memory `7260D0`.

In line `0040385A`, a comparison is done with the value in memory `7260D0` with the value 0. If they are equal, the zero flag is set to 1, and the jump is taken.

All we need to do is to change the value in memory `7260D0` from 0 to any other number, so that the comparison will not be equal, and the jump is not taken

![image](https://user-images.githubusercontent.com/7328587/119841154-284ada00-bf38-11eb-9bec-0d0f7b39f5d4.png)

![image](https://user-images.githubusercontent.com/7328587/119841205-33056f00-bf38-11eb-92c3-ee753a6459b0.png)

After changing that address, we see the string "REGISTERED" being shown

![image](https://user-images.githubusercontent.com/7328587/119841283-41ec2180-bf38-11eb-8640-bd16dd725e15.png)
