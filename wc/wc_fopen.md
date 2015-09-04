## 加入 fopen 函式，讀檔

### 程式內容
```c
#include <stdio.h>

#define IN 1    /* inside a word */
#define OUT 0   /* outside a word */

/* count lines, words, and characters in input */
int main(void){
    int c, nl, nw, nc, state;

    state = OUT;
    nl = nw = nc = 0;

    /* file open as stream */
    FILE *fp = fopen("test", "r");

    /* start counting */
    while ((c = getc (fp)) != EOF){
        /* anything that's not EOF, counts. */
        ++nc;

        /* count newline */
        if (c == '\n')
            ++nl;

        /* count words*/
        if (c == ' ' || c == '\n' || c == '\t')
            state = OUT;
        else if (state == OUT){
            state = IN;
            ++nw;
        }
    }

    /* file stream closed*/
    fclose (fp);

    /* print the results of calculation */
    printf("number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw);

    return 0;
}
```

### 測試檔案內容
```
1
2
3
5

this is a test
```

### 編譯程式
```bash
$ gcc wc_fopen.c -o wc_fopen.o
```

### 執行結果
```
$ ./wc_fopen.o
number of line: 6
number of char: 24
number of word: 8
```


