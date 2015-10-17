## 印出當前工作目錄

pwd 工具可協助使用者了解，當前在哪一個工作目錄工作。

### 程式內容
```c
#include<stdio.h>
#include<stdlib.h>
       
int main(int argc, const char *argv[])
{   
    char * p;
       
    p = getenv("PWD");
    printf("%s\n", p); 
      
    return 0;
}   
```

### 編譯程式
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 gcc -o getenv getenv.c
```

### 執行程式
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./getenv
```

### 執行結果
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 ./getenv
/usr/src/myapp
```

