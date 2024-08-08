# 1.Git工作区，暂存区和版本库

![image-20240801154107958](C:\Users\LZH\AppData\Roaming\Typora\typora-user-images\image-20240801154107958.png)

# 2.git add添加到暂存区

```shell
#将index.txt文本放到暂存区
git add index.txt
#把文件夹下的ceshi文件夹放在暂存区(暂存区不能存放空文件夹)
git add ceshi/
#把文件夹下所有的内容都放在暂存区
git add --all（或者git add .）
```

# 3.git commit提交到历史区

```shell
#把暂存区的内容放到历史区
git commit -m"我是第一个版本"
```

##### 我们使用git log这个指令查看版本信息

```shell
#查看当前历史区版本信息
git log
```

# 4.历史版本回退

### 1.git reset --hard HEAD^(返回版本到工作区)

```shell
#回退到上一次提交的版本
git reset --hard HEAD^
井
#回退到上上次提交的版本
git reset --hard HEAD^^
git reset --hard HEAD~2
```

##### 版本前进的方法

```shell
git reflog (查看操作记录)
#注意：git log是查看hard->head指针前面的版本的提交信息，git reflog查看的是所有操作信息
git reset --hard 版本号
```

### 2.git reset --soft HEAD^(版本回退到暂存区)

- ##### 作用一修改提交信息

- ##### 作用二结合git add .修改bug后的提交信息

### 3.git revert 与 git reset

![image-20240801165242646](C:\Users\LZH\AppData\Roaming\Typora\typora-user-images\image-20240801165242646.png)

# 5.git分支

### 1.认识分支

- git分支，就是我们自己把我们的整个文件夹分成一个一个独立的区域
- 比如我在开发**登录**功能的时候，可以放在login分支下进行开发
  - 开发列表功能的时候，可以放在list分支下进行开发
  - 大家互不干扰，每一个功能都是一个独立的功能分支
*-
- git在初始化的时候，会自动生成一个分支，叫做master
- 是表示主要分支的意思
- 我们就可以自己开辟出很多独立分支

### 2.创建分支

- 开辟一个分支使用git branch分支名称指令

  ```shell
  #开辟一个1ogin分支
  git branch login
  ```

- 查看当前分支情况

  ```shell
  git branch
  ```

  - 会看到，当前有两个分支了
  - 一个是master,一个是login
  - 前面有个*号，并且有高亮显示的，表示你当前所处的分支

### 3.切换分支

- 我们对登录功能的开发要移动到login分支去完成

- 我们切换所处分支使用git checkout 分支名称

  ```shell
  #切换到1ogin分支
  git checkout login
  ```

- 然后我们在整个分支上进行登录功能的开发
- 开发完毕以后，我们就在当前分支上进行提交
- 提交以后我们进行分支切换
  - 发现master上面还是最初始的状态
  - 而login分支上有我们新写的登录功能的代码

### 4.合并分支

- git的合并分支，只能是把别的分支的内容合并到自己的分支上

- 使用的指令是git merge

  ```shell
  #切换到master分支
  git checkout master
  #把1ogin的内容合并到自己的分支
  git merge login
  ```

### 5.删除分支

- 这个时候我们开辟的分支就没有什么用了，就可以删除分支了

  1. 先切换到别的分支

  2. 使用指令`git branch -d 分支名`来删除

     ```shell
     #先切换到别的分支
     git checkout master
     #删除login分支
     git branch -d login
     ```

# 6.分支合并冲突

- 当分支合并时与主分支冲突时，需要手动修改主分支的代码决定保留的代码部分，然后在进行：

  ```shell
  git add .
  git commit -m "解决冲突"
  #切换到其他分支
  git checkout 分支名
  ```

# 7.git远程仓库拉取，推送

### 1.添加仓库地址

- 使用`git remote add origin`仓库地址来添加

  ```shell
  #添加仓库地址（orign是仓库地址的别名）
  git remote add origin 仓库地址
  ```

  - remote：远程的意思
  - add：添加的意思
  - origin：是一个变量名（仓库地址）

### 2.git push推送

- 使用`git pus`h指令上传

  ```shell
  #上传内容
  git push origin master  或者 git push -u origin master
  #表示把内容上传到origin这个地址
  #git push origin master:master 的缩写第一个master是本地的master分支，第二个是远程的master分支
  ```

  - 如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何
    参数使用git push。
  - 使用git push -u origin master 之后就可以使用`git push`上传
  - 除非需要传递到别的分支上

- 完成了git推送就可以删除本地文件了

### 3.git clone克隆

- `git`克隆是指把远程仓库里面的内容克隆一份到本地
- 可以克隆别人的**公开**的仓库，也可以克隆自己的仓库
- 克隆别人的仓库，我们只能拿下来用，修改后不能从新上传
- 克隆自己的仓库，我们修改后还可以再次上传更新



- 输入克隆指令`git clone 仓库地址`

  ```shell
  #直接克隆仓库
  git clone 仓库地址
  ```

### 4.git pull拉取

- 当人家的代码更新以后，你想获得最新的代码

- 我们不需要从新克隆

- 只要拉取一次代码就可以了

- 直接在项目文件夹里面使用指令下拉

  ```shell
  #拉取远程最新代码
  git pull -u origin master
  ```

- 这样一来，你本地的仓库就可远程的仓库同步了

### 5.删除远程分支

```shell
#删除远程分支
git push origin :login
```

# 8.ignore文件（待更新）

