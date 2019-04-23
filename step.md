### git步骤 ###
>  git config --global user.name "用户名"
> git config --global user.email "用户邮箱"
> 因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识。
> 注意：git config  –global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱
> cd xx ：切换同磁盘内文件，xx：（加冒号切换磁盘）


> git init ： 把当前的目录变成可以管理的git仓库，生成隐藏.git文件。
> 
> git add XX ： 把xx文件添加到暂存区去。（git add 把文件添加进去，实际上就是把文件添加到暂存区）
> 
> git add --all ：提交所有的
> 
> git commit –m "xx" ： 用命令 git commit告诉Git，把文件提交到仓库 –m 后面的是注释。
> 
> 远程仓库
>  在了解之前，先注册github账号，由于你的本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要一点设置：
>  第一步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，
>  如果有的话，直接跳过此如下命令，如果没有的话，打开命令行，输入如下命令：
>  **（ssh-keygen  -t rsa –C “youremail@example.com”）**, 由于我本地此前运行过一次，所以本地有
>  id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
>  第二步：登录github,打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，
>  在Key文本框里黏贴id_rsa.pub文件的内容。
> 
> git remote add origin https://github.com/tugenhua0707/testgit ：关联一个远程库
> 
> git push –u(第一次要用-u 以后不需要) origin master ：把当前master分支推送到远程库
> 
> git clone https://github.com/tugenhua0707/testgit ：从远程库中克隆
> 
> git clone -b 分支名字 远程库地址 ： 克隆制定分支的远程库
> 
> git checkout –b dev ：创建dev分支 并切换到dev分支上