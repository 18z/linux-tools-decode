## getchar()

### 使用目的

讀取使用者從鍵盤輸入之字元。
standard library (stdio.h) 提供了許多讀取字元的函式，getchar 是最簡單的。

### 使用方法
```c
c = getchar();
```

getchar() 所截取的 character 就會被存到變數 c 中。

### 搭配 while 迴圈使用
```
while((c = getchar()) != EOF){
    statements;
}
```

while 迴圈的 condition 是 `(c = getchar()) != EOF`。
`!=` 表示左右兩邊不相等，亦即`(c = getchar())` 不等於 EOF 時，
則執行 {...} 內容。

EOF 是 End of file 的縮寫。

### 為何需要 EOF ?

原因在於我們需要有一個標記來判斷是否已讀取到資料或檔案的結尾。
該標記不能是任何可以被鍵盤打出來的字元。
因此，就設計了 EOF 這個標記，使得我們可以判斷是否已經讀取到資料或檔案的結尾。

當使用者輸入 Ctrl + d 時，也就是告訴程式這是資料或檔案的結尾了，
因此，getchar() 會回傳 EOF 值。
