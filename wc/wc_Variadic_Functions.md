## 不定參數函數
有時我們無法確定傳入函數的參數到底會有多少，此時就可用不定參數。
註：須使用 `stdarg.h` 標頭檔才可使用此函數。

### 不定參數函數定義
```c
return_type function_name (type name, ...)
```

在括弧中，出現`...`者，就是不定參數函數的樣子了。

### 如何取得不定參數的值
```c
int add_em_up (int count, ...)
{
  va_list ap;
  int i, sum;

  va_start (ap, count);         /* Initialize the argument list. */

  sum = 0;
  for (i = 0; i < count; i++)
    sum += va_arg (ap, int);    /* Get the next argument value. */

  va_end (ap);                  /* Clean up. */
  return sum;
}

int main (void)
{
  /* This call prints 16. */
  printf ("%d\n", add_em_up (3, 5, 5, 6));

  /* This call prints 55. */
  printf ("%d\n", add_em_up (10, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10));

  return 0;
}
```

```
1.  You initialize an argument pointer variable of type va_list using va_start.
    The argument pointer when initialized points to the first optional argument.

    用 巨集(macro) va_list 宣告一個指標變數 ap。
    用 va_start 將 ap 內填入指向第一個參數的記憶體位置。

2.  You access the optional arguments by successive calls to va_arg.
    The first call to va_arg gives you the first optional argument,
    the next call gives you the second, and so on.

    用 va_arg 來呼叫下一個參數。

    You can stop at any time
    if you wish to ignore any remaining optional arguments.

    若呼叫到一半，想忽略剩下的參數，我們隨時可停止。

    It is perfectly all right for a function to access fewer arguments
    than were supplied in the call, but you will get garbage values
    if you try to access too many arguments.

3.  You indicate that you are finished with the argument pointer variable
    by calling va_end.

    藉由 va_end 來表示 ap 這個指標變數可以跟它說再見了。

    (In practice, with most C compilers, calling va_end does nothing.
    This is always true in the GNU C compiler.
    But you might as well call va_end just in case your program is
    someday compiled with a peculiar compiler.)
```


```c
static void error_print (int perr, char *fmt, va_list ap)
{
  vfprintf (stderr, fmt, ap); // 將錯誤訊息寫入 stderr 中
  if (perr)
    perror (" ");
  else
    fprintf (stderr, "\n");   // 印出錯誤訊息。
  exit (1);
}
```

```c
/* Print error message and exit with error status. */
static void errf (char *fmt, ...)
{
  va_list ap;

  va_start (ap, fmt);
  error_print (0, fmt, ap);
  va_end (ap);
}
```

### 為何不直接就 printf 訊息就好？而要這麼麻煩？
```
可能原因：使用多函數參數輸入，增加錯誤訊息擴充彈性。
```

### 為何使用 vfprintf 函式？
```
1. 想要使用 stderr 來顯示錯誤訊息。
2. 將不定參數內容寫入 stderr 中，需要用到 vfprintf 函式。
```

### vfprintf 用法
```c
int vfprintf(FILE *stream, const char *format, va_list arg)
```

```
The C library function
int vfprintf(FILE *stream, const char *format, va_list arg)
sends formatted output to a stream using an argument list passed to it.

vfprintf 將 argument list 內容送到 stream 中。
```

### 參考文獻
* [GNU libc](http://www.gnu.org/software/libc/manual/html_node/Variadic-Functions.html)
* [vfprintf](http://www.tutorialspoint.com/c_standard_library/c_function_vfprintf.htm)
