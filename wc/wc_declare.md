## 變數宣告與列印

### 變數宣告

```c
int nl, nc, nw;
nl = nc = nw = 2;
```

`int nl, nc, nw` 亦即宣告三個變數，此三變數存的是整數值。
nl (number of line) 表示行數, nc (number of character) 表示字元數,
nw (number of word) 表示字數。

`nl = nc = nw = 2` 即表示，此三個變數都給予整數值 2。在 C 語言中，
值的給予皆是從等號右邊傳遞給等號左邊。但若是 `==` 雙等號，
則表示比較等號左右兩邊值是否相等。

另，在 C 語言中，任何一個 statement 結尾一定都要有分號 ;

### 變數列印

`printf("number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw);`
使用函式的方法很簡單，直接打出函數名稱，並在函式名稱後的括弧內，
填入欲傳入之參數值。

從例子中，我們可看到，我們呼叫了 printf() 這個函式，且傳入了
`"number of line: %d\nnumber of char: %d\nnumber of word: %d\n", nl, nc, nw` 這一串參數。

首先看到雙引號內"" 之參數值。這裡表示列印出來後之骨幹及格式。
`%d` 表示變數值將會在該位置被列印出來。而`\n`則表示換行符號。
雙引號後，則是依序將欲列印出之變數擺放上去，並以逗號區隔。

