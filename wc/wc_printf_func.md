### 標頭檔：stdio.h

### 函式：int printf (const char *template, …)

### glibc 函式說明：
The printf function prints the optional arguments under the control of the template string template to the stream stdout. It returns the number of characters printed, or a negative value if there was an output error. 

### 輸入：
The printf function prints the optional arguments under the control of the template string template to the stream stdout.

1. optional arguments (例如：變數 i, j 等)
2. template string template (例如：%s, %c, %d \n 等)

其中 optional arguments 的 template 是受 template 控制。 

### 輸出：
It returns the number of characters printed, or a negative value if there was an output error.  

1. 當函式正常執行時，輸出字元數。
2. 當函式出現錯誤時，輸出負數值。

### 使用範例：
```c
#include <stdio.h>

/* print wc results */

int main(void)
{
    int nl, nc, nw;
    nl = nc = nw = 2;

    printf("number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw);
    return 0;
}
```

### 參考文獻
[1] Gnu.org, 'The GNU C Library: Formatted Output Functions', 2015. [Online]. Available: http://www.gnu.org/software/libc/manual/html_node/Formatted-Output-Functions.html. [Accessed: 18- Nov- 2015].