# Memory 與 Pointer

## 差別：

```
rdi   → 是地址
[rdi] → 是地址裡的值
```

## 讀記憶體

```
mov rax, [rdi]
```

代表:

```
rax = *rdi
```

## 寫記憶體

```
mov dword [rdi], 10
```

代表:

```
*(int*)rdi = 10
```

# 資料大小（Data Size）

| 類型 | Bytes | Assembly |
| --- | --- | --- |
| char | 1 | byte |
| short | 2 | word |
| int | 4 | dword |
| long / pointer | 8 | qword |

**當目標是記憶體時必須指定大小**

# Register 家族

| 64-bit | 32-bit | 16-bit | 8-bit |
| --- | --- | --- | --- |
| rax | eax | ax | al |