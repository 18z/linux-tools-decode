## 印出當前工作目錄

pwd 工具可協助使用者了解，當前在哪一個工作目錄工作。
此版程式加入 getopt 函式使用。
讓使用者可以選擇要印出 Logical 或 Physical working directory。

### 程式內容
```c
#include <sys/stat.h>
#include <sys/types.h>

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

static char *getcwd_logical(void);
void usage(void);

int
main(int argc, char *argv[])
{
    int physical;
    int ch;
    char *p;

    physical = 1;
    while ((ch = getopt(argc, argv, "LP")) != -1)
        switch (ch) {
        case 'L':
            physical = 0;
            break;
        case 'P':
            physical = 1;
            break;
        case '?':
        default:
            usage();
        }
    argc -= optind;
    argv += optind;

    if (argc != 0)
        usage();
    /*
     * If we're trying to find the logical current directory and that
     * fails, behave as if -P was specified.
     */
    if ((!physical && (p = getcwd_logical()) != NULL) ||
        (p = getcwd(NULL, 0)) != NULL)
        printf("%s\n", p);
    else
        printf("Something went wrong!\n");

    exit(0);
}

void
usage(void)
{
    printf("usage: pwd [-L | -P]\n");
    exit(1);
}

static char *
getcwd_logical(void)
{
    struct stat lg, phy;
    char *pwd;

    /*
     * Check that $PWD is an absolute logical pathname referring to
     * the current working directory.
     */
    if ((pwd = getenv("PWD")) != NULL && *pwd == '/') {
        if (stat(pwd, &lg) == -1 || stat(".", &phy) == -1)
            return (NULL);
        if (lg.st_dev == phy.st_dev && lg.st_ino == phy.st_ino)
            return (pwd);
    }

    return (NULL);
}
```


### 編譯程式
```bash
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 gcc -o pwd_getopt.o pwd_getopt.c
```

### 執行程式
```bash
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./pwd_getopt.o -L
/usr/src/myapp

$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./pwd_getopt.o -P
/usr/src/myapp

$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./pwd_getopt.o asdfj
usage: pwd [-L | -P]
```
