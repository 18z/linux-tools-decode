###  需要：stdio.h 標頭檔

函式：`int fprintf (FILE *stream, const char *template, …)`

This function is just like printf, except that the output is written to the stream stream instead of stdout.
>`此函式與 printf 類似，相異處在於 output 是寫到 stream stream 而非 stdout。`


函式：`int printf (const char *template, …)`

The printf function prints the optional arguments under the control of the template string template to the stream stdout.
>`printf 函式將 optional arguments 以 template string 之格式，將 output 寫到 stdout。`

It returns the number of characters printed, or a negative value if there was an output error.
>`此函式回傳印出之字元總數。若有錯誤發生則回傳一負數值。`


### 參考文獻
* http://www.gnu.org/software/libc/manual/html_node/Formatted-Output-Functions.html
* https://bytes.com/topic/c/answers/221662-void-printf-vs-printf
