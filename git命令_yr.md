#1.查看版本状态
**命令**

- `git status`  	——查看当前版本库的状态

- `git diff`		——查看当前相对上一次提交修改的内容
#2.版本回退
**命令**

- `git log       `                   显示从最近到最远的提交日志

- `git log   --pretty== oneline  `   显示log,但是不显示很多凌乱的信息

- `q     `                           显示log版本信息有很多，使用q键停止查看

- `git reset —hard head^ `        回退到上一个版本

- `git reset —hard head^^  `      回退到上上个版本

- `git reset —hard head~100 `     回退到之前100个版本

- `git reset —hard +commit_id`    回到某个版本号的版本

[问题说明：版本回退过多，想仍然使用被回退掉的最新版本](http://markdownpad.com)

情况一：曾经查看过log, 当前的命令窗口并未关闭，找到原来的版本号，使用如下命令恢复：

- `git reset — hard 版本号` 

情况二：命令行已经关闭，不知道原来的版本号。

使用`git reflog` 查看曾经使用过的命令，曾经回退版本的时候会在这里显示版本号，然后继续使用情况一中的方法，恢复版本。

#3.工作区与暂存区
- `git  add` 添加文件，是将文件修改添加到暂存区
- `git commit` 提交更改，实际是把暂存区的所有内容提交到当前分支

#4.管理修改


[问题说明:我们修改一个文件，第一次修改之后执行git add ，第二次修改不执行git add ,然后我们执行git commit并使用git status查看状态，可以发现第二次的修改并未提交。这是因为Git跟踪修改，如果不add到暂存区就不会加入到commit。](http://markdownpad.com)

解决方案：继续执行git add，再git commit，也可以别着急提交第一次修改，先add第二次修改再commit

#5.撤销修改
- 情况一: 文件修改后还没被add到暂存区，
	- `git checkout --  + 文件名`    将文件在工作区的修改全部撤销。
	
执行结果:

		让文件回到最近一次git commit或者add时的状态
- 情况二：想要撤销的部分已经add到暂存区，但是还没有被commit
	- 解决方法：使版本回退的方法

#6.删除文件
`rm + 文件名`     删除文件


#7.远程仓库
查看远程仓库地址：

	git remote -v

查看远程仓库日志：

	git log origin/master -n 3

查看远程与本地之间的差异

	git fetch origin
	git diff origin/master  master --minimal
查看所有分支

	git branch -a




###查看更多：https://www.jianshu.com/p/9b040c70d4db