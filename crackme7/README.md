crackme7
---

Change the status of the program from `Unregistered` to `Registered`

![image](https://user-images.githubusercontent.com/7328587/119833760-f59de300-bf31-11eb-94a0-88706e14ba78.png)

### The crack
<hr>

Trace the address where the string "Registered" is, and modify the value moved into `eax` from 5 to 4

`mov eax, 5`

`mov eax, 4`

![image](https://user-images.githubusercontent.com/7328587/119836253-2bdc6200-bf34-11eb-91e9-f9bfc43dbe28.png)

![image](https://user-images.githubusercontent.com/7328587/119836344-3f87c880-bf34-11eb-98d8-75a61334d826.png)

This changes the logic flow, and `Registered` is displayed

![image](https://user-images.githubusercontent.com/7328587/119836546-65ad6880-bf34-11eb-8d53-163d88740c74.png)

