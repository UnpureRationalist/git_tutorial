# Git基础

## 1.初始设置

#### 设置姓名和邮箱地址

```shell
$ git config --global user.name "userName"
$ git config --global user.email "userName@xxx.xxx"
```

#### 提高命令输出可读性

```shell
$ git config --global color.ui auto
```

#### 创建 SSH Key

```shell
$ ssh-keygen -t rsa -C "userName@xxx.xxx"
```

#### 在 GitHub 添加公开密钥

```shell
$ cat ~/.ssh/id_rsa.pub   # 显示公开密钥，在 GitHub 页面输入即可
```

## 2.使用示例

#### clone 仓库

```shell
$ git clone ...
```

#### 查看状态

```shell
$ git status
```

#### 提交

```shell
$ git add yourFileName		# 将文件加入暂存区
$ git commit -m "Message"	# 提交
$ git push					# push
```

查看提交日志

```shell
$ git log
```

![image-20210227235400993](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210227235400993.png)

## 3. 基本操作

#### 初始化仓库

```shell
$ git init		# 生成 .git 文件夹，称之为“附属于该仓库的工作树”
```

#### 查看仓库状态

```shell
$ git status
```

#### 向暂存区添加文件

```shell
$ git add README.md
```

#### 保存仓库的历史记录

```shell
$ git commit -m "First commit"		# 记录一行提交信息
```

  

```shell
$ git commit 						# 记录详细提交信息
```

#### 查看提交日志

```shell
$ git log
$ git log --pretty=short			# 只显示提交信息的第一行
$ git log fileName/DirName			# 只显示指定文件、文件夹的日志
$ git log -p						# 显示文件的改动
$ git log -p fileName				# 只显示指定文件提交日志和提交前后差别
```

#### 查看更改前后的差别

```shell
$ git diff
```

#### 查看工作树和最新提交的差别

```shell
$ git diff HEAD
```

## 4. 分支的操作

#### 显示分支一览表

```shell
$ git branch
```

#### 创建、切换分支

```shell
$ git checkout -b newBranchName		# 创建新分支 newBranchName 并切换， 相当于下面两条命令

$ git branch newBranchName			# 创建新分支
$ git checkout newBranchName		# 切换分支
```

#### 切换回上一个分支

```shell
$ git checkout -
```

#### 合并分支

```shell
$ git merge --no-ff newBranchName	# 合并分支，执行此命令会弹出 vim 窗口，输入“ZZ”退出
```

#### 以图表形式查看分支

```shell
$ git log --graph
```

## 5. 更改提交的操作

#### 回溯历史版本

```shell
$ git reset --hard 42810318e5cbbae39739cae41cc872eb12c5280c			# 最后字符串为目标时间节点的哈希值
```

#### 查看当前仓库操作日志

```shell
$ git log			# 只能查看以当前状态为重点的历史日志
$ git reflog		# 查看当前仓库操作日志 一般用于恢复原先状态
```

#### 修改上一条提交信息

```shell
$ git commit --amend		# 执行该命令后将启动 vim 编辑器
```

#### 压缩历史

```shell
$ git rebase -i HEAD~n		# n 为一个正整数，表示将最新 n 个开始记录合并。此操作将打开编辑器 vim
```

## 6. 推送至远程仓库

#### 添加至远程仓库

```shell
$ git remote add origin git@github.com:UnpureRationalist/git_tutorial.git		# origin 为标识符
```

#### 推送至远程仓库

```shell
$ git push -u origin master
```

## 7. 从远程仓库获取

#### 获取远程仓库

```shell
$ git clone git@github.com:UnpureRationalist/git_tutorial.git
```

#### 查看当前分支信息

```shell
$ git branch -a		# -a 参数同时显示本地仓库和远程仓库的分支信息
```

![image-20210228140737363](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210228140737363.png)

#### 获取远程的 feature-D 分支

```shell
$ git checkout -b feature-D origin/feature-D		# -b 参数的后面是本地仓库中新建分支的名称
# 上面指令指定了 origin/feature-D，就是说以名为 origin 的仓库（这里指 GitHub 端的仓库）的 feature-D 分支为来源，
# 在本地仓库中创建 feature-D 分支
```

#### 向本地的 feature-D 分支提交更改

```shell
$ git commit -am "Add feature-D"
```

####  推送 feature-D 分支

```shell
$ git push
```

#### 获取最新的远程仓库分支

```shell
$ git pull origin feature-D
```

## 8. 在线学习资料

- [Pro Git](http://git-scm.com/book/zh/v2)

- [LearnGitBranching](http://pcottle.github.io/learnGitBranching/)

- [tryGit](http://try.github.io/)

  

