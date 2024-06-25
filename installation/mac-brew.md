```bash
mac ~ % /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
git version 2.37.1 (Apple Git-137.1)

               开始执行Homebrew自动安装程序 
             [cunkai.wang@foxmail.com] 
          ['2024-06-25 09:27:58']['12.7']
       https://zhuanlan.zhihu.com/p/111014448 


请选择下列一个 数字编号 后回车
（这里只是下载brew，随意选。国内下载源有5种稍后让你选择配置）

1、通过清华大学下载brew
2、通过Gitee下载brew
3、！我已经安装brew，跳过克隆，直接带我去配置国内下载源
4、不克隆brew，只把仓库地址设置成Gitee
5、不克隆brew，只把仓库地址设置成清华大学

请输入序号: 1

    你选择了清华大学brew本体下载源
    
 Mac os设置开机密码方法：
    (设置开机密码：在左上角苹果图标->系统偏好设置->用户与群组->更改密码)
    (如果提示This incident will be reported. 在用户与群组中查看是否管理员) 
请输入开机密码，输入过程不显示，输入完后回车
Password:
已获取权限
  
==> 安装过程开始调用Brew官方安装脚本，提示会变成英文，看不懂的复制到在线翻译。
  如果下载速度慢可以ctrl+c或control+c重新运行脚本选择下载源

  ->  !!!!是否删除之前本机安装的Brew（是Y  否N） 我没有检测本机是否安装brew，选哪个都会继续运行  
  (Y/N):   Y

--> 脚本开始执行
未发现Git代理（属于正常状态）
         
  
              开始  进入brew官方安装脚本  开始
  
  
下载官方install.sh文件,当前目录是: /Users/mac
Cloning into 'brew-install-ck'...
remote: Enumerating objects: 19, done.
remote: Counting objects: 100% (19/19), done.
 ..........
/usr/local/include
/usr/local/lib
/usr/local/lib/pkgconfig
==> The following existing directories will have their owner set to hf:
 ..........
Press RETURN/ENTER 现在是brew官方安装提示，它需要你按回车键开始 other key to abort:
 ..........
==> /usr/bin/sudo /bin/chmod g+rwx /Users/hf/Library/Caches/Homebrew
==> /usr/bin/sudo /usr/sbin/chown -R hf /Users/hf/Library/Caches/Homebrew
==> Downloading and installing Homebrew...
remote: Enumerating objects: 271978, done.
remote: Counting objects: 100% (81158/81158), done.
remote: Compressing objects: 100% (9448/9448), done.
 ..........
 * [new branch]            fix-tap-migration-renames-with-api -> origin/fix-tap-migration-renames-with-api
 * [new branch]            load-internal-cask-json-v3 -> origin/load-internal-cask-json-v3
 * [new branch]            master               -> origin/master
 * [new branch]            tapioca-patch        -> origin/tapioca-patch
 * [new tag]               4.3.7                -> 4.3.7
 ..........
 * [new tag]               4.3.6                -> 4.3.6
remote: Enumerating objects: 33, done.
remote: Counting objects: 100% (20/20), done.
remote: Total 33 (delta 20), reused 20 (delta 20), pack-reused 13
Unpacking objects: 100% (33/33), 5.95 KiB | 174.00 KiB/s, done.
From https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew
 * [new tag]               4.0.29     -> 4.0.29
 * [new tag]               4.1.9      -> 4.1.9
 * [new tag]               4.2.14     -> 4.2.14
Switched to a new branch 'stable'
==> Fetching /usr/local/Homebrew...

==> Resetting /usr/local/Homebrew...
Reset branch 'stable'

==> Installation successful!

==> Homebrew has enabled anonymous aggregate formulae and cask analytics.
Read the analytics documentation (and how to opt-out) here:
  https://docs.brew.sh/Analytics
No analytics data has been sent yet (nor will any be during this install run).
 ..........
- Run brew help to get started
- Further documentation:
    https://docs.brew.sh

此步骤成功
         
  
  
                完成  退出brew官方安装脚本  完成
  
  
  
==> 配置国内镜像源HOMEBREW BOTTLE     
此处如果显示Password表示需要再次输入开机密码，输入完后回车
sed: /Users/hf/.zprofile: No such file or directory
有些电脑xcode和git混乱，再运行一次，此处如果有error正常。
xcode-select: error: command line tools are already installed, use "Software Update" to install updates


        Homebrew已经安装成功，接下来配置国内软件下载源。

请选择今后brew install的时候访问那个国内镜像，例如阿里巴巴，输入5回车。

1、中科大国内源（推荐）
2、清华大学国内源
3、上海交通大学国内源
4、腾讯国内源
5、阿里巴巴国内源(推荐) 
请输入序号: 5


    你选择了阿里巴巴国内源
    


        环境变量写入->/Users/hf/.zprofile


此步骤成功

==> 安装完成，brew版本

Homebrew 4.3.7
Homebrew前期配置成功
==> Updating Homebrew...
==> Downloading https://mirrors.aliyun.com/homebrew/homebrew-bottles/bottles-portable-ruby/portable-ruby-3.3.3.el_capitan.bottle.tar.gz
######################################################################### 100.0%
==> Pouring portable-ruby-3.3.3.el_capitan.bottle.tar.gz
==> Homebrew collects anonymous analytics.
Read the analytics documentation (and how to opt-out) here:
  https://docs.brew.sh/Analytics
No analytics have been recorded yet (nor will be during this `brew` run).

==> Homebrew is run entirely by unpaid volunteers. Please consider donating:
  https://github.com/Homebrew/brew#donations

Already up-to-date.

        Homebrew自动安装程序运行完成
          国内地址已经配置完成

  之前步骤选了删除本机brew的话，桌面多出一个Old_Homebrew文件夹，可以删除。

              初步介绍几个brew命令
查看版本：brew -v  更新brew版本：brew update
查找：brew search python（其中python替换为要查找的关键字）
安装：brew install python（其中python替换为要安装的名称）
本地软件库列表：brew ls

        
        欢迎右键点击下方地址-打开链接 点个赞吧
         https://zhuanlan.zhihu.com/p/111014448 

        如果遇到问题可以右键下面地址查看常见错误解决办法
        https://gitee.com/cunkai/HomebrewCN/blob/master/error.md

        brew官方地址：https://brew.sh/zh-cn/

 安装成功 但还需要重启终端 或者 运行 source /Users/hf/.zprofile   否则国内地址无法生效
  
mac ~ % 

```
