# reverse 思維進化

當你看到:

```nasm
mov eax, 0
mov ecx, 0

cmp ecx, edi
jge end

test ecx, 1
jne skip

add eax, ecx
```

你應該能立刻想到:

```c
while (i<n) {
	if (i%2==0)
	sum+=i;
}
```