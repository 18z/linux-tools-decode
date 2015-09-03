## 在終端機上接收使用者輸入之字串，並列印出行數、字元數與字數

在第一個程式中，我們學會了如何用 `printf` 來列印出行數、字元數與字數。
在接下來的文章裡，我們將以第一個程式為基礎，再撰寫第二個程式。

```
第二個程式功能有：

1. 讀取使用者在終端機上輸入之字串。
2. 針對使用者輸入之內容計算，並將行數、字元數與字數之統計數據列印出來。
```

### 程式內容
```c
#include <stdio.h>

#define IN 1 /* inside a word */
#define OUT 0 /* outside a word */

/* count lines, words, and characters in input */
int main(void){
    int c, nl, nw, nc, state;
    state = OUT;
    nl = nw = nc = 0;

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

    printf("number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw);
    return 0;
}
```

### 編譯程式
```
$ gcc wc_getchar.c -o getchar
```

### 執行結果
```
$ ./getchar
test
test1
number of line: 2
number of char: 11
number of word: 2

# 註：test 輸入完後按enter，test1 輸入完後按 enter，最後按 ctrl + d。便可看到統計結果。
```
