crackme3
---

The goal is to remove the nags, and to register the software

### Removing nags
<hr>

When opening this program closing this program, it shows two "nagging" screens.

Opening nag

![image](https://user-images.githubusercontent.com/7328587/119613321-77f1ae80-be2f-11eb-9b49-c91a2a93970c.png)

Closing nag

![image](https://user-images.githubusercontent.com/7328587/119613355-8344da00-be2f-11eb-845e-79e1790a9803.png)

We trace the code to the line where the nag appears, which is on line `00401039`, where is shows the display box

![image](https://user-images.githubusercontent.com/7328587/119613602-da4aaf00-be2f-11eb-9c7c-d9302597f8d8.png)

We can see that there is a jump statement on line `00401029`, which skips that code block if the `cmp` is not equal to 0.

By simply changing `jne` to `je`, we can bypass the first nag

![image](https://user-images.githubusercontent.com/7328587/119613793-17af3c80-be30-11eb-8fa3-cf102eb6098e.png)

To bypass the second nag, it's a little bit trickier. Here, there are no comparators to abuse, but instead we have to insert our own jump function

When we click the close button on the dialog, it brings us from line `004010C3` to `004010FF`

![image](https://user-images.githubusercontent.com/7328587/119613971-504f1600-be30-11eb-9a8c-6965668b4373.png)

Lines `004010FF` to `00401107` close the current dialog box

Lines `0040110D` to `0040111B` will create the closing nag

Lines `00401121` to `00401123` sends a signal to close to program

To bypass the closing nag, we modify line `0040110D` to `jmp 00401121`. What this does it that it skips the closing nag code entirely, and jumps unconditionally to send a close signal.

![image](https://user-images.githubusercontent.com/7328587/119614390-cfdce500-be30-11eb-81fb-014c8418ac30.png)

Another way to do this is to `nop` the entire code block that generates the closing nag

![image](https://user-images.githubusercontent.com/7328587/119615646-344c7400-be32-11eb-9e54-d90597e83ca6.png)

### Registering software
<hr>

Registering the software, or making it print the "REGISTERED" string, is done by toggling the jump logic on line `00401D8` from `je` to `jne`

![image](https://user-images.githubusercontent.com/7328587/119651481-a5525280-be57-11eb-9b45-ff688960a5c3.png)

![image](https://user-images.githubusercontent.com/7328587/119651544-b602c880-be57-11eb-89ae-7279ac65250f.png)
