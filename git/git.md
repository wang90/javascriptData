# 工作中git使用笔记

### 同步代码
``````
git status
git stash //保存当前工作进度
git fetch origin
git rebase origin/master
git status
git stash pop //恢复最新的进度到工作区
git status
git commit --amend追加提交
``````
### git rebase 的优点   
`````
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
```````

### git修改分支名字 
``````
git branch -m oldbranchname newbranchname    
``````

### diff
显示当前工作空间和提交的不同
``````
# 显示工作目录和索引的不同
git diff

# 显示索引和最近一次提交的不同
git diff --cached

# 显示工作目录和最近一次提交的不同
git diff HEAD
``````

### code review 的缩略词语！  

```````
# 开发中
PR: Pull Request. 拉取请求，给其他项目提交代码  
WIP   Work in progress, do not merge yet.  传说中提 PR 的最佳实践是，如果你有个改动很大的 PR，可以在写了一部分的情况下先提交，但是在标题里写上 WIP，以告诉项目维护者这个功能还未完成，方便维护者提前 review 部分提交的代码。
# Riview 完别人的 PR ，没有问题 ;
# 朕知道了 代码已经过 review，可以合并  
LGTM Looks good to me. 
SGTM: Sounds Good To Me. 和上面那句意思差不多，也是已经通过了 review 的意思 
# 帮我看下，一般都是请别人 review 自己的 PR
PTAL Please take a look. Please Take A Look. 你来瞅瞅？用来提示别人来看一下 
# 一般代表抄送别人的意思
CC Carbon copy 
#TBR: To Be Reviewed. 提示维护者进行 review  
# 我觉得这个想法很好, 我们来一起讨论下
RFC  —  request for comments. 
# 如果我没记错
IIRC  —  if I recall correctly. 
# 我确认了或者我接受了,我承认了
ACK  —  acknowledgement.
# 我不同意
NACK/NAK — negative acknowledgement.
# TL;DR: Too Long; Didn't Read. 太长懒得看。也有很多文档在做简略描述之前会写这么一句 
# TBD: To Be Done(or Defined/Discussed/Decided/Determined). 根据语境不同意义有所区别，但一般都是还没搞定的意思
```````

### git如何清除本地remotes/origin/*分支
``````
git branch -a
git remote prune origin
``````

### 远程覆盖本地
```````
git fetch --all
git reset --hard origin/master 
git pull
```````
### 强制覆盖远程分支
```````
#git push origin 分支名 --force
git push origin master --force
```````

### 修改 github 项目语言
```
// vi .gitattributes
*.js linguist-language=python
*.css linguist-language=python
*.html linguist-language=python
// :wq
```
### 查看 git config
```````
git config --global  --list
```````

### 工作中不想提交，但是需要保存的方法
##### 保存到待存取
````````
git stash save 'push to stash area'
````````
##### 查看暂存区
````````
git stash list
````````
##### 获取暂存区内容
````````
# 获取
git stash apply stash@{0}
# 删除
git stash drop stash@{0}
# or
stash pop
````````

### 打标签
``````
git tag v1.0 e39d0b2
git checkout v1.0
``````

### 查看远程映射
``````
git remote -v
``````
### 拒绝合并无关历史
``````
# 当git pull origin master 时就出现了这样一条错误：
fatal: refusing to merge unrelated histories  // 拒绝合并无关历史
## 解决
git pull origin master --allow-unrelated-histories 
``````
### 新建分支并切换
``````
git checkout -b iss53
Switched to a new branch "iss53"
``````

###  type（必须） : commit 的类别，只允许使用下面几个标识：
```````
feat : 新功能
fix : 修复bug
docs : 文档改变
style : 代码格式改变
refactor : 某个已有功能重构
perf : 性能优化
test : 增加测试
build : 改变了build工具 如 grunt换成了 npm
revert : 撤销上一次的 commit
chore : 构建过程或辅助工具的变动
```````
### github 仓库搜索
``````
search xxx-awesome
``````


