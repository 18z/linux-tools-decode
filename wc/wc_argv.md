## 使用 argc，argv 從 cmd 傳檔案給程式

### 程式內容
```c
#include <stdio.h>
#include <stdarg.h>

#define IN 1    /* inside a word */
#define OUT 0   /* outside a word */

/* count lines, words, and characters in input */
/* It is fundamental to c that char**x and char*x[]
   are two ways of expressing the same thing.*/

int main(int argc, char **argv)
{
    int c, nl, nw, nc, state;

    state = OUT;
    nl = nw = nc = 0;

    FILE *fp = fopen(argv[1], "r");

    if (!fp)
        printf("cannot open file %s", argv[0]);


    while ((c = getc (fp)) != EOF) {
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

    fclose (fp);
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
$ gcc wc_argv.c -o wc_argv.o
```

### 執行結果
```bash
$ ./wc_fargv.o test
number of line: 6
number of char: 24
number of word: 8
```
