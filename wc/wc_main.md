## Main function

### 程式起始點

在 [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf) 中，第 5.1.2.2.1 小節提到程式起始點 (program startup)，顧名思義，也就是每個程式被執行後，第一個被呼叫的 function。它叫做 __main__。

main function 可被定義為：

```c
/* 回傳值為 int 且無參數傳入 */
int main(void) { /* ... */ }
```

或

```c
/* 回傳值為 int 且有兩個參數 (argc, argv) 傳入 */
int main(int argc, char *argv[]) { /* ... */ }
```

一開始，我們先專注在第一種定義，`int main(void) { /* ... */ }
`，較複雜的定義`int main(int argc, char *argv[]) { /* ... */ } `，往後會介紹。

int 為回傳型態，即代表這個程式執行完畢後將回傳一整數值給 host environment。
main 則為函式的名稱。一般來說函式名稱可隨開發者定義，但 main 較特別，
因為它是所有 C 語言程式執行的起點。

main 後面有括弧()，括弧內則是 void。
此即表示無參數從 host environment 中傳入此程式。


### 參考文獻
* [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)
