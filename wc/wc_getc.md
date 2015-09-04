## getc()
```c
int getc(FILE *stream)
```

`getc()`，從 file stream 裡面逐一讀取字元，並回傳 int 值。

照理說，單一字元的型態應該為 char，getc() 讀取完後，回傳的型態應該是 char。

但這裡卻回傳 int。

原因在於 char 不夠大，存不了 EOF。必須用 int 才存得進去。

### 參考文獻
* The C Programming Language 2nd Edition - K & R 聖經本

