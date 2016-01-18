### 標頭檔：stdio.h

### 函式：int getc (FILE *stream)

### glibc 手冊函式說明：

This is just like **`fgetc`**, except that it is permissible (and typical) for it to be implemented as a macro that evaluates the stream argument more than once. **`getc`** is often highly optimized, so it is usually the best function to use to read a single character.

### 輸入
This is just like **`fgetc`**, except that it is permissible (and typical) for it to be implemented as a macro that evaluates the stream argument more than once.

如同 **`fgetc`**，差異在 getc 以 macro 實作，可多次 evaluate the stream argument。

### 回傳值
如同**`fgetc`**

### 使用範例：

### 參考文獻
[1] http://www.gnu.org/software/libc/manual/html_node/Character-Input.html
