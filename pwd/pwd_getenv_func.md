## getenv()

### 需要：stdlib.h 標頭檔

函式： `char * getenv (const char *name)`

### 函式回傳值與傳入參數
This function returns a `string` that is the `value of the environment variable name`.
>`此函式回傳一字串，該字串為環境變數之值。`

You must not modify this string.
>`該字串不能被修改。`

In some non-Unix systems not using the GNU C Library, it might be overwritten by subsequent calls to getenv (but not by any other library function).
>`尚未看懂。`

If the environment variable name is not defined, the value is a null pointer.
>`若環境變數沒給，回傳值為 null pointer。`

### getenv 與 getcwd 差別
```
# 將 test 資料夾當作是 /Users/xxx/Downloads 的捷徑
$ ln -s /Users/xxx/Downloads test

# 切換目錄到 test 底下
$ cd test

# 執行 getenv
$ ./getenv

# getenv 回傳 Logical 目錄
/Users/xxx/Documents/c-homework/examples/test

# 執行 getcwd 
$ ./getcwd

# getcwd 回傳 Physical 目錄
/Users/xxx/Downloads
```

### 參考文獻
* http://www.tutorialspoint.com/c_standard_library/c_function_getenv.htm
* http://www.gnu.org/software/libc/manual/html_node/Environment-Access.html
* http://stackoverflow.com/questions/6799470/can-a-pointer-to-a-string-be-used-in-a-printf


