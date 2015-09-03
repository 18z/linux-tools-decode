## if - else 判斷式

### 使用目的
判別特定條件是否成立。若成立則執行特定內容。

### 使用方法

```c
if (condition)
    statement;
```

若符合 condition，則執行 statement。

```c
if (condition1)
    statement1;
else if (condition2)
    statement2;
else
    statement3;
```

若符合 condition1 則執行 statement1。若符合 condition2 則執行 statement2。
若 condition1 及 condition2 都不符合，則執行 statement3。

最後一個 else 及 statement3 有時可省略。

情況就會變成。
若符合 condition1 則執行 statement1。若符合 condition2 則執行 statement2。
若 condition1 及 condition2 都不符合，就繼續往下執行。什麼 statement 也沒有執行。

## 搭配 while 迴圈使用
```c
while ((c = getchar()) != EOF) {
    ++nc;
    if (c == '\n')
        ++nl;

    if (c == ' ' || c == '\n' || c == '\t')
        state = OUT;
    else if (state == OUT) {
        state = IN;
        ++nw;
    }
}
```
```
當讀取到的字元非 EOF 時，則 number of character 加一。
接著，檢查該字元是否為換行符號`\n`，若是則 number of line 加一。

再接著，檢查字元是否為空白、換行或tab其中之一。
若是，則將 state 狀態改成 OUT，亦即在字外。

while 迴圈，第一輪結束。
接著讀取下一個字元。

由於不是 EOF，所以 number of character 加一。
接著，檢查該字元是否為換行符號`\n`，檢查結果為否，則 number of line 不加一。
再接著，檢查字元是否為空白、換行或tab其中之一。
檢查結果為否。所以再試試看 condition2，也就是檢查是否在字外。
檢查結果為是，因此，將 state 狀態改成 IN，亦即在字內，並且 number of word 加一。
```
