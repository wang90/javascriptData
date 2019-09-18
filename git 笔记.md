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


# code review 的缩略词语！  
*PR*: Pull Request. 拉取请求，给其他项目提交代码   
*LGTM*: Looks Good To Me. 朕知道了 代码已经过 review，可以合并   
*SGTM*: Sounds Good To Me. 和上面那句意思差不多，也是已经通过了 review 的意思    
*WIP*: Work In Progress. 传说中提 PR 的最佳实践是，如果你有个改动很大的 PR，可以在写了一部分的情况下先提交，但是在标题里写上 WIP，以告诉项目维护者这个功能还未完成，方便维护者提前 review 部分提交的代码。   
*PTAL*: Please Take A Look. 你来瞅瞅？用来提示别人来看一下   
*TBR*: To Be Reviewed. 提示维护者进行 review   
*TL;DR*: Too Long; Didn't Read. 太长懒得看。也有很多文档在做简略描述之前会写这么一句   
*TBD*: To Be Done(or Defined/Discussed/Decided/Determined). 根据语境不同意义有所区别，但一般都是还没搞定的意思   
