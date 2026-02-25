# CPU 與 Machine Code

## CPU 最終只看得懂：

```
010101010101...
```

也就是 **Machine Code**

Assembly 只是機器碼的可讀版本

例如：

```
48 01 f8
```

對應：

```
add rax, rdi
```

## CPU 執行流程

CPU 只做三件事:

```
1. Fetch
2. Decode
3. Execute
```

然後無限重複