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

git checkout   <branchname >    # 切换分支
git checkout -b <branchname >  # 创建并切换到新分支
git switch <branch-name >       # 切换分支
git branch                  # 查看分支
git branch  <branchname >   #     创建分支
git branch -d <branchname >  # 删除分支
git merge <branchname >     # 合并分支
git rebase <branchname >     # 变基合并分支

git clone git@github.com:用户名/仓库名.git  #克隆远程仓库到本地
git remote add origin git@github.com:用户名/仓库名.git  #添加远程仓库

git config --global -l  #查看全局配置
git config --global user.name "用户名"  #设置用户名
git config --global user.email "邮箱"  #设置邮箱
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890

git config --global --unset http.proxy   #取消全局代理
git config --global --unset https.proxy   #取消全局代理
````

###    项目有关命令：
``` shell
git clone <项目地址>  #克隆项目到本地
git remote add origin <项目地址>  #添加远程仓库
git push -u origin master  #推送本地仓库到远程仓库
git branch -a  #查看所有分支
git branch -r  #查看远程分支
git branch -m <old_name> <new_name>  #重命名分支
git branch -D <branch_name>  #删除分支
git checkout -b <branch_name>  #创建并切换到新分支
git merge <branch_name>  #合并分支
git rebase <branch_name>  #变基合并分支
git stash  #暂存当前工作区
git stash list  #查看暂存区列表
git stash pop  #恢复暂存区文件
git stash drop  #删除暂存区文件
git remote -v  #查看远程仓库地址
git remote show origin  #查看远程仓库详细信息
git remote rename origin old_name  #重命名远程仓库
git remote remove origin  #删除远程仓库
git fetch origin  #从远程仓库获取更新
git pull origin master  #从远程仓库获取更新并合并到本地仓库
git push origin <branch_name>  #推送本地分支到远程仓库
git push origin --delete <branch_name>  #删除远程分支
git tag  #查看所有标签
git tag -a v1.0 -m "版本1.0"  #创建标签
git show v1.0  #查看标签信息
git push origin v1.0  #推送标签到远程仓库
git checkout v1.0  #切换到指定标签



git restore src/components/Pagination.vue   #恢复文件

git restore --staged src/components/Pagination.vue   #取消暂存

git reset --hard HEAD^      # 回退到上一个版本
git reset --hard commit-id  # 回退到指定版本
# 显示每个文件的差异
$files = git diff --name-only
foreach ($file in $files) {
    Write-Output "Diff for $file"
    git diff $file
    Read-Host -Prompt "Press Enter to continue to the next file"
}  

```
