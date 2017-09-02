Github CLI
================================================================================

搞技术难免要用到github的. 必学技能.
git 分两种. 带界面的GUI 和没界面的CLI.
一般只要会GUI就可以了. 软件很多的. 很好用. 上手没难度.
如果你的Linux服务器不带视图界面就必须要用CLI
CLI 也不太难. 比GUI肯定麻烦点的. 没不要就别折腾CLI了.


🔸 Github CLI 实例
--------------------------------------------------------------------------------  

⦿ 目的:    
备份 CentOS7 服务器的 Web网站(/home/wwwroot/cv.0214.help) 到Github. 
注意这里web里面已经有文件的.不是空的文件夹.


⦿ 创建Git仓库


git 安装        yum install git 
查看版本        git --version
CD              cd /home/wwwroot/cv.0214.help
当前仓库状态    git status
初始化当前仓库  git init .
再次查看状态    git status
git 添加文件    git add .
git 提交修改    git commit -m "first commit"





⦿ 关联Github
git你可以本地用.也可以关联到github用.
绝大多数都是用github来备份的.

首先要把 github的账户密码加到 git 项目的配置文件中. 

添加 github 用户   $ git config --global user.name "Xu-Jian"
添加 github 邮箱   $ git config --global user.email "xujian0219@126.com"


⦿ 还要把 Centos服务器的密钥上传给Github
参考 DjangoCMS 里的git设置.

• CentOS7 生成密钥. 有的话可以直接用
~/.ssh 文件夹下有 id_rsa 和 id_rsa.pub 文件就可以.
我们要做的 就是把id_rsa.pub 里面的信息加到 github 账户设置的 ssh and gpg keys中.

• 查看 id_rsa.pub 
cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCyCsWVdb6mokKsXnEizJngMoLc8pRm+CrYYmaGJUGGCn2fSvMhx6/vs54hNAQ2CNpr0kR0VwHLGhW+OQd5V5Gk0ZXkgOWCfYjmYwUZUFc7KVlAIQKHjHtAEgxlLlT26wHGgTSJHHfyg++ZD6QX6YbMzffYtb3V6XLjnvjZ2Lx93ws/jEaxPMZOD2bvLlVRmhu8MyNOvsUOWy9ucf4kJpsZ+Ak2llSPLr6xrpQMwr0cqp2us7V0ue7l/QJU0T3EtH7q03pVAMywfJl9/fFKjc/a78amFFg6vhVuzvB4enqVBimcNQNDmXVjutc8qLN/EhMe3bvZBHFHjPgqngdIbpBp root@mail


复制内容. 
Github 账户设置 ➜  ssh and gpg keys ➜ new ssh key 
➜ title(随意填) CentOS7-GCE
➜ key  这里是重点.  一般是ssh-rsa 开头的.
➜ add sshkey



⦿ 测试密钥设置
    $ ssh -T git@github.com
    Hi Xu-Jian! You've successfully authenticated, but GitHub does not provide shell access.
    有 successfully 就说明添加成功了.
    现在centos 服务器就有权限修改你github里面的内容了.

现在本地web 是已经有内容的. 
github 上还没有建立项目.
我们需要先去gitgub建立一个项目! CV-web-
项目最好不要包含中文名!
然后就会给你一个 ssh 地址 git@github.com:Xu-Jian/CV-web-.git
这个地址我们等下用到.

cd /home/wwwroot/cv.0214.help

然后添加远程仓库   
git remote add origin git@github.com:Xu-Jian/CV-web-.git

push本地代码到远程仓库
git push -u origin master 

看现在就成功了!
去github新建的项目就会发现多出很多文件. 就说明成功了!!!






　　　　