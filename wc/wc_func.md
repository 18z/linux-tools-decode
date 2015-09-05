### 函式

## 程式內容
```c
#include <stdio.h>

#define IN 1    /* inside a word */
#define OUT 0   /* outside a word */

/* count lines, words, and characters in input */
/* It is fundamental to c that char**x and char*x[]
   are two ways of expressing the same thing.*/

void counter(char *file)
{
    int c, nl, nw, nc, state;
    state = OUT;
    nl = nw = nc = 0;

    FILE *fp = fopen(file, "r");

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

    printf("number of line: %d\n"
           "number of char: %d\n"
           "number of word: %d\n",
           nl, nc, nw);
}

int main(int argc, char **argv)
{
    counter(argv[1]);
    return 0;
}
```

## 測試檔案內容
```
1
2
3
5

this is a test
```

## 編譯程式
```bash
$ gcc wc_func.c -o wc_func.o
```

## 執行結果
```
$ ./wc_func.o test
number of line: 6
number of char: 24
number of word: 8
```
