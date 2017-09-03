#git 命令
	
##1.git 安装与配置
	- $ git config --global user.name "Your Name" 配置姓名
	- $ git config --global user.email "email@example.com" 配置邮箱
	- $ git config --global color.ui true 让git显示颜色

##2.git仓库创建	
	- $ git init 创建版本库

##3.git日志
	- $ git status 查看状态
	- $ git diff readme.txt	查看修改内容
	- $ git log 查看日志
	- $ git log --pretty=oneline  简单查看日志
	- $ git log --graph --pretty=oneline --abbrev-commit 图形日志
	- $ git reflog  记录每一次命令

##4.git版本提交与回退
	- $ git add readme.txt	添加修改到暂存区
	- $ git commit -m "add distributed"  提交到分支.
	- $ git reset --hard HEAD^  版本回退到上一版本
	- $ git reset --hard 3628164 版本回退到对应commit id

##5.删除文件
	- $ git rm test.txt 删除文件
	- $ git commit -m "delete"  提交到分支.
	
##6.撤销修改
	- $ git checkout -- readme.txt 丢弃工作区的修改
	- $ git reset HEAD readme.txt  把暂存区的修改回退到工作区

##7.分支
	- $ git checkout -b dev 创建并切换，相当于
	- $ git branch dev 创建dev分支 
	- $ git checkout dev 切换到dev分支。
	- $ git branch 查看当前分支
	- $ git merge dev 把dev分支的工作成果合并到当前分支上
	- $ git branch -d dev 删除分支dev
	- $ git branch -D feature-vulcan  强行删除没有合并过得分支
	- $ git merge --no-ff -m "merge with no-ff" dev   不使用Fast forward模式的合并,log有分支，能看出曾做过合并.

##8.bug分支
	- $ git stash 隐藏当前工作现场
	- $ git stash list 查看被隐藏的工作现场
	- $ git stash pop 恢复被隐藏，把stash内容删除
	- $ git stash apply stash@{0} 恢复被隐藏的工作现场
	- $ git stash drop  删除stash内容。

##9.远程仓库
	- $ ssh-keygen -t rsa -C "youremail@example.com" 创建SSH Key
	- $ git remote add origin https://github.com/wallwiz/mygit.git 把本地仓库关联到github.
	- $ git push -u origin maste  远程库是空的，第一次推送master分支时，加上-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
	- $ git push origin master  推送分支到远程仓库
	- $ git clone https://github.com/wallwiz/gitskill.git 克隆到本地仓库.
	- $ git remote   查看远程仓库信息
	- $ git remote -v 	更详细的信息
	- $ git checkout -b dev origin/dev 创建远程dev分支到本地
	- $ git branch --set-upstream dev origin/dev  指定本地dev与远程origin/dev分支的连接
	- $ git pull 抓下提交
	- $ git push origin :dev 删除远程分支
	- $ git remote rm origin 删除远程库


##10.标签管理
	- $ git tag v1.0  打一个新标签到当前commit
	- $ git tag v0.9 6226 打标签到对应的commit id
	- $ git tag -a v0.1 -m "version 0.1 released" 3628164  创建带有说明的标签
	- $ git tag -s v0.2 -m "signed version 0.2 released" fec145a   通过-s用私钥签名一个标签
	- $ git tag       查看所有标签
	- $ git show v0.9 查看标签信息
	- $ git tag -d v0.1 删除标签
	- $ git push origin v1.0  推送标签到远程
	- $ git push origin --tags 推送全部未推送到远程的本地标签
	- $ git push origin :refs/tags/v0.9  从远程删除标签,先从本地删除,再从远程删除

##12.忽略文件
	- 1.在Git工作区的根目录下创建一个特殊的.gitignore文件
	- 2.写入要忽略的文件
	- 3.把.gitignore也提交到Git
	- $ git add -f App.class 强制添加文件
	- $ git check-ignore -v App.class  查看为何被忽略

##13.配置别名
	- $ git config --global alias.st status  将status别名为st,--global对当前用户起作用,不加只对当前仓库起作用
	- $ git config --global alias.unstage 'reset HEAD' 
	- 每个仓库的Git配置文件都放在.git/config文件中
	- 当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中

