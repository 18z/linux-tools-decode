## 列印出行數、字元數與字數

wc 是用來計算檔案行數、字元數與字數的工具。在此階段我們不會講到如何做行數、字元數及字數的計算方法。我們**只會**講到如何用 printf 來模擬 wc 執行後顯示在 terminal 上的結果。

### 程式內容
```c
#include <stdio.h>

/* print wc results */

int main()
{
    int nl, nc, nw;
    nl = nc = nw = 2;

    printf("number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw);
}
```

### 編譯程式
```
$ gcc wc_printf.c -o wc_printf
```

### 執行程式
```
$ ./wc_printf
```

### 執行結果
```
$ ./wc_printf
number of line: 2
number of char: 2
number of word: 2
```
