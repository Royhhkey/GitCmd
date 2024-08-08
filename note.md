![alt text](QQ_1723082881283.png)
## 推送文件至远程

#### 1 建立本地仓库

-------
#### 2 与远程建立连接
``` shell
ssh -T git@github.com
```
#### 3 init命令初始化仓库
``` shell
git init
```
#### 4 add命令添加文件至暂存区
``` shell
git add < 文件名 >
git add 文件夹1/ 文件夹2/ ……多个文件夹之间空格隔开
git add .
```
#### 5 commit命令添加文件从暂存区至本地仓库
``` shell
git commit -m “注释”
```
#### 5 push命令本地仓库到github
``` shell
git push -u origin master
```
常用命令：
====
``` shell
git init                  # 初始化本地仓库
git add .                 # 添加所有文件至暂存区 
git add filename          # 添加单个文件至暂存区
git commit -m "注释"         #提交文件至本地仓库


git push origin main        #推送本地仓库到远程仓库
git push -u origin master    #推送本地仓库到远程仓库
git push origin main:remote_branch_name  #指定分支
git pull origin branch-name  #从远程仓库获取更新


git status                   # 查看哪些文件在暂存区中 
git log                    #  查看提交历史
git diff                   # 查看工作区和暂存区之间的差异


git checkout HEAD .        # 丢弃工作区的修改
git checkout HEAD <file >   # 丢弃暂存区和工作区的修改
git reset --hard HEAD^      # 回退到上一个版本
git reset --hard commit-id  # 回退到指定版本


git checkout -b <branchname >  # 创建并切换到新分支
git switch <branch-name >       # 切换分支
git branch                  # 查看分支
git branch  <branchname >   #     创建分支
git branch -d <branchname >  # 删除分支
git merge <branchname >     # 合并分支
git rebase <branchname >     # 变基合并分支

git clone git@github.com:用户名/仓库名.git  #克隆远程仓库到本地
git remote add origin git@github.com:用户名/仓库名.git  #添加远程仓库
````