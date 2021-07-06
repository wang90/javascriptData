## Tmux

### 查看会话
`````
tmux ls
`````
### 新建会话
`````
tmux new -s <session-name>
# session-name 不填写则为 0,1,2,4
`````
### 进入会话
`````
tmux attach -t 0
tmux attach -t <session-name>
`````
### 杀死会话
`````
tmux kill-session 0
tmux kill-session <session-name>
`````
### 重命名会话
`````
tmux rename-session -t 0 <new-name>
`````
### 窗口划分
`````
tmux split-window
tmux split-window -h
`````
### 新建窗口
`````
tmux new-window
tmux new-window -n <window-name>
`````
### 重命名窗口
``````
 tmux rename-window <new-name>
``````
