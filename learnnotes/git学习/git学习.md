###创建ssh key
测试本地库和远程库连接`ssh -T git@github.com`

1. 首先看用户主目录下是否有.ssh目录，再看看目录下是否有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
`$ ssh-keygen -t rsa -C "你的邮箱地址"`
2. 登陆GitHub，打开“Account settings”，“SSH Keys”页面：然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

###git创建本地库
1. 创建文件
2. 用命令`git add`告诉git，把文件修改添加到本地库的暂存区,如：`git add readme.txt`
3. 用命令`git commit`告诉git，把文件提交到当前分支:`git commit -m "wrote a readme file"`(-m表示本次提交的说明,引号里的内容)

###把本地库与github上的仓库相关联，再把本地仓库内容推送到github仓库中
1. 首先进入已修改的文件的目录，然后将文件加入暂存区，执行`$ git add 文件名`,若一次add多个文件，可使用`git add --all`
2. 用命令git commit告诉git，把文件提交到当前分支:`git commit -m "wrote a readme file"`(-m表示本次提交的说明,引号里的内容)
3. `$ git remote add origin git@github.com:nanfengchuiyeluo6/你的仓库名.git`
4. 然后推送：`$ git push -u origin master`

###将github仓库克隆到本地
`$ git clone git@github.com:nanfengchuiyeluo6/仓库名.git`

**改变克隆本地库路径**
&emsp; 进入到要要修改到的路径，如f盘某处，然后使用`git init`

###fatal: remote origin already exists.
&emsp; 先删除remote `$ git remote rm origin`

###同步本地仓库与远程仓库文件
`git pull --rebase origin master`

###git push出错出现git pull...的错误
`git fetch`
`git rebase`
`git push origin master`

###分支管理
`git checkout -b dev`代表创建并切换到当前dev分支
`get branch`可以显示所有分支，当前分支前会有*号
分支工作完成后，切换回master分支：
`git checkout master`
将dev工作成果合并到master中分支上：
`git merge dev`
合并完成后删除分支：
`git branch -d dev`


###git修改默认端口
首先在.ssh文件夹中新建config文件
然后写下：
```
Host github.com
HostName ssh.github.com
User 1378379779@qq.com
PreferredAuthentications publickey  
IdentityFile ~/.ssh/id_rsa  
Port 443
```