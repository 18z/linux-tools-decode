## GCC 支援之 C 語言版本


### GCC 支援四種 C 語言標準。

1. C90 

	```
	# 編譯時可使用下列參數套用 C90 標準
	-ansi, -std=c90 or -std=iso9899:1990
	```

2. C94 或稱 C95 

	```
	# 編譯時可使用下列參數套用 C94 標準
	-std=iso9899:199409
	```

3. C99 

	```
	# 編譯時可使用下列參數套用 C99 標準
	-std=c99 or -std=iso9899:1999
	```

4. C11

	```
	# 編譯時可使用下列參數套用 C11 標準
	-std=c11 or -std=iso9899:2011
	```


若無特別指定 C 語言標準，GCC 預設使用 gun11 (-std=gnu11)

gnu11 = C11 + GNU extensions。

### 參考來源：
* [GCC 官方文件](https://gcc.gnu.org/onlinedocs/gcc/Standards.html)
* [C11 spec](http://www.open-std.org/jtc1/sc22/wg14/www/standards)

