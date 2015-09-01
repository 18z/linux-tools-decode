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


### 參考文獻
* [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)
