### 需要：errno.h 標頭檔

The error code macros are defined in the header file errno.h.
>`error code macros 被定義在 errno.h 標頭檔裡。`

All of them expand into integer constant values.
>`所有的 error code macros 都 expand into 整數 constant 值。`

Some of these error codes can’t occur on GNU systems, but they can occur using the GNU C Library on other systems.
>`部分 error codes 無法在 GNU systems 中 occur，但可在其他使用 GNU C Library 的系統中 occur。`

Macro: int ENOENT
>`出現在 pwd 中的 error code macro。`

No such file or directory. This is a “file doesn’t exist” error for ordinary files that are referenced in contexts where they are expected to already exist.
>`該 error code 表示：沒有該檔案或目錄。`

### 參考文獻
* http://www.gnu.org/software/libc/manual/html_node/Error-Codes.html
