# x86-assembly-notes

這個 repository 紀錄我學習 x86-64 Assembly、底層原理與 Reverse Engineering 思維的筆記整理。

目標不是只會寫 C / Python，
而是真正理解:

- CPU 在做什麼
- 記憶體如何運作
- 函式如何被呼叫
- Compiler 如何把高階語言轉成機器碼
- 如何從 Assembly 還原 C 邏輯

---

## 目前筆記內容

### 基礎觀念

- CPU 與 Machine Code
- Register 基礎
- Zero Extension
- 基本指令（mov / add / imul / shift / lea）

---

### 記憶體與 Stack

- Memory 與 Pointer
- Stack Frame（rbp / rsp / 區域變數）
- Calling Convention（System V ABI）

---

### Flag 與條件判斷

- cmp 與 Flag
- test 指令
- 與跳躍結合

---

### 迴圈與控制流程

- while / for 的底層結構
- cmp + jg / jge 深度理解
- 跳出條件推導規則

---

### Reverse 思維

- reverse 思維進化
- 邏輯還原技巧
- 如何從 Assembly 還原 C

---

## 學習目標

我希望透過這些筆記建立:

- 底層系統理解能力
- Reverse Engineering 思維
- Binary Exploitation 基礎
- Fuzzing 理解
- 對 Compiler 行為的直覺

---

## 使用工具

- GDB
- pwndbg
- objdump
- readelf
- checksec
- pwntools
- Ghidra

---

## 為什麼要學 Assembly？

高階語言會幫你隱藏細節，
但漏洞不會。

真正的漏洞存在於:

- Stack
- Heap
- Register
- Flag
- Calling Convention
- Memory Layout

如果想理解：

- Buffer Overflow
- ROP
- Format String
- Use After Free

你必須懂 Assembly。

---

## 長期規劃

接下來會加入:

- ELF 結構解析
- Function Prologue / Epilogue 深度拆解
- Compiler 優化模式
- 常見 Exploit 模型
- C 與 Assembly 對照分析

---

## 更新狀態

持續更新中。

## License

This project is licensed under the MIT License.
