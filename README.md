# cat

`bin` 下面的 [`cat.pl`](bin/cat.pl) 就像 `cat` 这个指令一样，
它可以连接（合并）多个文件，但 `cat` 是横向地合并，`cat.pl` 是
纵向地合并。

使用方法为：

    // 递归地引入其它文件：(mnemonics/巧记法: `@` 象形为递归)

    @include <-=path=

    // 原样地引入其它文件：(mnemonics: `%` **p**ercent/百分号 ---> **p**reserve/保留)

    %include <-=path=

    // Verbatim

    @include <-=path= 会变成 @include <-=path=
    %include <-=path= 会变成 %include <-=path=

    //  path 可以是绝对路径，比如：
    //
    //      "D:\tzx\git\cat\README.md"
    //      "D:\\tzx\\git\\cat\\README.md"
    //      "D:/tzx/git/cat/README.md"
    //      "~/git/cat/README.md"
    //
    //  也可以是相对路径（相对于当前处理的文本），比如：
    //
    //      "test/a.txt"
    //      "test/d/../b.txt"
    //      "../blog/README"

`cat.jar` 实现了类似的功能（使用 `make` 来生成 jar 包），两者的表现几乎一致。
使用实例见
[`tutorial_cat.jar_.md`](tutorial_cat.jar_.md) 和
[`tutorial_cat.pl_.md`](tutorial_cat.pl_.md)。

```git-diff
[1mdiff --git a/result_cat.pl_.txt b/result_cat.jar_.txt[m
[1mindex cd55ec1..ae92653 100644[m
[1m--- a/result_cat.pl_.txt[m
[1m+++ b/result_cat.jar_.txt[m
[36m@@ -144,11 +144,11 @@[m [mh.txt[m

    h <- y (no such file to %)[m

    Error openning file: [31m[./y.txt].[m[32m[y.txt].[m

    h <- z (no such file to @)[m

    Error openning file: [31m[./z.txt].[m[32m[z.txt].[m

h.end[m

```
