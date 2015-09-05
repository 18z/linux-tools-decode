## 程式使用方法與錯誤訊息

### 程式內容
```c
#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

#define IN 1    /* inside a word */
#define OUT 0   /* outside a word */

/* count lines, words, and characters in input */
/* It is fundamental to c that char**x and char*x[]
   are two ways of expressing the same thing.*/

static void error_print (int perr, char *fmt, va_list ap)
{
    vfprintf (stderr, fmt, ap);
    if (perr)
        perror (" ");
    else
        fprintf (stderr, "\n");
    exit (1);
}

static void errf (char *fmt, ...)
{
    va_list ap;

    va_start (ap, fmt);
    error_print (0, fmt, ap);
    va_end (ap);
}

void counter(char *file)
{
    int c, nl, nw, nc, state;
    state = OUT;
    nl = nw = nc = 0;

    FILE *fp = fopen(file, "r");

    if (!fp)
        printf("cannot open file %s", file);

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
    if (argc < 2)
        errf ("usage: wc FILE");

    counter(argv[1]);
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
$ gcc wc_usage_error_msg.c -o wc_usage_error_msg.o
```

### 執行結果
```bash
$ ./wc_usage_error_msg.o test
number of line: 6
number of char: 24
number of word: 8

$ ./wc_usage_error_msg.o
usage: wc FILE
```
