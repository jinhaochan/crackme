Crackme1
---

We have a binary that shows us a GUI, which we must key in the serial number. We have to do two things
1. Figure out the serial number
2. Always make the checkbox display congrats when the button is clicked

### Finding out the serial number

This is the easy part, where you simply search for string references, and we find it in the definition

![image](https://user-images.githubusercontent.com/7328587/119592857-d73dc780-be0b-11eb-9093-d564d9b48c26.png)

`cr4ckingL3ssons`

### Always make the checkbox display congrats

We see that a conditional jump is being made when comparing the input string to `cr4ckingL3ssons`

The condition `test eax, eax` on line `00401137` checks if `eax` contains 0.

If `eax` is 0, the congrats message is displayed, if not it makes a jump to display the wrong serial key message

![image](https://user-images.githubusercontent.com/7328587/119593110-37cd0480-be0c-11eb-8a02-07f93559f5e6.png)

To do this, we simply make the contents of `eax` to be 0.

One way to do this is on line `00401132`, `or eax, 1`. If we change this to `and eax, 0`, `eax` will always be zero, and the condition will always pass

![image](https://user-images.githubusercontent.com/7328587/119593439-8d091600-be0c-11eb-93ad-1cc0578520da.png)

![image](https://user-images.githubusercontent.com/7328587/119593475-9b573200-be0c-11eb-9c3b-95e435e8e4a2.png)


### XOR to make EAX 0

Another way to make `eax` zero is by xoring it with itself. 

We replace the jump instruction with `xor eax, eax`

![image](https://user-images.githubusercontent.com/7328587/119593696-fbe66f00-be0c-11eb-8755-6f2716c4f9b0.png)
