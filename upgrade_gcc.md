## 升級 GCC 版本

### 從 4.8.4 版升級至 5.1.0 版

GCC 版本不同，會導致其預設使用的C語言標準版本不同。
例如：4.8.4 版本預設使用 C90 標準。而 5.1.0 版本則使用 C11 標準。

4.8.4 版本對於 C99 及 C11 標準的支援皆未完善。
5.1.0 版本，C99 及 C11 標準支援已完善。

GCC 最新版本，依據官網，現在是 5.2.0 版。
然而，為了方便更新，及聚焦在撰寫 C 語言上，我們使用最方便法(PPA)來更新 GCC。
該 PPA 上面，目前最新的 GCC 版本是 5.1.0 版。

因此，我們就先暫時更新至 5.1.0 版

### 升級方式 Personal Package Archive
```
# 新增 PPA
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test

# 更新套件列表
$ sudo apt-get update

# 安裝 GCC 5.1.0
$ sudo apt-get install gcc-5
```

### 設定 alias
```
# 編輯 ~/.bashrc 檔
$ vim ~/.bashrc

# 在 ~/.bashrc 中加入下列行
alias gcc='/usr/bin/gcc-5'

# 套用新設定
$ source ~/.bashrc
```

### 檢查更新結果
```
# GCC 版本檢查指令
$ gcc --version

# 檢查結果
gcc-5 (Ubuntu 5.1.0-0ubuntu11~14.04.1) 5.1.0
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

### 參考文獻

* [GCC 5.1.0](https://gcc.gnu.org/onlinedocs/gcc-5.1.0/gcc/Standards.html#Standards)
* [GCC 4.8.4](https://gcc.gnu.org/onlinedocs/gcc-4.8.4/gcc/Standards.html#Standards)
