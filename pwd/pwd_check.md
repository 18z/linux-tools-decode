## Logical directory 檢查機制

前面介紹了如何用 getcwd 取得 physical working directory，
及使用 getenv 取得 logical working directory。

此篇文章將延伸 getenv，增設檢查機制，
檢查 $PWD is an absolute logical pathname referring to the current working directory.

### 檢查項目

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


1. 確認 getenv("PWD") 的回傳值不為 NULL，且 pwd 所指向的標的其值(*pwd) 是 / 根目錄。

    ```
    指標: pwd
    存放: /usr/bin/ 目錄位置
    pwd 為 '/' 根目錄，這一點不曉得為什麼，待研究。
    ```

2. 檢查是否能取得檔案 pwd 與 "." 的 attribute。
3. 再檢查兩個檔案的 device id 以及 inode number 是否相同。

### 參考來源
* http://src.gnu-darwin.org/src/bin/pwd/pwd.c


