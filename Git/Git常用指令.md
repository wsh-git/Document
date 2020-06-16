# 初次使用时，每次提交远程仓库都会出现使用凭证的问题

## 1、在工程目录中找到.git文件夹（有可能是隐藏状态）

## 2、找到config文件

[remote "origin"]
        url = https://github.com/wsh-git/Document.git

改为:
	url = https://用户名:密码@github.com/wsh-git/Document.git（github的账号信息）限于个人仓库使用

## 3、保存之后就可以直接提交到远程仓库了