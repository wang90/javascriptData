# nvm 使用手册

### 下载 nvm
```````
brew install nvm
brew link nvm 
```````
### 下载最新版node
```````
nvm install node 
```````
### 下载特定版本
```````
nvm ls 
nvm install v12.18.2
```````
### 切换不同版本
``````
nvm use 12.18.2
nvm use default
nvm use node
``````
### nvm use node 失败
```````
nvm is not compatible with the npm config "prefix" option: currently set to "/usr/local/Cellar/nvm/0.27.1/versions/node/v4.1.1"
Run `nvm use --delete-prefix v14.5.0 --silent` to unset it
```````
``````
nvm use node
nvm use --delete-prefix v14.5.0
``````
### 每次终端启动nvm 解决
每次启动nvm后会显示下面的话
```````
nvm is not compatible with the npm config "prefix" option: currently set to "/usr/local" 
Run `npm config delete prefix` or `nvm use --delete-prefix v14.5.0 --silent` to unset it.
```````
解决方案
``````
nvm use --delete-prefix v14.5.0 --silent // 确保npm命令可以使用
npm config delete prefix // 删除 nvm prefix；
npm config set prefix $NVM_DIR/versions/node/v14.5.0  // 设置 nvm prefix 为v14.5.0 
``````
