### 一步一步建構 linux wc 指令

#### 目標：一次只加入一個觀念，逐漸將 linux 中的 wc 撰寫完成。

```c
#include <stdio.h>

#define IN 1    /* inside a word */
#define OUT 0   /* outside a word */

/* count lines, words, and characters in input */
int main(){
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
    printf("line:\t%d\nword:\t%d\nchar:\t%d\n", nl, nw, nc);
}
```