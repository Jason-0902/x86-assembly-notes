# Stack Frame（rbp / rsp / 區域變數）

# Stack 是什麼？

Stack 是:

- 後進先出（LIFO）
- 從高位址往低位址長
- 由 `rsp` 指向頂端

# 兩個超重要 register

| Register | 作用 |
| --- | --- |
| rsp | stack pointer（目前 stack 頂） |
| rbp | base pointer（這個函式的基準點） |

# 一個典型函式長這樣

```nasm
push rbp
mov rbp, rsp
sub rsp, 0x20
```

## 觀念題

```nasm
push rbp
```

實際發生什麼？

A) rbp 清零
B) rbp 的值被放到 stack → correct
C) stack 被清空
D) rsp 變大

# `push rbp` 發生了什麼？

等價於這兩步:

```nasm
sub rsp, 8        ; 因為是 64-bit
mov [rsp], rbp    ; 把 rbp 存到 stack
```

也就是:

1.  `rsp` 先往下移（stack 往低位址長）
2. 把 **`rbp` 的值寫到新的 `[rsp]` 位置**

## 為什麼要這樣做？

因為我們要：

保存「上一個函式的 rbp」

等一下函式結束時要還原

---

```nasm
mov rbp, rsp
```

這代表：

> 讓 rbp 成為「這個函式的基準點」
> 

之後所有區域變數都會用:

```nasm
[rbp - offset]
```

來存取

# sub rsp, 0x20

代表:

```
rsp = rsp - 0x20
```

因為：

- stack 往低位址長
- 減少 rsp → 等於「往下挖空間」

這其實是在:

> 為這個函式預留 0x20 (32 bytes) 的 local 變數空間
> 

# 典型函式開頭（Prologue）

```nasm
push rbp
mov  rbp, rsp
sub  rsp, 0x20
```

意思是:

1. 保存舊 rbp
2. 建立新的 base pointer
3. 分配 local 變數空間

# 函式結尾（Epilogue）

通常會看到:

```
mov rsp, rbp
pop rbp
ret
```

或簡寫成:

```
leave
ret
```

## 關鍵理解題

假設:

```
push rbp
mov  rbp, rsp
sub  rsp, 0x20
```

此時如果一個 local 變數在:

```
[rbp - 0x8]
```

請問:

它在 stack frame 的哪個位置？

A) return address

B) 上一個 rbp

C) local 變數 → answer

D) 參數

# 為什麼 `[rbp - 0x8]` 是 local 變數？

當函式進來時：

```nasm
push rbp
mov  rbp, rsp
sub  rsp, 0x20
```

stack 會長成這樣（高位址在上）：

```
|                |
|  參數（若有）   |
|----------------|
| return address |
|----------------|
| old rbp        |  ← rbp 指向這裡
|----------------|
| local var 1    |  ← [rbp - 0x8]
| local var 2    |  ← [rbp - 0x10]
| ...            |
|----------------|
|                |  ← rsp 在這裡（已減 0x20）
```

# 記憶公式

| 位置 | 用途 |
| --- | --- |
| `[rbp + 0x8]` | return address |
| `[rbp]` | old rbp |
| `[rbp - x]` | local 變數 |