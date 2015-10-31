### 需要： unistd.h 標頭檔

函式：`int getopt (int argc, char *const *argv, const char *options)`

The getopt function gets the next option argument from the argument list specified by the argv and argc arguments.
>`getopt 函式從由參數 argv，argc 所定義的 argument list 中取得 next option argument。`

`Normally` these values come directly from the arguments received by `main`.
>`一般來說，參數值都是藉由 main function 中獲得的。`

The `options argument` is a `string` that specifies the option characters that are valid for this program.
>`參數 options 基本上就是 string，這個 string 是由 option characters (也就是可以由很多個 characters) 組成。而這些 characters 在程式裡面是 valid 的。(個人理解為，這些 characters 在程式裡有特殊用途。)`

An option character in this string can be followed by `a colon` (‘:’) to indicate that `it takes a required argument`.
>`option character 後面可接 :，表示此 option character 後面可接參數。`

If an option character is followed by `two colons` (‘::’), its `argument is optional`; this is a GNU extension.
>`若 option character 後面接 ::，表示此 option character 後面參數可接可不接。`

getopt has three ways to deal with options that follow non-options argv elements.
>`getopt 有三種處理 non-options argv elements 的方法。`

The special argument `‘--’` forces in all cases `the end of option scanning`.
>`Special argument -- ，停止所有的 option scanning。`

The default is to permute the contents of argv while scanning it so that eventually all the non-options are at the end.
>`argv 的 contents，在被 scanning 時，預設是被 permute (重新排列)的。如此，所有的 non-options 都會被排在最後。`

This allows options to be given in any order, even with programs that were not written to expect this.
>`這樣作使得 options 可以不用依照順序輸入。`

If the options argument string begins with a `hyphen` (‘-’), this is `treated specially`.
>`若 options argument 前面有接 -，則它會被 treated specially。`

It permits arguments that `are not options` to be returned as if they were `associated with` option character `‘\1’`.

POSIX demands the following behavior: The first non-option stops option processing. This mode is selected by either setting the environment variable POSIXLY_CORRECT or beginning the options argument string with a plus sign (‘+’).

The getopt function returns the option character for the next command line option.
When `no more option arguments` are available, `it returns -1`.
>`當 options arguments 被 scan 完了，no more option arguments are available 時，getopt 函式會回傳 -1。`

There may still be more non-option arguments; you must compare the external variable optind against the argc parameter to check this.
>`須搭配 external variable optind 來雙重確認是否 options arguments 都被 scan 完了。`

```c
argc -= optind;
argv += optind;

if (argc != 0)
    usage();
```

If the option `has an argument`, getopt returns the argument by storing it in the variable `optarg`.
>`若 option 後面有接參數，則所接參數值會被存放在 optarg 中。`

You don’t ordinarily need to copy the optarg string, since it is `a pointer into the original argv array`, not into a static area that might be overwritten.

If getopt finds an option character in argv that `was not included in options`, or `a missing option argument, it returns ‘?’` and `sets the external variable optopt to the actual option character`.
>`若輸入的參數在 option character 中找不到，則以 ? 代表，並將輸入參數值存放在 external variable optopt 中。`

If `the first` character of options is `a colon (‘:’)`, then getopt returns ‘:’ instead of ‘?’ to indicate a missing option argument.

In addition, if the external variable opterr is nonzero (which is the default), getopt prints an error message.

### 函式實際運用
```c
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int
main (int argc, char **argv)
{
  int aflag = 0;
  int bflag = 0;
  char *cvalue = NULL;
  int index;
  int c;

  opterr = 0;

  while ((c = getopt (argc, argv, "abc:")) != -1)
    switch (c)
      {
      case 'a':
        aflag = 1;
        break;
      case 'b':
        bflag = 1;
        break;
      case 'c':
        cvalue = optarg;
        break;
      case '?':
        if (optopt == 'c')
          fprintf (stderr, "Option -%c requires an argument.\n", optopt);
        else if (isprint (optopt))
          fprintf (stderr, "Unknown option `-%c'.\n", optopt);
        else
          fprintf (stderr,
                   "Unknown option character `\\x%x'.\n",
                   optopt);
        return 1;
      default:
        abort ();
      }

  printf ("aflag = %d, bflag = %d, cvalue = %s\n",
          aflag, bflag, cvalue);

  for (index = optind; index < argc; index++)
    printf ("Non-option argument %s\n", argv[index]);
  return 0;
```
### 執行結果
```bash
% testopt
aflag = 0, bflag = 0, cvalue = (null)

% testopt -a -b
aflag = 1, bflag = 1, cvalue = (null)

% testopt -ab
aflag = 1, bflag = 1, cvalue = (null)

% testopt -c foo
aflag = 0, bflag = 0, cvalue = foo

% testopt -cfoo
aflag = 0, bflag = 0, cvalue = foo

% testopt arg1
aflag = 0, bflag = 0, cvalue = (null)
Non-option argument arg1

% testopt -a arg1
aflag = 1, bflag = 0, cvalue = (null)
Non-option argument arg1

% testopt -c foo arg1
aflag = 0, bflag = 0, cvalue = foo
Non-option argument arg1

% testopt -a -- -b
aflag = 1, bflag = 0, cvalue = (null)
Non-option argument -b

% testopt -a -
aflag = 1, bflag = 0, cvalue = (null)
Non-option argument -
```

### 參考文獻
* http://www.gnu.org/software/libc/manual/html_node/Using-Getopt.html#Using-Getopt
* http://www.gnu.org/software/libc/manual/html_node/Example-of-Getopt.html
* http://wen00072-blog.logdown.com/posts/171197-using-getopt-parse-command-line-parameter
