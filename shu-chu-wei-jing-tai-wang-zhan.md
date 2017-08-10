**3、使用gitbook发布电子书**

Gitbook简易教程 - WEB开发 - SegmentFault

使用命令对已经创建的Book进行编译

> 找到需要编译的书籍所在目录，执行gitbook serve 命令,在本电脑的默认路径为C:UsersQGYGitBookLibraryImportgitbooksimpletutorial，如图所示

Serving book on [http://localhost:4000](http://localhost:4000/)

浏览器访问链接[http://服务器IP:4000/](http://182.180.14.120:4000/)

[![](https://s1.51cto.com/wyfs02/M01/8E/60/wKioL1i-1sfCQww0AADfH8fxzdc660.png-wh_500x0-wm_3-wmp_4-s_4286105878.png "wKioL1i-1sfCQww0AADfH8fxzdc660.png-wh\_50")](https://s1.51cto.com/wyfs02/M01/8E/60/wKioL1i-1sfCQww0AADfH8fxzdc660.png-wh_500x0-wm_3-wmp_4-s_4286105878.png)

没有异常之后链接电子书目录到目标目录

~&gt; ln -s /home/sxzhou/source\_book/mdq\_guide\_mannul/\_book /home/sxzhou/dest\_book/mdq\_guide\_mannul

在/home/sxzhou/dest\_book/目录下执行，nohup python-m SimpleHTTPServer 8080

nohup:忽略输入并把输出追加到"nohup.out"

执行完上面的命令后不要执行ctrl+c，直接关闭窗口就ok了。

然后浏览器访问链接[http://服务器IP:8080/mdq\_guide\_mannul/index.html，如果没有出现和之前gitbook](http://服务器IP:8080/mdq_guide_mannul/index.html，如果没有出现和之前gitbook) serve测试一样的结果的话可能的情况是模拟的web服务器关闭了

