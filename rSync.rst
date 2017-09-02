❤️ 实例1
================================================================================

🔸 简介

目的: GCE 的简历网页 用 rsync 实时备份到 vps1 
GCE 是服务端. VPS1 是客户端

客户端（目标）：rsync(接收同步资源服务器)
服务端（源）：  lsyncd+rsync（发送资源服务器）

🔸 VPS1 准备设置.

⦿ 虚拟主机设置
我们要先在vps1上 创建虚拟主机.

:: 

    lnmp vhost add 
    ================================================
    Virtualhost infomation:
    Your domain: cv.0214.live
    Home Directory: /home/wwwroot/cv.0214.live
    Rewrite: none
    Enable log: no
    Create database: no
    Create ftp account: no
    ================================================


⦿ 查看nginx.conf 默认配置
    vi /usr/local/nginx/conf/nginx.conf
    确保include了 cv.0214.live.conf

⦿ 重启 Nginx 
    service nginx restart

🔸 GCE 准备设置.

⦿ SSH 密钥设置
    gce 要用ssh 来同步数据. 必须要配置ssh密钥.
    在gce上能不用密码直接ssh vps1 就可以.






🔸 GCE 设置.
CGE 是服务端. 发送数据给VPS1的. 为了提高效率lsyncd. 要使用 lsyncd 需要先安装 rsync 


⦿ 安装 lsync 
    yum install lsyncd -y
    安装 lsyncd 会自动安装 rsync.

⦿ 查看 lsync 版本
    ✘✘∙GCE ~ ➜ lsyncd --version
    Version: 2.2.2

⦿ 查看 rsync 版本 
    ✘✘∙GCE ~ ➜ rsync --version
    rsync  version 3.0.9  protocol version 30



⦿ 配置 lsyncd  
vi /etc/lsyncd.conf



settings {
        logfile = "/tmp/lsyncd.log",
        statusFile = "/tmp/lsyncd.status",
        insist = true,
        nodaemon   = true,
        statusInterval = 5,
        maxDelays = 3,
}
sync {
        default.rsyncssh,
        source = "/home/wwwroot/cv.0214.help",
        host="23.105.192.96",
        targetdir = "/home/wwwroot/cv.0214.live",

        rsync = {
                binary = "/usr/bin/rsync",
                archive  = true,
                compress = true,
                whole_file = false
        },
        ssh = {
                port = 2222,
                identityFile ="/Users/v/.ssh/id_rsa",
         }
}



⦿ 启动 lsyncd
    sudo lsyncd /etc/lsyncd.conf

⦿ 同步检验
    现在去vps1 的 /home/wwwroot/cv.0214.help文件夹.
    下面就多了很多文件了!!! 都是GCE上同步过来的.
    当然现在 vps1上你还不能用域名来访问同步过来的网页内容.
    你需要配置下 nginx 和域名解析.

⦿ 域名解析    cv.0214.live ➜ 23.105.192.96
⦿ 浏览器测试  cv.0214.live  和 cv.0214.help 的内容就一样了.

⦿ 修改同步测试
    修改 gce 的网页内容. 看看 vps1 的会不会变化.
    稍微有点延迟. 大概20秒左右 就会同步修改到 cv.0214.live


⦿ 开机启动



🔸 VPS1 设置.
VPS1 是客户端. 只需要就收数据. 所以只要安装 rsync 就可以了.
不用进行设置的.































参考  https://linux.cn/article-5849-1.html

参考 
http://www.voidcn.com/blog/ckl893/article/p-6046749.html


文件同步工具. 服务器和客户端都需要安装.
最常见是 rsync  调用corn的 时效性有点差.  其实有更好的选择: lsyncd
lsyncd也有多种工作模式可以选择，本地目录cp，本地目录rsync，远程目录rsyncssh。





❗️❗️❗️ 本地文件夹同步到服务器 , 本地为准❗️❗️
❗️❗️❗️ 本地文件夹同步到服务器 , 本地为准❗️❗️

客户端（目标）：rsync(接收同步资源服务器)
服务端（源）：  lsyncd+rsync（发送资源服务器）

（1）需要配置rsyncd.conf文件的一端，称为rsync server
（2）不需要配置rsyncd.conf文件的一端，称为rsync client



🔸 lsync 要求: 
Lua >= 5.1
rsync >= 3.1



🔸 lsynx 三种模式

  rsync、direct.   本地电脑内的文件夹同步, direct 性能高点而已. 
  rsyncssh         通过ssh 实现本地电脑和服务器之间的文件夹同步

  不同模式的配置是不一样的! 参数也是不一样的!!



🔸 安装

  ⦿ Centos 安装   yum install lsyncd -y
    默认安装配置文件地址是/etc/lsyncd.conf

  ⦿ Mac OS 安装   
    brew install lsyncd 

❗️ Mac 自带的 rsync 版本太旧了. 用 brew 安装个新版本的.
brew install rsync

❗️ 双方至少需要安装 rsync 3.0+ 版本.



🔸 Mac 本地测试 ✔︎
    本地 把一个文件夹 同步到另一个文件夹中..

    ⦿ 配置 
    sudo vi /etc/lsyncd.conf

      1 settings {
      2         logfile = "/tmp/lsyncd.log",
      3         statusFile = "/tmp/lsyncd.status",
      4         statusInterval = 5,
      5         maxDelays = 3,
      6 }
      7
      8 sync {
      9         default.rsync,
    10         source = "/Users/v/Desktop/vps22",
    11         target = "/Users/v/Desktop/vps33",
    12
    13         rsync = {
    14                 binary = "/usr/local/bin/rsync",
    15                 archive  = true,
    16                 compress = true,
    17
    18         },
    19
    20 }

    ⦿ 启动
    sudo lsyncd /etc/lsyncd.conf

    ⦿ 文件测试
      最初 vps22 里面是有文件的.  vps33 文件夹是新建的.
      启动后.  vps33 文件夹 就和 vps22 文件夹一样了.
      在vps22 文件夹里面修改. 会应用到 vps33
      vps33 文件夹的修改 不会影响 vps22 



🔸 异地测试. ✔︎
目标是把 mac 里的一个文件夹 同步到 centos vps 中.
这就需要 用到 rsyncssh 模式了.


  1 settings {
  2         logfile = "/tmp/lsyncd.log",
  3         statusFile = "/tmp/lsyncd.status",
  4
  5         insist = true,       ❗️❗️ 这行必须有
  6         nodaemon   = true,   ❗️❗️ 这行必须有
  7
  8         statusInterval = 5,
  9         maxDelays = 3,
 10 }
 11
 12 sync {
 13         default.rsyncssh,
 14
 15         source = "/Users/v/Desktop/vps22",
 16
 17         host="23.105.192.96",
 18
 19         targetdir = "/root/vps",
 20
 21         rsync = {
 22                 binary = "/usr/local/bin/rsync",
 23                 archive  = true,
 24                 compress = true,
 25                 whole_file = false
 26
 27         },
 28
 29         ssh = {
 30                 port = 2222,
                    identityFile ="/Users/v/.ssh/id_rsa",
                    -- ❗️❗️Mac 必须加私钥路径. 不然只能用密码登录.
 31         }
 32
 33 }
 34




🔸 Mac 源 配置

sudo vi /etc/lsyncd.conf

settings {
        logfile = "/tmp/lsyncd.log",
        //记录日志的文件

        statusFile = "/tmp/lsyncd.status",
        //运行状态文件
        
        statusInterval	=	5,
        //写入状态的时间间隔，默认是10s

        maxDelays = 3,
        //累计到多少所监控的事件激活一次同步，即使后面的delay延迟时间还未到
}

sync {
        default.rsyncssh,
        //同步模式. 有三种: default.rsync、default.direct

        source = "/Users/v/Desktop/vps",
        //同步源地址，使用绝对路径

        targetdir = "/root/vps",
        //同步的目标地址，使用绝对路径


        host = "104.224.139.45",
        //目标ip地址


        rsync = { binary = "/usr/local/bin/rsync" },
        // Mac 自带版本太老. 用brew 新版本的路径.

        ssh = {
          port = 2222,

        }

}


⦿ 启动❗️❗️❗️    sudo lsyncd /etc/lsyncd.conf
  用 lsyncd --help 查看 > 启动语法: lsyncd + 配置文件路径

⦿ 后台运行  sudo lsyncd /etc/lsyncd.conf &
⦿ 查看后台任务  jobs


⦿ 查看进程：  ps -ef | grep lsync
⦿ 查看日志..  tail -f /tmp/lsyncd.log 






⦿ 查看日志..  tail -f /tmp/lsyncd.status


⦿ 测试同步..


⦿ 启动
配置结束后，在命令行运行如下命令，即可完成lsync的启动。
lsyncd -pidfile /var/run/lsyncd.pid /etc/lsyncd.conf










🔸 配置说明


--开头表示注释

⦿ settings

logfile 定义日志文件
stausFile 定义状态文件
nodaemon=true 表示不启用守护模式，默认
statusInterval 将lsyncd的状态写入上面的statusFile的间隔，默认10秒
inotifyMode 指定inotify监控的事件，默认是CloseWrite，还可以是Modify或CloseWrite or Modify
maxProcesses 同步进程的最大个数。假如同时有20个文件需要同步，而maxProcesses = 8，则最大能看到有8个rysnc进程
maxDelays 累计到多少所监控的事件激活一次同步，即使后面的delay延迟时间还未到



⦿ sync
里面是定义同步参数，可以继续使用maxDelays来重写settings的全局变量。一般第一个参数指定lsyncd以什么模式运行：rsync、rsyncssh、direct三种模式：

default.rsync ：本地目录间同步，使用rsync，也可以达到使用ssh形式的远程rsync效果，或daemon方式连接远程rsyncd进程；
default.direct ：本地目录间同步，使用cp、rm等命令完成差异文件备份；
default.rsyncssh ：同步到远程主机目录，rsync的ssh模式，需要使用key来认证

source 同步的源目录，使用绝对路径。

target 定义目的地址.对应不同的模式有几种写法：
/tmp/dest ：本地目录同步，可用于direct和rsync模式
172.29.88.223:/tmp/dest ：同步到远程服务器目录，可用于rsync和rsyncssh模式，拼接的命令类似于/usr/bin/rsync -ltsd --delete --include-from=- --exclude=* SOURCE TARGET，剩下的就是rsync的内容了，比如指定username，免密码同步
172.29.88.223::module ：同步到远程服务器目录，用于rsync模式
三种模式的示例会在后面给出。

init 这是一个优化选项，当init = false，只同步进程启动以后发生改动事件的文件，原有的目录即使有差异也不会同步。默认是true

delay 累计事件，等待rsync同步延时时间，默认15秒（最大累计到1000个不可合并的事件）。也就是15s内监控目录下发生的改动，会累积到一次rsync同步，避免过于频繁的同步。（可合并的意思是，15s内两次修改了同一文件，最后只同步最新的文件）

excludeFrom 排除选项，后面指定排除的列表文件，如excludeFrom = "/etc/lsyncd.exclude"，如果是简单的排除，可以使用exclude = LIST。
这里的排除规则写法与原生rsync有点不同，更为简单：
监控路径里的任何部分匹配到一个文本，都会被排除，例如/bin/foo/bar可以匹配规则foo
如果规则以斜线/开头，则从头开始要匹配全部
如果规则以/结尾，则要匹配监控路径的末尾
?匹配任何字符，但不包括/
*匹配0或多个字符，但不包括/
**匹配0或多个字符，可以是/

delete 为了保持target与souce完全同步，Lsyncd默认会delete = true来允许同步删除。它除了false，还有startup、running值，请参考 Lsyncd 2.1.x ‖ Layer 4 Config ‖ Default Behavior。



rsync

（提示一下，delete和exclude本来都是rsync的选项，上面是配置在sync中的，我想这样做的原因是为了减少rsync的开销）

bwlimit 限速，单位kb/s，与rsync相同（这么重要的选项在文档里竟然没有标出）
compress 压缩传输默认为true。在带宽与cpu负载之间权衡，本地目录同步可以考虑把它设为false
perms 默认保留文件权限。
其它rsync的选项





🔸 启动
lsyncd -log Exec /usr/local/lsyncd-2.1.5/etc/lsyncd.conf








🔸 排除文件
这里的排除规则写法与原生rsync有点不同，更为简单：







