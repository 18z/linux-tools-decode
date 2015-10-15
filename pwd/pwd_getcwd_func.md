## getcwd()

### 需要：unistd.h 標頭檔

函式：`char * getcwd (char *buffer, size_t size)`


### 函式回傳值
The getcwd function `returns an absolute file name` representing the `current working directory`, 
>`getcwd 函式的回傳值是 an absolute file name，這個 file name 代表的是當前工作目錄 (current working directory)。`

回傳值是 char * 

[stack overflow](http://stackoverflow.com/questions/15151377/what-exactly-is-a-c-pointer-if-not-a-memory-address)

```
Normally, a pointer stores an address to an object or function. 
If it isn't storing an actual address (to an object or function), 
the result is implementation defined 
(meaning that exactly what happens and what the pointer now represents 
depends on your system and implementation, 
so it might be a handle or ID on a particular system, 
but using the same code/value on another system might crash your program).
```

### 函式參數
storing it in the `character array buffer that you provide`. 
>`file name 是存放在我們提供的字元陣列 buffer 中 (character array buffer)。`

The `size argument` is how you tell the system the allocation `size of buffer`.
>`size 這個 argument ，就是我們告訴系統 size of buffer 的 allocation。(其實沒有完全理解。)`

### pwd source code 中 getcwd(NULL, 0) 參數這樣給; 

The GNU C Library version of this function also `permits you to specify a null pointer for the buffer argument`. 
>`此函式的 GNU C Library 版本，允許使用者去 specify null pointer 給 buffer argument。`

Then getcwd `allocates a buffer automatically`, as with malloc (see Unconstrained Allocation). 
>`接著 getcwd 就會用 malloc 自動去 allocates a buffer。`

If the size is `greater than zero`, then the buffer `is that large`; `otherwise, the buffer is as large as necessary to hold the result`.
>`若 size 大於 0，則 buffer 就會是該數值。否則，buffer 大小就會依照實際情況來分配。`

The `return value` is `buffer on success` and `a null pointer on failure`. 
>`回傳值，成功的話就是 buffer 值，不成功就是 null pointer。`


### 什麼情況下此函式會出錯？
```
The following errno error conditions are defined for this function:

EINVAL
The size argument is zero and buffer is not a null pointer.

ERANGE
The size argument is less than the length of the working directory name. You need to allocate a bigger array and try again.

EACCES
Permission to read or search a component of the file name was denied.
```

### 心得與未知待學習
```
從這程式得知如何以最簡單方式建構出 pwd 的功能。
但是 getcwd() 的兩個參數到底為何是這樣給值，還需要多研究。尚未完全理解。
目前只能從文獻上看到允許 specify null pointer 給 buffer 以及 buffer size 可以怎麼給。

But why?
```
### 參考文獻
* [http://www.gnu.org/software/libc/manual/html_node/Working-Directory.html
](http://www.gnu.org/software/libc/manual/html_node/Working-Directory.html)