### 修改npm配置
``````
npm config set prefix "nodeJs的安装目录"
``````
#### 重新安装需要的全局包
``````
npm install "包名" -g
``````
### fix npm install --save '' error
``````
npm ERR! Object for dependency "make-dir" is empty.
npm ERR! Something went wrong. Regenerate the package-lock.json with "npm install".
npm ERR! If using a shrinkwrap, regenerate with "npm shrinkwrap".
``````
原因npm install 不自动生成 package-lock.json文件
可能是因为npm版本6.14.7无法自动生成package-lock.json
解决办法
``````
npm config set package-lock false
``````
### 发布一个包
``````
npm publish
``````
