

# git操作指令

## 操作用户名、邮箱

### 全局

#### 设置

git config --global user.name xxx

git config --global user.email xxx.xxx.@xx.com

#### 查看

git config --global user.name

git config --global user.email

git config --global --list

### 当前仓库

#### 设置

git config user.name xxx（or --global -> --local）

git config user.email xxx.xxx.@xx.com

#### 查看

git config user.name

git config user.email

git config --list

### Tips:

本地仓库的配置文件在.git/config



## 仓库初始化

git init（生成.git文件夹，默认是隐藏状态）



## 添加文件到暂存区

git add filename

git add filename01 filename02 ...

git add . 添加当前文件夹

git add -A 添加当前所有修改文件



## 查看本地修改不同

### 未添加到暂存区

git diff filename

git diff 查看当前所有文件修改的变动

### 已添加到暂存区

git diff filename --staged



## 提交到仓库

git commit -m "提交的message"



## 提交仓库Message

### header  --> type(scope):subject

#### type常用类型

feat:新功能

fix:修复bug

style:格式

refactor:代码重构

chore:项目构建



## 查看日志

git log

git log --pretty=oneline 单行显示日志（可以查看的更多）

退出按键q



## 回退操作

git reset --hard 提交的历史版本号（通过git log 命令查看版本号）



## 对已经push远程的文件进行回滚

git revert 版本号



## 对未添加到暂存区的文件进行撤销

git checkout -- filename

git checkout -- . (后面加一个. 就是对当前所有文件进行撤销操作)



## 对已经添加到暂存区的文件撤销到未添加到暂存区的状态

git reset HEAD filename(回到未添加到暂存区的状态，如果想继续撤销就可以用git checkout -- filename)

git reset HEAD (把当前所有已经添加到暂存区的文件全部一次性回退到之前的状态)



##  查看历史操作指令

git reflog



## 查看分支

git branch 查看本地当前的分支

git brach -a 查看所有的分支



## 创建分支

git branch 分支名称



## 切换分支

git checkout 分支名称



## 创建新的分支，同时切换到新的分支上

git checkout -b 分支名称

：switched to a new branch 'branchname'



## 删除分支

git branch -d 分支名称



## 合并分支

git merge 被合并的分支



# 初次使用时，每次提交远程仓库都会出现使用凭证的问题

## 1、在工程目录中找到.git文件夹（有可能是隐藏状态）

## 2、找到config文件

[remote "origin"]
        url = https://github.com/wsh-git/Document.git

改为:
	url = https://用户名:密码@github.com/wsh-git/Document.git（github的账号信息）限于个人仓库使用

## 3、保存之后就可以直接提交到远程仓库了

