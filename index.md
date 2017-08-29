git学习参考链接
http://www.cnblogs.com/schaepher/p/5561193.html
http://blog.csdn.net/u014343528/article/details/48787221
设置gitpages
http://www.cnblogs.com/yuanzm/p/3945814.html
http://blog.csdn.net/qibin0506/article/details/51813428

1. 点击 new repository

2.  repository name:必须是 用户名+.github.com
	yangxinquan0902.github.com

3. Description : 对这个仓库的描述

4. Public 公开

5. Initialize this repository with a README
	选中

6. 在仓库中 点击 setting--》Launch automatic page generator--->continu to layouts-->publish page
--------------------------------
1. 生成秘钥：
	ssh-keygen -t rsa -C "邮箱"
		一路回车
2. 去 c:users/admian/.ssh
		id_rsa	// 私有秘钥
		id_rsa.pub  // 共有秘钥
		打开id_rsa.pub 用 文本编辑器
3. 点击头像--》setting--》SSH and GPG keys-->new ssh key--->title-->赋值sshkey --->add ssh key

4.填写 我是谁
	git config --global user.name 用户名
	git config --global user.email 注册邮箱

	验证成功：
		git config -l




提交流程
--------------------------------------------
1. git clone 仓库名(域名)，项目到工作区（working directory）
2. 赋值个人站 到这个文件夹下
3. git add .  把代码放到缓存区(unstage)

	git config --global user.email "yangxinquan0902@163.com"
  	git config --global user.name "yangxinquan0902"

git config --global user.name查看用户名
git config –list查看用户信息


缓存区作用：
作为过渡层
避免误操作
保护工作区和版本区
分支处理


4. git commit -m "aaaa"
	把缓存区 带代码 放到 仓库(repository)


工作区直接到版本库：
		git commit –a –m ”aaaaaaaa”

5. git push 
	仓库 到 github














linux命令：
	cd 文件名字
	cd ..查找文件上一级
	clear清楚
	ls  查看目录
	echo 内容 > 文件名称
	cat 文件名称    查看文件内容
	mkdir  创建文件夹
	pwd   查看当前所在目录
	vi
	vim  建文件
		按esc--》:wq 回车

	rm 删除文件
	rmdir 删除空文件夹



git命令
git config --list参看配置列表
git status 参看状态
git log查看提交日志

对比
git diff 工作区到缓存区之间对比
git diff –cached(--staged) 缓存区到仓库之间对比
git diff master 工作区与仓库的对比

撤销
git reset HEAD  工作区撤销回缓存区
git checkout 工作区撤销回之前的仓库

删除
git rm text.txt工作区已经手动删除，然后删除缓存区
git rm -f text.txt  工作区和缓存区同时删除
git rm --cached text.txt  缓存区删除但工作区不删除






Git 命令详解及常用命令

关于git，首先需要了解几个名词，如下：
Workspace      //工作区
Index / Stage    //缓存区
Repository     //仓库区（或本地仓库）
Remote       //远程仓









一、新建代码库
// 在当前目录新建一个Git代码库
$ git init
 
// 新建一个目录，将其初始化为Git代码库
$ git init [project-name]
 
// 下载一个项目和它的整个代码历史
$ git clone [url]


二、配置
Git的设置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。
// 显示当前的Git配置
$ git config --list
 
// 编辑Git配置文件
$ git config -e [--global]
 
// 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"


三、增加/删除文件
// 添加指定文件到暂存区
$ git add [file1] [file2] ...
 
// 添加指定目录到暂存区，包括子目录
$ git add [dir]
 
// 添加当前目录的所有文件到暂存区
$ git add .
 
// 添加每个变化前，都会要求确认
// 对于同一个文件的多处变化，可以实现分次提交
$ git add -p
 
// 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] 
 
// 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]
 
// 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]

四、代码提交
// 提交暂存区到仓库区
$ git commit -m [message]
 
// 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]
 
// 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a
 
// 提交时显示所有diff信息
$ git commit -v
 
// 使用一次新的commit，替代上一次提交
// 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]
 
// 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] 


五、分支
// 列出所有本地分支
$ git branch
 
// 列出所有远程分支
$ git branch -r
 
// 列出所有本地分支和远程分支
$ git branch -a
 
// 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
 
// 新建一个分支，并切换到该分支
$ git checkout -b [branch]
 
// 新建一个分支，指向指定commit
$ git branch [branch] [commit]
 
// 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]
 
// 切换到指定分支，并更新工作区
$ git checkout [branch-name]
 
// 切换到上一个分支
$ git checkout -
 
// 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]
 
// 合并指定分支到当前分支
$ git merge [branch]
 
// 选择一个commit，合并进当前分支
$ git cherry-pick [commit]
 
// 删除分支
$ git branch -d [branch-name]
 
// 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]


六、标签
// 列出所有tag
$ git tag
 
// 新建一个tag在当前commit
$ git tag [tag]
 
// 新建一个tag在指定commit
$ git tag [tag] [commit]
 
// 删除本地tag
$ git tag -d [tag]
 
// 删除远程tag
$ git push origin :refs/tags/[tagName]
 
// 查看tag信息
$ git show [tag]
 
// 提交指定tag
$ git push [remote] [tag]
 
// 提交所有tag
$ git push [remote] --tags
 
// 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]

七、查看信息
	// 显示有变更的文件
$ git status
 
// 显示当前分支的版本历史
$ git log
 
// 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
 
// 搜索提交历史，根据关键词
$ git log -S [keyword]
 
// 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
 
// 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature
 
// 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
 
// 显示指定文件相关的每一次diff
$ git log -p [file]
 
// 显示过去5次提交
$ git log -5 --pretty --oneline
 
// 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn
 
// 显示指定文件是什么人在什么时间修改过
$ git blame [file]
 
// 显示暂存区和工作区的差异
$ git diff
 
// 显示暂存区和上一个commit的差异
$ git diff --cached [file]
 
// 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD
 
// 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]
 
// 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"
 
// 显示某次提交的元数据和内容变化
$ git show [commit]
 
// 显示某次提交发生变化的文件
$ git show --name-only [commit]
 
// 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]
 
// 显示当前分支的最近几次提交
$ git reflog


八、远程同步
	# 下载远程仓库的所有变动
$ git fetch [remote]
 
# 显示所有远程仓库
$ git remote -v
 
# 显示某个远程仓库的信息
$ git remote show [remote]
 
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
 
# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]
 
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
 
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
 
# 推送所有分支到远程仓库
$ git push [remote] --all

九、撤销
	// 恢复暂存区的指定文件到工作区
$ git checkout [file]
 
// 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]
 
// 恢复暂存区的所有文件到工作区
$ git checkout .
 
// 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]
 
// 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard
 
// 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]
 
// 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]
 
// 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]
 
// 新建一个commit，用来撤销指定commit
// 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]
 
// 暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop


