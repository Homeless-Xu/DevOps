


★★★★★ https://www.ibm.com/developerworks/cn/opensource/os-sphinx-documentation/index.html


★★★★ PDF 方案:   http://wiki.jerrypeng.me/rest-tjlug/

★★★★★ Sphinx 使用手册:  http://zh-sphinx-doc.readthedocs.io/en/latest/markup/


Sphinx 使用手册:  https://zh-sphinx-doc.readthedocs.io/en/latest/contents.html






🔸 Sphinx 简介:
================================================================================

⦿ Blog VS Book
--------------------------------------------------------------------------------  

| 对于一些一两篇文章就能写清楚的可以记笔记或写博客， 
| 但是如果要写成一个系列的，不如写成一本书的形式，更美观，也更系统。
| 我们需要用纯文本格式来写书.这个通用性最强.而不是用专业的写书软件.
| 还要可以自动生成html 文件方便的分享到网络.

**最终架构: Sphinx + GitHub + ReadtheDocs**
    - 1.) 本地用 Sphinx 写书.  然后生成 html/pdf 
    - 2.) 把书同步到 GitHub 进行托管文档，
    - 3.) Github项目导出到 ReadtheDocs 网站.会给你一个网页链接.
    - 4.) 本地编辑 ➜  同步Github、自动生成 html ➜ 浏览器访问

Sphinx 用纯文本格式编写文档，然后可以输出成 html/pdf 
Sphinx 就是我们需要的工具. 和 markdown 一样类似的标记语言.




⦿ Sphinx 简介
--------------------------------------------------------------------------------  

Sphinx 是一种文档工具，它可以令人轻松的撰写出清晰且优美的文档.
Sphinx 最初是为了方面开发者浏览 Python 语言的说明文档而创建的.
Python 有许许多多的命令. 各种各样的使用方法. 要把Python 使用方法写清楚
必须有清晰的文章结构. Spring 就可以做到这一点.

Sphinx 可以导出HTML 和 PDF
生成HTML 简单. 但是要生成PDF 就得额外安装软件
要生成pdf的话，很麻烦! 需要先安装Latex，推荐使用MacTex，它的安装包约有2GB，安装需要4GB的空间。
PDF 建议用在线的 Latex 编辑器. 省时省力.能写出非常好看的PDF文档.


Sphinx 实例: http://azuwis.github.io/sphinx_demo/demo.html
上面的文档. 结构清晰. 一目了然. 非常适合写书籍.


书本是以章节为单位的! 每个章节一个单独的.rst文件.
然后把所有的 .rst 章节都放入到目录索引中.就变成书了.

项目根目录创建chapter1.rst, chapter2.rst和chapter3.rst 三个章节的文档源码，
但是初建编译时，并不会被编译进去，还得在index.rst中把这些文件包含进来。
在rst中配置文件index.rst 中把章节包含到其中

- toctree用来于产生目录表，
- numbered表示章节带标题，
- maxdepth表示目录中只显示几层标题

:: 

    Contents:

    .. toctree:: 
       :maxdepth: 2 
       :numbered:

       chapter1 
       chapter2 
       chapter3









🔸 安装 Sphinx

    pip install sphinx sphinx-autobuild sphinx_rtd_theme

    ⦿ 查看版本: sphinx-build --version
    ⦿ 语法:     Usage: sphinx-build [options] sourcedir outdir [filenames...]


🔸 创建Sphinx项目

    sphinx-quickstart
        会进入一个设置向导，根据向导一步一步设置文档项目，其实必填项只有项目名称，作者和版本，其他设置都可以一路回车：

            文档根目录(Root path for the documentation)，默认为当前目录(.)
            是否分离文档源代码与生成后的文档(Separate source and build directories): y
            模板与静态文件存放目录前缀(Name prefix for templates and static dir):_
            项目名称(Project name) : EvaEngine
            作者名称(Author name)：AlloVince
            项目版本(Project version) : 1.0.1
            文档默认扩展名(Source file suffix) : .rst
            默认首页文件名(Name of your master document):index
            是否添加epub目录(Do you want to use the epub builder):n
            启用autodoc|doctest|intersphinx|todo|coverage|pngmath|ifconfig|viewcode：n
            生成Makefile (Create Makefile)：y
            生成windows用命令行(Create Windows command file):y


    最后会生成Sphinx一个文档项目必需的核心文件.

    ⦿ 项目结构
        .
        ├── Makefile
        ├── _build
        ├── _static
        ├── _templates
        ├── conf.py
        ├── hello.rst
        ├── index.rst
        └── make.bat



Makefile：编译过代码的开发人员应该非常熟悉这个文件，如果不熟悉，那么可以将它看作是一个包含指令的文件，在使用 make 命令时，可以使用这些指令来构建文档输出。
_build：这是触发特定输出后用来存放所生成的文件的目录。
_static：所有不属于源代码（如图像）一部分的文件均存放于此处，稍后会在构建目录中将它们链接在一起。
conf.py：这是一个 Python 文件，用于存放 Sphinx 的配置值，包括在终端执行 sphinx-quickstart 时选中的那些值。
index.rst：文档项目的 root 目录。如果将文档划分为其他文件，该目录会连接这些文件。




向导中的所有设置都保存在conf.py中，可以随时调整。



🔸 添加文章: 

根目录添加 hello.rst
hello,world
=============


然后修改
index.rst 修改如下:

::

    Contents:
    .. toctree::
    :maxdepth: 2
   
    hello



🔸 更改主题

vi conf.py
html_theme = "sphinx_rtd_theme"




🔸 预览效果





🔸 Sphinx 实时预览工具: Marboo Pro
    https://amoblin.gitbooks.io/marboo-guide/content/zh-cn/04-document-generator-settings/4.3%20sphinx.html


    - 生成HTML
    - 修改 marboo 配置

















🔸 Sphinx 基本语法
================================================================================


🔸 Sphinx 标记:
    
    标记段一般要与前一段落用空行格开，标记段结束要与下一段落用空行格开，









🔸 大标题

This is a Title
===============
That has a paragraph about a main subject and is set when the '='
is at least the same length of the title itself.


🔸 小标题

Subject Subtitle
----------------
Subtitles are set with '-' and are required to have the same length 
of the subtitle itself, just like titles.
 


🔸 无序列表
--------------------------------------------------------------------------------   
 * Item Foo
 * Item Bar

🔸 有序列表
--------------------------------------------------------------------------------    
 #. Item 1
 #. Item 2
 





⦿ 标题
--------------------------------------------------------------------------------  

- 一级标题： = 
- 二级标题： - 
- 三级标题： + 
- 四级标题： ^


⦿ 行内标记
--------------------------------------------------------------------------------  

| 一个星号里表示斜体: *text*
| 两个星号表示粗体: **text**
| 两个反斜号表示行内代码: ``text``

标记前后要有空格的不然报错.你的文件中含有这个肯定会报错 ``thisis*one*word``

``thisis\ *one*\ word`` 来实现 thisis\ *one*\ word
使用反斜杠对 星号前后的空格进行转义 


⦿ 换行
--------------------------------------------------------------------------------  

|   默认段落内是不换行的. 这个很麻烦.
|   要换行 最简单的办法是在每行最前面加上 | 这个符号. 
|   就会换行了.



⦿ **代码块**
--------------------------------------------------------------------------------  

:: 

    It is not processed in any way, except
    that the indentation is removed.

    It can span multiple lines.




⦿ 链接
--------------------------------------------------------------------------------  

.. raw:: html  

    <a href="http://www.0214.help">网站链接</a>



⦿ 图片
--------------------------------------------------------------------------------  

.. image:: ./_static/finger.png

不支持 png 格式的图片的. jpg 可以.








🔸 表格
--------------------------------------------------------------------------------  


=====  =====  =======
  A      B    A and B
=====  =====  =======
False  False  False
True   False  False
False  True   False
True   True   True
=====  =====  =======






🔸 精简实例
================================================================================


- 1.) 项目初始化        sphinx-quickstart 
- 2.) 改 conf.py 85行:      html_theme = "sphinx_rtd_theme" 
- 3.) 改 index.rst 

        :: 

            .. toctree::
                :maxdepth: 2
                :caption: Contents:

            改成下面格式. SS_SSR 是文件名. 不用.rst后缀!  

            .. toctree::
                :maxdepth: 2
                :caption: Contents:

                SS_SSR



🔸 详细实例.
================================================================================

github 网页创建新项目:下载到本地.

⦿ 项目初始化
    sphinx-quickstart
        输入项目名 + 作者 + 语言 zh_CN 其他全部默认.

⦿ sphinx 主题修改
    vi conf.py   85行 修改:    html_theme = "sphinx_rtd_theme"

⦿ 生成 html 文档
    make html

⦿ 本地预览:
    浏览器 打开文件 ➜  file:///Users/v/Desktop/SS-SSR/_build/html/index.html
    就可以看到网页了. 但是现在什么内容都没有,我们要新加个文件进去.

⦿ 创建文件: SS_SSR.rst

⦿ SS_SSR.rst 内容:
::

    This is a Title
    ===============

    =====  =====  =======
    A      B    A and B
    =====  =====  =======
    False  False  False
    True   False  False
    False  True   False
    True   True   True
    =====  =====  =======




⦿ 编辑 index.rst

:: 
    .. toctree::
        :maxdepth: 2
        :caption: Contents:

    改成 

    .. toctree::
        :maxdepth: 2
        :caption: Contents:

        SS_SSR


注意!
SS_SSR上边一个空行. 
SS_SSR左边是3个空格. 必须和上面的:冒号在同一列.




⦿ 本浏览

下面刷新网页. 就出来了.
但是现在文章的结构不行. 
你要自己设置 标题. 
这些只是语法问题. 不难的. 
下面我们怎么才能把书本放到网络.
我们这里用github.
把项目上传同步到github去先.


🔸 设置 ss-ssr 项目 
--------------------------------------------------------------------------------  

| github ➜ ss-ssr 项目 ➜ settings ➜ integrations & services ➜ Add services ➜ ReadtheDocs
| 必须先开启GitHub项目里面的 readthedoc 服务.才能在把这个项目添加到 readthedoc网站里面.
| readthedoc网站才能给你的项目生成一个链接. 让你可以用浏览器访问

🔸 注册 Read the Docs
--------------------------------------------------------------------------------  

 　https://readthedocs.org/

注册. 然后绑定github. ➜ import a project ➜ 选择项目 ➜ 阅读文档 
http://ss-ssr.readthedocs.io/en/latest/
就出现了.... 
当然 有个小小的广告. 免费服务么.... 无所谓了...
现在整个流程都清楚了.
下面就来完善文档结构了额.
















































