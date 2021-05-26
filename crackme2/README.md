crackme2
---

This software checks if the file is registered or not

### Find break point where dialog is presented

We need to find this break point because the logic for checking if the software is registered would be before this

We can do this by stepping through the program until the dialog box appears

![image](https://user-images.githubusercontent.com/7328587/119606846-d6b22a80-be25-11eb-9893-f66588ae41de.png)

We see that the dialog box appears after we executed the call function on line `0040132F`

We then set a break point to it, and jump into the function

### Function to check registered

In this function, we see that it tries to read a file called `keyfile.txt`

![image](https://user-images.githubusercontent.com/7328587/119606984-1e38b680-be26-11eb-972c-0ca8b435f96d.png)

We can confirm this by reading the function definition of `CreateFileA`: https://docs.microsoft.com/en-us/windows/win32/api/fileapi/nf-fileapi-createfilea

We see that it takes in 7 parameters, which corresponds to the 7 parameters that are being pushed to the stack before calling the function

In this case, the filename, which  is the first parameter of the function (and the last variable to be pushed on the stack) is beind referenced to

In line `00401049`, we see that it moves the value in `eax` to `esi`. `eax` contains the return value of the previous function that was called, in this case it was `CreateFileA`

In line `0040104B`, it is checking if the value in `esi` (or the value in `eax` which was the return value of `CreateFileA`) is equals to -1. Reading the function definition, the function will return -1 if there is an error opening the file. We can thus conclude that this program tries to open the file `keyfile.txt` and read it's contents

![image](https://user-images.githubusercontent.com/7328587/119607447-eda54c80-be26-11eb-8548-416738e9986a.png)

We can confirm that behavior when reading line `0040105F`, which calls `ReadFileEx`

Therefore, all we have to do is to create a file called `keyfile.txt`, and put in any name, and the function will show the registration

![image](https://user-images.githubusercontent.com/7328587/119607574-2513f900-be27-11eb-801e-111c868e4a82.png)


![image](https://user-images.githubusercontent.com/7328587/119607552-1deceb00-be27-11eb-9002-4342b561ed70.png)
