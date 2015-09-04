## 準備作業

### 作業系統版本：
Ubuntu 14.04.3 LTS"

```
# 檢查作業系統版本指令
$ cat /etc/*-release

# 檢查結果
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

### GCC (GNU Compiler Collection) 版本：
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4

```
# GCC 版本檢查指令
$ gcc --version

# 檢查結果
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

### GNU C Library 版本：
ldd (Ubuntu EGLIBC 2.19-0ubuntu6.6) 2.19

```
# 檢查 GNU C Library (glibc) 版本指令
$ ldd --version

# 檢查結果
ldd (Ubuntu EGLIBC 2.19-0ubuntu6.6) 2.19
Copyright (C) 2014 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
```

### 編輯器：VIM
```
# Ubuntu-14.04.3-LTS 內建 VIM 編輯器
# 新建立與編輯檔名為 documents 的 c 語言檔案
$ vim documents.c

# 推薦 vim  plugin
1. tComment : 幫助開發者快速註解或取消註解。
2. snipMate : 許多 C 語言snippets 可使用，加快開發速度。
              例如：打main 按 tab 鍵，即可幫開發者輸入整個 main function。
3. tagbar   : 協助使用者 trace code。

vim plugin 設定請參閱
https://github.com/deanboole/Provision/blob/master/vim/vimrc

# 推薦編輯排版套件：indent
自動排版 C 語言程式
```

### 套件需求：build-essential
```
# 更新套件列表
$ sudo apt-get update

# 安裝所需套件
$ sudo apt-get install build-essential
```
