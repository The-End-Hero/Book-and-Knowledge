git add .      //添加所有改动代码

git commit -m “这是说明”   //commit代码说明

git push 		//提交代码

git branch      //查看本地分支

git branch -r //列出所有远程分支名称

git checkout -b 本地分支名称 origin/远程分支名称//拉取远程分支到本地并且新建分支

git status       //查看修改的代码

git clone 地址  //克隆项目

git status       //查看修改了什么文件

git pull  xxxxxx  //拉取远程分支代码并且合并-->相当于fetch+merge

git checkout -b xxxxx  //基于当前分支，创建xxxxx分支，并且切换到xxxxx分支上去

git stash       //隐藏需要commit的内容

git stash pop   //释放这些隐藏   

git stash list  //显示被隐藏的内容

git checkout xxxxxx（git status 出来的项目）//去掉这部分提交

git branch -d xxxxx 删除xxxxx分支

git branch -D xxxxx 强制删除xxxxx分支

cherry-pick 将其他分支已经commit过的头 加在当前分支上