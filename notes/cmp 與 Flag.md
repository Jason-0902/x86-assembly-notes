# cmp 與 Flag

## cmp 本質

```
cmp a, b
```

等於：

```
a - b
```

但：

- 不儲存結果
- 只更新 Flag

## 最重要 Flag

| Flag | 意義 |
| --- | --- |
| ZF | Zero Flag |
| SF | Sign Flag |
| OF | Overflow |
| CF | Carry |