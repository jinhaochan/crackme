Mexico
---

### Objective

Modify the binary so that it prints the flag instead of `"try harder"`

### Original code

![image](https://user-images.githubusercontent.com/7328587/119462656-88dcea00-bd73-11eb-813e-0cf03684fd92.png)

Here we see the code printing out the "try harder" in line `00401653`

### Code we want to call

![image](https://user-images.githubusercontent.com/7328587/119463233-2506f100-bd74-11eb-960e-8e1b76983dfa.png)

This is the code block we want to call at address `00401500`, which prints out the flag.

We can uncover references to this address, and we see that the caller for this function lies in line `0040164C`, which is in the original code flow

### Patch (v1)

In the original code on line `00401642`, we see a comparison being done with `C1`. In the next line, if the value is smaller than `C1`, then we jump to line `00401653`, which prints the `"try harder"` string

If we want to call the function to print the flag, we need to make value to be smaller than `C1`.

The first version of the patch can be done by changing `C1` to something small, like 0, so that the value being used to comapre will be greater.

![image](https://user-images.githubusercontent.com/7328587/119464896-c6db0d80-bd75-11eb-9c94-ae69468807f1.png)

### Patch (v2)

The second way to trigger this is to change the comparison logic to be `jg` instead of `jle`

![image](https://user-images.githubusercontent.com/7328587/119465080-ef630780-bd75-11eb-8456-5234355e0758.png)
