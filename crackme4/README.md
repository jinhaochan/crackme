crackme4
---

When we run this program, it shows us that there is 11 days of the program left. Our aim is to extend that duration to a larger duration

![image](https://user-images.githubusercontent.com/7328587/119656463-4ee81280-be5d-11eb-9658-c98fe0ad474f.png)

When we analyze the code, we see that the value for the number of days left are stored in `ecx`, and line `0040103D` moves a values to `ecx`

![image](https://user-images.githubusercontent.com/7328587/119656633-7d65ed80-be5d-11eb-85e1-b2d20c976120.png)

The crack is simply changing the value placed into `ecx` to a very large number, and that results in a longer number of days of registration

![image](https://user-images.githubusercontent.com/7328587/119656851-c322b600-be5d-11eb-99a5-342cdfb468e5.png)

![image](https://user-images.githubusercontent.com/7328587/119656883-cf0e7800-be5d-11eb-8240-45e249d1f07b.png)
