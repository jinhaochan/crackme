The Dutch Cracker
---

In this program, we need to remove the nag, as well as make the program say `Clean crack! Good Job!` when clicking on the button `Re-Check`

The Nag 

![image](https://user-images.githubusercontent.com/7328587/119676079-287fa280-be70-11eb-82da-0bb2cf637313.png)

The program string and button

![image](https://user-images.githubusercontent.com/7328587/119676167-3c2b0900-be70-11eb-82a3-d52cdb039cdc.png)

### Removing the nag
<hr>

To remove the nag, we need to see where is it getting called first. By searching for strings and setting a breakpoint, we can see that line `0040108B` calls the pushes of arguments, and displays the message

![image](https://user-images.githubusercontent.com/7328587/119676728-a93e9e80-be70-11eb-9a59-73493899811e.png)

to remove this, we replace everything with a nop from `004010A7` to `004010B6`

![image](https://user-images.githubusercontent.com/7328587/119676982-e440d200-be70-11eb-838f-ce9f77480107.png)

Now when we start the program, the nag will not appear due to the bunch of nops

### Changing the string on clicking `Re-Check`
<hr>

When we click `Re-Check`, we find the strings that is updated on the dialog box, which is `Nag not removed!`

We find where that string is called, and set a breakpoint on it

![image](https://user-images.githubusercontent.com/7328587/119677457-52859480-be71-11eb-860a-7f6862bbf2f9.png)

To bypass that call, we replace the line `004010F8` with nop

![image](https://user-images.githubusercontent.com/7328587/119677616-7517ad80-be71-11eb-902e-5b981b10b39b.png)

But we see now that it triggers the second flow, which prints `Dirty Crack! Nag removed not registered!`. This happens because the jump at `00401104` is not executed. The solution is to change it to an unconditional jump `jmp`

![image](https://user-images.githubusercontent.com/7328587/119677936-b6a85880-be71-11eb-9354-c2f4a274d607.png)

With that, we bypass both the nag and the dirty crack check


