# My First Service 1 (pwn 100)
It's a basic format string attack. In the server, the code is something like this.  
``` c
char buf[100];
fgets(buf, 100, stdin);
printf(buf);
```
If we input something like ```%x %x %x %x %x %x %x %x```, we can see the stack of the memory. With many "%x" printing the stack content, we can find out some bytes which look like ascii. Decode it to ascii string and get the flag.

