# Zero Extension

```python
mov eax, 1
```

會：

```
自動把 rax 高 32-bit 清零
```

等於:

```
rax = 0000000000000001
```

但:

```
mov ax, 1
```

不會清高位