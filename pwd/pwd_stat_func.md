## stat()

### 需要：sys/stat.h 標頭檔

函式：`int stat (const char *filename, struct stat *buf)`

The stat function returns information about the attributes of the file named by filename in the structure pointed to by buf.
>`回傳 information about the attributes of the file。`
>`個人理解，stat 回傳值只是表示，是否可取得該檔案的 attributes 而已。`
>`file 是 named by structure 中被 buf 指向的那個  filename。 buf -> filename`
>`個人理解，就是把 buf 這個 struct 指標變數，指向 filename。`

Q1: [In Linux, everything is a file](http://www.linux.org/threads/in-linux-everything-is-a-file.4245/)
>`"." 當前工作目錄，也是個 file。`

If filename is the name of a symbolic link, the attributes you get describe the file that the link points to. If the link points to a nonexistent file name, then stat fails reporting a nonexistent file.

The return value is 0 if the operation is successful, or -1 on failure.
>`若回傳值是 0，則表示可成功取得該 file 的各種 attributes，反之，若回傳值為 -1，則無法取得該 file 各種 attributes。`

In addition to the usual file name errors (see File Name Errors, the following errno error conditions are defined for this function:

ENOENT
The file named by filename doesn’t exist.

When the sources are compiled with _FILE_OFFSET_BITS == 64 this function is in fact stat64 since the LFS interface transparently replaces the normal implementation.

### 範例程式
```c
#include <stdio.h>
#include <sys/stat.h>

int main(int argc, const char *argv[])
{
    struct stat phy;
    int r;

    r = stat(".", &phy);

    printf("%d\n", r);
    printf("%d\n", phy.st_dev);
    printf("%llu\n", phy.st_ino);

    return 0;
}
```
### 參考文獻
* http://www.gnu.org/software/libc/manual/html_node/Reading-Attributes.html
* https://en.wikibooks.org/wiki/C_Programming/POSIX_Reference/sys/stat.h#Example
