# git 常用命令 #
	git config --global user.name "用户名"
	git config --global user.email "用户邮箱"
	因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识。
	注意：git config  –global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱
	cd xx ：            切换同磁盘内文件，xx：（加冒号切换磁盘）

   mkdir xx：         XX (创建一个空目录 XX指目录名)

   pwd：          显示当前目录的路径。

   **git init ：          把当前的目录变成可以管理的git仓库，生成隐藏.git文件。**

   **git add XX ：     把xx文件添加到暂存区去。（git add 把文件添加进去，实际上就是把文件添加到暂存区）**

   git  add --all  ：提交所有的

   **git commit –m "xx" ： 用命令 git commit告诉Git，把文件提交到仓库  –m 后面的是注释。**

							git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支（当前版本库，本地仓库）上。

   git status   ：     查看仓库状态（命令git status来查看是否还有文件未提交）

   git diff  XX ：     查看XX文件修改了那些内容

   git log    ：      查看历史记录
   
   git log --pretty=oneline  查看历史记录（精简模式）

   git reset  –hard HEAD^ 或者 git reset  –hard HEAD~   ：回退到上一个版本（一个^是回退一个版本）

                        (如果想回退到100个版本，使用git reset –hard HEAD~100 )

   cat XX         查看XX文件内容

   git reflog       查看历史记录的版本号id

   git reset  --hard +版本号 ：回到这个版本号的版本

	**撤销修改**
	第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit掉。
	第二：我可以按以前的方法直接恢复到上一个版本。使用 git reset  –hard HEAD^
	第三 ：git checkout -- XX  把XX文件在工作区的修改全部撤销。（在没有commit之前就是把文件夹在工作区和版本库里保持一致）
	命令git checkout -- readme.txt 中的 — 很重要，如果没有 -- 的话，那么命令变成切换分支了

   git rm XX   ：       删除XX文件

   **git remote add origin https://github.com/tugenhua0707/testgit ：关联一个远程库**

   **git push –u(第一次要用-u 以后不需要) origin master ：把当前master分支推送到远程库**

   **git clone https://github.com/tugenhua0707/testgit  ：从远程库中克隆**

   **git clone -b 分支名字 远程库地址 ：       克隆制定分支的远程库**

   git checkout –b dev  ：创建dev分支 并切换到dev分支上

   git branch  ：查看当前所有的分支

   **git checkout master ：切换回master分支**

   **git merge dev    ：在当前的分支上合并dev分支**
  
	分支管理策略合并dev分支，使用命令 git merge --no-ff  -m “注释” dev  --no-ff 表示禁用fast forword模式
	合并后当删除分支后查看历史记录的时候，被删除的分支信息还在

   **git branch –d dev ：删除dev分支**

   **git branch name  ：创建分支**

   git stash ：把当前的工作现场隐藏起来 等以后恢复现场后继续工作

   git stash list ：查看所有被隐藏的文件列表

   git stash apply ：恢复被隐藏的文件，但是内容不删除

   git stash drop ：删除文件

   git stash pop： 恢复文件的同时 也删除隐藏文件列表中恢复的文件

   git remote ：查看远程库的信息

   git remote –v ：查看远程库的详细信息

   git push origin master（分支名）  ：Git会把master分支推送到远程库对应的远程分支上,
   每个分支在githup中可以单独显示，没有合并的话，push谁谁就显示push的内容


> 当你从远程库克隆时候，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且远程库的默认名称是origin。





	远程仓库
     在了解之前，先注册github账号，由于你的本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要一点设置：
     第一步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，
	 如果有的话，直接跳过此如下命令，如果没有的话，打开命令行，输入如下命令：
	 ssh-keygen  -t rsa –C “youremail@example.com”, 由于我本地此前运行过一次，所以本地有
	 id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
	 第二步：登录github,打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，
	 在Key文本框里黏贴id_rsa.pub文件的内容。


	七：bug分支：

     在开发中，会经常碰到bug问题，那么有了bug就需要修复，在Git中，分支是很强大的，每个bug都可以通过一个临时分支来修复，修复完成后，合并分支，然后将临时的分支删除掉。
	比如我在开发中接到一个404 bug时候，我们可以创建一个404分支来修复它，但是，当前的dev分支上的工作还没有提交
	并不是我不想提交，而是工作进行到一半时候，我们还无法提交，比如我这个分支bug要2天完成，但是我issue-404 bug需要5个小时内完成。怎么办呢？还好，Git还提供了一个stash功能，可以把当前工作现场 ”隐藏起来”，等以后恢复现场后继续工作。
	所以现在我可以通过创建issue-404分支来修复bug了。
	首先我们要确定在那个分支上修复bug，比如我现在是在主分支master上来修复的，现在我要在master分支上创建一个临时分支，演示如下：
	修复完成后，切换到master分支上，并完成合并，最后删除issue-404分支