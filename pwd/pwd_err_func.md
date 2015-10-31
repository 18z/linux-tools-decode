### 需要： err.h 標頭檔

函式： `void err (int status, const char *format, …)`

The err function is `roughly equivalent` to a call like `error (status, errno, format, the parameters)`
>`err 函式基本上跟 error 函式很相似。`

except that the global variables error `respects` and `modifies` are `not used` and that the program is `exited` even if status is `zero`.
>`前面看不懂。後面講 program 還是會  exited 即使 status 是 0。但還是看不懂。`

---

函式：`void error (int status, int errnum, const char *format, …)`

The error function can be used to report general problems during program execution.
>` error 函式用來 report 程式執行中所遇到之 general problems。`

The format argument is a format string just like those given to the printf family of functions.
>`format argument 是一個 format string，就像 printf 家族中所用的參數。`

The arguments required for the format can follow the format parameter.
>`可直接參考 printf 家族中的 %c, %s, %d 等參數。`

Just like perror, error also can report an error code in textual form.
>`error 也可以用 textual form 來 report an error code。`

But unlike perror the error value is explicitly passed to the function in the errnum parameter. This eliminates the problem mentioned above that the error reporting function must be called immediately after the function causing the error since otherwise errno might have a different value.

The error prints `first` the `program name`. If the application defined a global variable error_print_progname and points it to a function this function will be called to print the program name. Otherwise the string from the global variable program_name is used.
>`error 會先印出 program name。`

The program name is followed by a colon and a space which in turn is followed by the output produced by the format string.
>`program name 會在一個 colon 及一個 space 之後印出來。`

If the `errnum` parameter is `non-zero` the `format string output` is followed by a `colon` and a `space`, followed by the error message for the error code errnum. In any case is the output terminated with a newline.
>`若 errnum parameter 是非零值，則 format string output 就會在一個 colon 及一個 space 之後印出來。`

The `output` is `directed` to the `stderr stream`. If the stderr wasn’t oriented before the call it will be narrow-oriented afterwards.
>`output 會被導向 stderr stream。`

The function will return unless the status parameter has a non-zero value. In this case the function will call exit with the status value for its parameter and therefore never return. If error returns the global variable error_message_count is incremented by one to keep track of the number of errors reported.

### 參考文獻
* http://man7.org/linux/man-pages/man3/err.3.html
* http://www.gnu.org/software/libc/manual/html_node/Error-Messages.html

