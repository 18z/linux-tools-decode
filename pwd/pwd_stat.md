## 印出當前工作目錄

pwd 工具可協助使用者了解，當前在哪一個工作目錄工作。
印出 logical directory，印出前程式設立許多檢查機制。
Check that $PWD is an absolute logical pathname referring to the current working directory.。

### 程式內容
```c
#include<stdio.h>
#include<stdlib.h>
#include<sys/stat.h>

int main(int argc, const char *argv[])
{
    struct stat lg, phy;
    char * pwd;

    if ((pwd = getenv("PWD")) != NULL && *pwd == '/') {
        if (stat(pwd, &lg) == -1 || stat(".", &phy) == -1)
            printf("can't return info from stat()\n");
        if (lg.st_dev == phy.st_dev && lg.st_ino == phy.st_ino)
            printf("%s\n",pwd);
    }

    return 0;
}
```

### 編譯程式
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 gcc -o getenv_stat getenv_stat.c
```

### 執行程式
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./getenv_stat
```

### 執行結果
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./getenv_stat
/usr/src/myapp
```

