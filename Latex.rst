
🔸LaTeX 
================================================================================

    1. LaTeX是一类用于编辑和排版的软件，用于生成PDF文档。
    2. 方便美观的数学公式编辑.
    3. 论文、简历利器

用LaTex刷简历，最好用现成的模板，不然从0开始就是找虐。




用LaTex写简历或者paper等，已经非常常见的。
在美国，甚至直接有人用LaTeX上课做笔记。所以，如果想让自己的简历显得professional一点，建议用LaTeX写。 

❗️❗️❗️ sharelatex网站上一堆模板，即改即显示即用即下载。❗️❗️❗️
❗️❗️❗️ sharelatex网站上一堆模板，即改即显示即用即下载。❗️❗️❗️
❗️❗️❗️ sharelatex网站上一堆模板，即改即显示即用即下载。❗️❗️❗️
ShareLatex是一个在线编辑Latex的网站，代码开源在Github上。你可以使用PC端的Latex，但是如果你无法遇到各种各样的编译问题，觉得麻烦的时候，ShareLaTeX绝对是你的福音。

What is LaTeX：LaTeX类似于html脚本语言，很容易上手。虽然也需要“编译”等才能生成pdf或者ps文档，但是实际上网上很有很多很漂亮、很专业的模板，我们只需要将自己相应的信息填入相应的位置即可。这样，生成的pdf、ps文档要好看得多。所以，很多学术会议都有自己的LaTeX模板，投稿者只需要把相应的内容复制到相应的代码段中，生成的pdf文件就是又漂亮、又符合要求的论文，而不需要用word反复修改格式。当然，如果你要自己从头开始写一个完整的LaTeX代码，而不用模板，那么还是很麻烦的.......不知道我解释清楚没有......P.S.实际上，有的美国学生（当然，主要以计算机系的学生为主），鄙视用word的。因为word收到攻击的可能性大，而且也不好看，这种人比较geek。最近有关于LaTeX的课程作业，发现LaTeX确实不错。再看当年申请时候用MS Word生成的pdf，顿时觉得很不专业，很丑。当然，因为是新生申请，所以没大碍。但是如果之前就会，那么这就很好了。 


How to use LaTeX： 
1、到网上搜索LaTeX的简历模板，推荐http://rpi.edu/dept/arc/training/latex/resumes/。 
2、将.tex文件下载下来，用记事本打开进行编辑，即替换掉他人的信息，将自己的信息替换到相应的位置。 
3、编译、运行、生成pdf。本来这一步需要专门的编译器如Lyx等的，但是发现有一个在线编译的好东东http://nirvana.informatik.uni-halle.de/~thuering/php/latex-online/latex.php?sprachauswahl=2&aufruf=22103。所以：1）将之前在.tex文件中修改好的代码复制到该网页的source code空白处，output format设置为pdf就可以了。2）点击compile进行编译（生成div文件）。3）点击下面红色的“PDF-Format! ”，这样就可以看到生成的pdf了，然后保存到自己的电脑上。 
Then, it's done~ 

但愿对各位同学有用。而且以后到了美国，一般都可能要用LaTeX的。 





🔸 sharelatex 
在线编辑. 个人免费. https://cn.sharelatex.com/
一系列模板... 省时省力..免去安装latex的麻烦.
还能在线预览pdf.还能直接下载!!!


如果只是简历制作. 推荐用在线编辑器. 不然下载个4G的 LaTex 也麻烦..
本地编辑器适合老师用来写课件.或者论文.




🔸LaTeX 文档编辑


⦿ 编辑器选择
    word 文档编辑需要用 word/pages 打开, latex文档也需要特别的软件.
    强烈推荐用 VS Code 安装个扩展就可以用了

⦿ LaTeX Language Support 扩展安装: 
    这个插件为VS Code提供了LaTeX语言支持。
    VS Code 菜单 ➜ “扩展” ➜ 安装


⦿ LaTeX Wokrshop 扩展安装

    这是主要的一个插件，提供了一个编译、智能提示、代码片段、引用提示的环境。
    安装完成已经可以使用了.但我们最好还要配置一下


⦿ LaTeX Wokrshop 扩展配置

打开VS Code > 首选项 > 设置
可以看到左边是可供调整的设置选项，右边用户设置区，分两种，用户设置和工作区设置。
用户设置会覆盖默认设置，并应用于所有工作区、项目，而工作区设置会覆盖用户设置，但仅在此项目中产生作用，我们要修改的是以下设置：

"latex-workshop.latex.toolchain": [
    {
        "command": "xelatex",
        "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-pdf",
            "%DOC%"
        ]
    }





还可以通过LaTeX Workshop:View PDF in new tab来达到如下效果：


⦿ 
    3. 有很多现成的模板!!! 
        示例模板: https://github.com/xueruini/thuthesis/releases
        下载解压 里面有很多文件.  其中 的 main .tex 后缀的就是Latex文档.
        我们用 vs code 打开这个文件.
        怎么实现PDF效果预览呢. 




🔸LaTeX 文档导出

⦿ 安装: 
    Mac 下的 LaTeX 其实有另一个名字: MacTex
    请到 http://www.tug.org/mactex/mactex-download.html 下载安装.

⦿ 使用:



