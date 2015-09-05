## 函式細講

函式(function)，可將一連串的 statements 集合起來。
在 main function 中，可藉由呼叫 function 以執行其所包含的 statements。

用 function 將 statements 集合起來的好處在於，使得 statements 更方便管理。
也使得 main function 更簡潔，讓開發者更容易閱讀。

### 函式定義
```c

return_type function_name(type parameter name, type parameters name){
    statements;
}
```

function 必須定義回傳值型態(function 不一定要有回傳值，可填 void)、
function name 以及欲傳入 function 中
中參數的型態與名稱。中參數的型態與名稱。

參數名稱對函式來說，是 local 的。也就是說，其他函式是無法看到這個名稱的。
其他函式也可用同一變數名稱，並無衝突。

同樣的，函式內變數也是 local 的，與 main function 中的變數並不互相影響。

如果沒有設定回傳 statement (return;)，則function回傳的值將無意義，
與完全沒寫 return 然後直接執行到 __}__ 一樣。

函式宣告後，若呼叫時用的方式或傳入的變數型態，
與宣告定義的用法不同，就會跳錯誤訊息。

而傳入參數的名稱可以不用遵守用法沒關係。

事實上，參數名稱在宣告定義時是 optional 的，也就是可寫可不寫。
