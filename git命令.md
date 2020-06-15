社区 凡是你能想到的基本上都已经有人实现了
组织 商业公司 基金会 联合国
凡是可以用js实现的 最终一定会用js实现

CVS、SVN这些免费的版本控制系统 集中式 版本控制系统

Git 是目前世界上最先进的 分布式 版本控制系统 linux作者
协作编辑 协同办公

GitHub网站 远程仓库 开源项目免费提供Git存储
vscode TS 口碑 atom sublime 微软收购git 私有仓库免费 云服务器

分布式版本控制系统通常也有一台充当“中央服务器”的电脑 不关机 中介

```
git --version
git --help

.gitconfig

git config --global user.name "Your Name"
git config --global user.email "email@example.com"

初始化仓库
git init

readme.txt U
第一步，用命令git add告诉Git，把文件添加到暂存区：[staged]
git add readme.txt
git add readme.txt test.txt
git add .
# 没有任何报告 没错就不报告

readme.txt A

第二步，用命令git commit告诉Git，把文件提交到仓库：[commit]
git commit -m "第一次提交"

[master (root-commit) fbe2e27] 第一次提交
1 file changed, 1 insertion(+)        
create mode 100644 readme.txt


修改文件 readme.txt M

git status命令 查看仓库状态
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

git add .
git status
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.txt

git status
nothing to commit, working tree clean

你好

git diff 文件版本对比

git log 命令查看版本记录
(HEAD -> master) 当前版本
上一个版本就是HEAD^，上上一个版本就是HEAD^^ 所以写成HEAD~100
ac87f1a6161fdd9739dde4f71d320fadca186790 版本ID

ac87f1a6161fdd9739dde4f71d320fadca186790 (HEAD -> master) 修正了发音
dc459ab2311baae047ad0bcaeb950e9b068b23dd 第四次提交      
28af86ff0af4617b25a8f9a189e7b625e6e5027e 第三次提交      
5c1a16ab3ef717f339230b224f01446107df0f01 新增了测试文件  
fbe2e27a5e4cb67a4c974ab6f49901b125ebd6f2 第一次提交
git log --pretty=oneline

历史版本回退
git reset --hard HEAD^
git reset --hard 28af86ff

前进到未来版本
git reset --hard ac87f1a61

git reflog 查看所有操作记录
git reset --hard ac87f1a
```

工作区和暂存区 仓库

工作区 编辑里面的文件夹和文件
暂存索引区 临时存储
仓库区 入库保存

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

# 撤销更改
## 用仓库最新版替换工作区
git reset --hard HEAD

## 撤销工作区修改 用暂存区替换工作区
## 还没有暂存的状态
git restore <file>...

## 撤销暂存区修改 工作区不变
git restore --staged <file>...
## 撤销工作区
git restore <file>...


# 删除操作
撤销工作区删除/修改
git restore <file>...

确定要删除
git add/rm <file>...


<!-- 基本 -->
git init
git add 
git commit

git status
git diff

git log
git reflog
git reset --hard



Git仓库托管服务Github

默认模式 本地Git仓库和GitHub仓库之间的传输是通过SSH加密

第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

$ ssh-keygen -t rsa -C "youremail@example.com"


id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人

第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：


```
…or create a new repository on the command line
echo "# learn-git" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:FindIndex/learn-git.git
git push -u origin master
                
…or push an existing repository from the command line
# 添加远程仓库 origin这个远程仓库的名字 FindIndex用户名  learn-git仓库名
git remote add origin git@github.com:FindIndex/learn-git.git
# 推送到远程仓库master分支
git push -u origin master
# 删除远程仓库配置
git remote remove <name>

# 从远程仓库拉到本地 更新
$ git pull
$ git pull origin

# 从远程仓库克隆整个仓库 初始化


…or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.
```