## fopen 函式
以下內容引用自台大資工系 - 資訊系統訓練班投影片

```
在 C 語言中，將所有的資料(例如：硬碟上之檔案等)視為由一連串字元組成的資料流(stream)。

標準檔案I/O函數在fopen()開啟一個檔案後，
C語言會要求作業系統在主記憶體保留一塊空間做為檔案I/O的缓衝區。

所有檔案I/O動作則是對這塊缓衝區做字元的讀取跟寫入，
直到檔案被關閉後fclose()，檔案的內容才會真正寫回儲存設備。
```

### 使用方法
```c
FILE *fp = fopen("test", "r");
...
fclose (fp);
```

`fopen("test","r");`若成功讀取 test 檔案，則回傳檔案在記憶體中的位置(file pointer)。

在 stdio.h 中，FILE 被定義為一個 struct，該 struct 存取一個檔案的各種資訊 (例如檔案大小，等)

`*fp` 則是指標。

`FILE *fp`亦即 fp 存放著記憶體位置。該記憶體位置指向 fopen() 中 test 檔案在記憶體中的資料流。
而該資料流的型態為 FILE。(FILE 指標)

最後，在記憶體中的資料讀取或寫入完畢後，用 fclose(); 將更動內容寫回儲存設備。

### fopen 參數
```c
FILE *fopen(const char *filename, const char *mode)
```

fopen 接收兩個參數，const char *filename 與 const char *mode。
奇怪的是，兩參數宣告的型態是指標。為何還能使用 "test" 或 "r" 當作參數傳入？

以下內容來自 [stack overflow](http://stackoverflow.com/questions/15151377/what-exactly-is-a-c-pointer-if-not-a-memory-address)

```
A pointer value can be some kind of
ID or handle or a combination of several IDs
(say hello to x86 segments and offsets)
and not necessarily a real memory address.

This ID could be anything, even a fixed-size text string.
Non-address representations may be especially useful 
for a C interpreter.
```

大意：指標不一定存的是記憶體位置，存的有可能是 ID、handle 等。
ID 有可能是任何東西，甚至有可能是 string。
handle 不曉得是什麼，待查證。

## 參考文獻
* [stack overflow](http://stackoverflow.com/questions/15151377/what-exactly-is-a-c-pointer-if-not-a-memory-address)

* [C 程式設計 - 檔案處理](https://github.com/deanboole/linux-tools-remake/blob/master/ref/C_8.ppt)

* [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)
