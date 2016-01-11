### 標頭檔：stdio.h

### 函式： int fgetc (FILE *stream)

### glibc 手冊函式說明：

This function reads the next character as an **`unsigned char`** from the stream **`stream`** and returns its value, converted to an **`int`**. If an end-of-file condition or read error occurs, **`EOF`** is returned instead.

### 輸入
This function reads the next character as an **`unsigned char`** from the stream **`stream`**

此函式從串流中，將下一個字元以 unsigned char 型態讀取。

### 回傳值
This function returns its value, converted to an **`int`**. If an end-of-file condition or read error occurs, **`EOF`** is returned instead.

將 unsigned char 之值轉為 int 並回傳。若遇 end-of-file 或 read error 時，則回傳 EOF。

### 使用範例：
```c
```

### 參考文獻
[1] http://www.gnu.org/software/libc/manual/html_node/Character-Input.html
