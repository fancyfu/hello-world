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

