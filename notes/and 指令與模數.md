# and 指令與模數

如果看到:

```nasm
and edx, 3
```

等價於：

```c
i & 3
```

因為:

```
3 = 0b11
```

這實際上在做:

```
i % 4
```

所以:

```nasm
and edx, 3
jne skip
```

代表:

```c
if (i % 4 != 0) skip;
```