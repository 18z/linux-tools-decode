### stdout 與 stderr 差別

在 test 目錄下創建兩檔案：file_created_by_root, file_created_by_user
除了 root 以外，其他使用者均不可讀寫 file_created_by_root。

```bash
$ ls -alh test/
total 48K
drwxrwxr-x  2 deanboole deanboole 4.0K Nov 12 11:20 .
drwxr-xr-x 37 deanboole deanboole  36K Nov 12 11:24 ..
-rw-------  1 root      root         9 Nov 12 11:20 file_created_by_root
-rw-rw-r--  1 deanboole deanboole    9 Nov 12 11:20 file_created_by_user
```
### 使用 deanboole 一般使用者帳號 grep host 字串

```bash
$ grep host test/*
grep: test/file_created_by_root: Permission denied
test/file_created_by_user:host 123
```

### 將執行結果導向 result.txt
```bash
$ grep host test/* > result.txt
grep: test/file_created_by_root: Permission denied
```

### 查看 result.txt 內容
```bash
$ cat result.txt
test/file_created_by_user:host 123
```

### 參考文獻
* http://www.jstorimer.com/blogs/workingwithcode/7766119-when-to-use-stderr-instead-of-stdout
* http://blog.longwin.com.tw/2013/03/stdin-stdout-stderr-redirection-2013/
