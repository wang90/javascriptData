同步代码
``````
git status
git stash //保存当前工作进度
git fetch origin
git rebase origin/master
git status
git stash pop //恢复最新的进度到工作区
git status

``````

git commit --amend追加提交

git rebase 的优点    
1.合并 commit 记录，保持分支整洁；   
2.相比 merge 来说会减少分支合并的记录；   
合并commit步骤
1）git log 查看提交内容    
git log --oneline 可以一行展现
2）git rebase -i
git rebase -i HEAD~3 修改前三个
3）进入到一个可编辑页面将p->s
pick：保留该commit（缩写:p）  
reword：保留该commit，但我需要修改该commit的注释（缩写:r）  
edit：保留该commit, 但我要停下来修改该提交(不仅仅修改注释)（缩写:e）  
squash：将该commit和前一个commit合并（缩写:s）  
fixup：将该commit和前一个commit合并，但我不要保留该提交的注释信息（缩写:f）  
exec：执行shell命令（缩写:x）  
drop：我要丢弃该commit（缩写:d）  
4）多余文件内的#注释掉
5）git rebase --abort撤销

git pull = git fetch + git merge   

git修改分支名字   
git branch -m oldbranchname newbranchname    
