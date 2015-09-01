## Main function

### 程式起始點

在 [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf) 中，第 5.1.2.2.1 小節提到程式起始點 (program startup)，顧名思義，也就是每個程式被執行後，第一個被呼叫的 function。它叫做 __main__。

main function 可被定義為：

```c
/* 回傳值為 int 且無參數傳入 */
int main(void) { /* ... */ }
```

或

```
/* 回傳值為 int 且有兩個參數 (argc, argv) 傳入 */
int main(int argc, char *argv[]) { /* ... */ }
```

### 若 main function 有參數傳入

則須遵循以下規定 (英文部分，從手冊擷取)：

— The value of argc shall be nonnegative.

```
argc 之值不可為負數。
```

— argv[argc] shall be a null pointer.

```
argv[argc] 須為 null 指標。
```

— If the value of argc is greater than zero, the array members argv[0] through argv[argc-1] inclusive shall contain pointers to strings, which are given implementation-defined values by the host environment prior to program startup. 

The intent is to supply to the program information determined prior to program startup from elsewhere in the hosted environment. If the host environment is not capable of supplying strings with letters in both uppercase and lowercase, the implementation shall ensure that the strings are received in lowercase.

```
若 argc 數值大於零，則 argv[0] 至 argv[argc-1] 陣列之值，
須為指向 strings 的指標。
這些值則是在 program startup 之前從 host environment 中取得的。

主要目的在於，支援程式獲取從系統環境中取得所需資訊。
若無法確定，host environment 是否同時支援傳入之字串字母大小寫，則字串一律用小寫。
```

— If the value of argc is greater than zero, the string pointed to by argv[0] represents the program name; argv[0][0] shall be the null character if the program name is not available from the host environment. If the value of argc is greater than one, the strings pointed to by argv[1] through argv[argc-1] represent the program parameters.

```
若 argc 數值大於零，則 argv[0] 指向的就是 program name 的字串。
若無法從 host environment 取得 program name，
則 argv[0][0] 之值為 null。

若 argc 數值大於一，則 argv[1] 至 argv[argc-1] 陣列
所指向的就是 program parameters。 
```

— The parameters argc and argv and the strings pointed to by the argv array shall be modifiable by the program, and retain their last-stored values between program startup and program termination.

```
參數 argc、argv 以及 argv 陣列所指向的 string，皆可以被 program 修改。
且在 program startup 及 program termination 之間，
它們的 last-stroed values 皆可被保存。
```

### 參考文獻
* [C11標準文件](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)
