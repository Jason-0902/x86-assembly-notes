# while / for 的底層結構

## while 的 Assembly 模式

C:

```c
while (condition) {
    body
}
```

Assembly 本質:

```c
loop_start:
    cmp ...
    jXX end_label     ; 條件不成立就跳出
    body
    jmp loop_start
end_label:
```

重點:

> Assembly 寫的是「跳出條件」，不是繼續條件。
> 

## 跳出條件推導規則

| C 條件 | 跳出條件 |
| --- | --- |
| while (i < n) | i >= n |
| while (i <= n) | i > n |
| while (i > n) | i <= n |
| while (i >= n) | i < n |

## for 迴圈本質

```
for (init;condition;update)
```

其實就是:

```
init;
while (condition) {
body;
update;
}
```

Assembly 形式:

```
init

loop:
    cmp ...
    jXX end
    body
    update
    jmp loop
end:
```

## cmp + jg / jge 深度理解

signed 比較

| 指令 | 意義 |
| --- | --- |
| jg | > |
| jge | >= |
| jl | < |
| jle | <= |

例如:

```nasm
cmp rax, rdi
jge end
```

代表:

```c
if (rax >= rdi) break;
```