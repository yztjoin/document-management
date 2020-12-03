```
git init 
初始化git生成git仓库

git add <filename> 
添加文件到提交树上

git commit -m 
“提交内容的注释”

git status 
查看文件状态  修改 add  还是commit

git log 
查看历史记录 显示git的所有版本

git log --pretty=oneline 
简化log的显示

git reset --hard HEAD^/HEAD^^ 
版本回退，一个^代表回退一个版本，在windows上面的doc框内需要使用双引号括住HEAD，
若想要回退到指定版本可以使用log里面的commitID放在HEAD后面可以直接回退

git reset HEAD -- <file>
该操作 可以 拉取最近一次提交到版本库的文件到暂存区 并且该操作不影响工作区

git reflog 
用于查看所有你操作过的命令

git checkout -- <fileName> 
可以丢弃工作区的修改回退到最近的修改
命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

git rm <fileName> 
删除文件

git checkout -b dev == git branch dev + git checkout dev
创建一个名叫dev的分支并且切换到此分支

git checkout <name>
切换分支

git merge <name>
合并分支

git branch
查看所有分支和当前在哪一个分支

git switch -v dev == git checkout -b dev
因为git checkout 和 git checkout -- fileName相似并且切换分支使用switch更合适

git branch -d <name>
删除分支

git log --graph --pretty=oneline --abbrev-commit
合并分支简要图

git log --graph // 退出需要英文状态下按Q
合并分支图

git merge --no-ff -m "merge with no-ff" dev // --no--ff 标识禁用fast forward模式
此模式在删除分支后会丢掉分支信息

git stash 
储存当前的工作缓存区，工作现场

git stash list
查看工作现场

git stash pop
恢复现场，加载之前的缓存

git branch -D <name>
强行删除该分支

git remote
查看远程仓库信息

git remote -v
查看更详细的远程仓库信息

git push origin master
推送master分支到远程仓库

git checkout -b dev origin/dev
创建远程origin的dev分支到本地

git pull 
抓取最新提交的git仓库

git branch --set-upstream-to <branch-name> origin/<branch-name>
git branch --set-upstream-to=origin/dev dev   
设置dev和origin/dev的链接

git rebase
把原本分叉的提交改变为一条直线

git tag <标签>
给当前分支打上标签

git tag -a <标签> -m <说明> <commitID>
git tag -a v0.1 -m "version 0.1 released" 1094adb
在git show <标签>可以看到说明文字

git config --global color.ui true
让git提示显示颜色

git tag 
查看当前分支

git tag <标签> <commitId>
给指定id打上标签

git show <标签>
git show v0.9
查看标签的详细信息


```

