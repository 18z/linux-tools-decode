## Autoconf, Automake

### 準備工作

1. 建立資料夾，並將程式移至 src 資料夾下

    ```
    $ mkdir project
    $ cd project; mkdir src;
    $ mv wc_func.c src/wc_func.c
    ```

2. 執行 autoscan 自動產生 configure.scan。並更改副檔名。

    ```
    $ autoscan
    $ mv configure.scan configure.ac
    ```

3. configure.ac 內容

    ```
    #                                               -*- Autoconf -*-
    # Process this file with autoconf to produce a configure script.

    AC_PREREQ([2.69])

    # 進行專案初始化，AC_INIT(安裝包名稱或專案名稱, 版本號,[聯絡資訊],[TarName])
    AC_INIT([wc-remake],[1.0],[xspiritualx@gmail.com])
    # 程式碼是否存在?
    AC_CONFIG_SRCDIR([src/wc_func.c])
    # 設定Automake版本最少為1.9
    AM_INIT_AUTOMAKE([1.9])
    # 確定C++編譯器是否存在
    AC_PROG_CC
    # 以下使用C++ Marco進行確認
    AC_LANG([C])

    # 是否有包含標準函式庫Header?
    AC_HEADER_STDC
    # 是否有包含string, iostream, fstream?
    AC_CHECK_HEADERS([string])
    AC_CHECK_HEADERS([iostream])
    AC_CHECK_HEADERS([fstream])

    # 告訴autoconf說本專案資料夾下有Makefile.am以及src/Makefile.am
    AC_CONFIG_FILES([Makefile])
    AC_CONFIG_FILES([src/Makefile])

    # 進行輸出
    AC_OUTPUT
    ```

4. 準備以下四個文件

    ```
    1. AUTHORS：寫明作者資訊。
    2. ChangeLog：程式碼異動記錄。
    3. NEWS：最新消息
    4. README：軟體說明與介紹
    ```

5. 撰寫對應的Makefile.am

    ```
    # 專案資料夾底下 Makefile.am
    # 程式碼目錄位於src資料夾下
    SUBDIRS = src
    # 資料文件放在doc資料夾下
    docdir = doc
    # 說明文件位於README
    dist_doc_DATA = README
    ```

    ```
    # src資料夾底下的Makefile.am寫法：
    bin_PROGRAMS=wcremake
    wcremake_SOURCES = wc_func.c
    ```

6. 依序執行 aclocal, autoconf, automake --add-missing

### 參考文獻
*[[Linux] Autoconf, Automake](http://blog.allenworkspace.net/2013/04/linux-autoconf-automake.html)


