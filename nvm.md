#### 下载 nvm
```````
brew install nvm
brew link nvm 
```````
#### 下载最新版node
```````
nvm install node 
```````
#### 下载特定版本
```````
nvm ls 
nvm install v12.18.2
```````
#### 切换不同版本
``````
nvm use 12.18.2
nvm use default
nvm use node
``````
#### nvm use node 失败
```````
nvm is not compatible with the npm config "prefix" option: currently set to "/usr/local/Cellar/nvm/0.27.1/versions/node/v4.1.1"
Run `nvm use --delete-prefix v14.5.0 --silent` to unset it
```````
``````
nvm use node
nvm use --delete-prefix v14.5.0
``````
