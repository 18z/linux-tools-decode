## wc_argv.md

```
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
    printf("line:\t%d\nword:\t%d\nchar:\t%d\n", nl, nw, nc);
}
```
