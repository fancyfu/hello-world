gitbook pdf

![](/assets/3981391-7d5e93fba468f90b.png)

```
C:\Users\AllenIverson\Desktop\gitcourse&gt;gitbook pdf  
info: 7 plugins are installed  
info: 6 explicitly listed  
info: loading plugin "highlight"... OK  
info: loading plugin "search"... OK  
info: loading plugin "lunr"... OK  
info: loading plugin "sharing"... OK  
info: loading plugin "fontsettings"... OK  
info: loading plugin "theme-default"... OK  
info: found 3 pages  
info: found 0 asset files

EbookError: Error during ebook generation: 'ebook-convert' is not recognized as an internal or external command,  
operable program or batch file.1
```

错误提示：ebook-convert不是内部或外部命令，原因是GitBook在生成PDF的过程中使用到calibre的转换功能，没有安装calibre或安装了calibre没有配置环境变量都会导致转换PDF失败

```
C:\Users\AllenIverson\Desktop\gitcourse&gt;gitbook pdf  
info: 7 plugins are installed  
info: 6 explicitly listed  
info: loading plugin "highlight"... OK  
info: loading plugin "search"... OK  
info: loading plugin "lunr"... OK  
info: loading plugin "sharing"... OK  
info: loading plugin "fontsettings"... OK  
info: loading plugin "theme-default"... OK  
info: found 3 pages  
info: found 2 asset files  
info: &gt;&gt; generation finished with success in 8.6s !  
info: &gt;&gt; 1 file\(s\) generated1
```

安装calibre后，转换成功。PS：安装calibre后需要重新启动命令行窗口

1. calibre

下载地址

![](/assets/1.png)

```
ebook-convert

C:\Users\AllenIverson\Desktop\gitcourse&gt;ebook-convert  
用法: ebook-convert.exe input\_file output\_file \[options\]

转换不同格式的电子书。

input\_file 表示输入文件，output\_file 表示输出文件。这两者作为命令行参数必须指定到最前面。

输出的电子书格式可由 output_file 的扩展名得到。同时 output\_file 也可以是一种以 .EXT 为扩展名的特殊格式。在这种情况下，输出文件的名称则使用输入文件的名称。注意：文件名不能以连字号作为开头。如果 output_  
file 不含扩展名，那么它将被视为一个目录并将会在该目录下生成 HTML 格式的“开放式电子书\(OEB\)”。这些文件会被视为正常文件而被输出插件所识别。

在指定输入和输出文件后，您可以自定义特定的转换选项。根据输入和输出文件的类型不同可用的转换选项也不同。如需获取针对输入和输出文件的帮助，请在命令行中输入 -h。

对于转换系统的完整文档请查阅  
[https://manual.calibre-ebook.com/conversion.html](https://manual.calibre-ebook.com/conversion.html)

给 ebook-convert.exe 传有空格的参数时，请将参数包括在引号中。例如 "C:\some path with spaces"

选项:  
  --version       显示程序版本号并退出

-h, --help      显示此帮助信息并退出

--list-recipes  列出内建的订阅清单名。您可以通过如下命令创建基于内建订阅清单的电子书： ebook-convert "Recipe  
                  Name.recipe" output.epub1

ebook-convert –version

C:\Users\AllenIverson\Desktop\gitcourse&gt;ebook-convert --version  
ebook-convert.exe \(calibre 2.81.0\)  
Created by: Kovid Goyal [kovid@kovidgoyal.net](mailto:kovid@kovidgoyal.net)1
```

使用

![](/assets/2.png)

![](/assets/3.png)

![](/assets/4.png)

