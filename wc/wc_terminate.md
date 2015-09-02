## 程式終止

### 何時終止與回傳值

根據 [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)，第 5.1.2.2.3 小節提到程式終止條件與回傳值，內文擷取如下：

```
If the return type of the main function is a type compatible with int,
a return from the initial call to the main function
is equivalent to calling the exit function
with the value returned by the main function as its argument;

reaching the } that terminates the main function
returns a value of 0.

If the return type is not compatible with int,
the termination status returned to the host environment is unspecified.
```

當程式回傳值與 int 型態是 compatible 時

則執行到 main function 最後一個 __}__ 或程式中出現 exit 時，程式即終止。並回傳 0 值。

當程式回傳值與 int 型態是 incompatible 時

則回傳給 host environment 的值便是 unspecified。

另，若最後回傳的值為 0 ，則表示程式執行成功。若回傳的值為非 0 之其他數值，
則表示執行過程中，發生錯誤。


* [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)
