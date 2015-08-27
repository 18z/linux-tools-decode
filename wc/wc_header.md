## 標頭檔

### 何為標頭檔？

C 語言本身並無內建如輸入/輸出 (input/output)、記憶體管理 (memory management)及字串操作 (string manipulation) 等功能。

這些功能皆在 GNU C library 裡面被定義。GNU C library 是由許多 header 檔 (例如 stdio.h) 組成的。因此，透過在程式最開頭 include 這些 header 檔，即可在程式內使用特定功能。

### 引用 header 的方法
```
/* 引用標頭檔，即可在程式內使用輸入/輸出的功能 */
# include <stdio.h>
```

### 參考文獻
* [GNU C library](http://www.gnu.org/software/libc/manual/html_mono/libc.html)
