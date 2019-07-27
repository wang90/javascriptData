react-app脚手架  
``````
npm install -g create-react-app   
create-react-app xxx 
npm start 启动
``````
 
react-app没有webpack问题：    
``````
npm run eject    
``````
如果报错：
``````
Remove untracked files, stash or commit any changes, and try again.
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! caiyun_push@0.1.0 eject: `react-scripts eject`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the caiyun_push@0.1.0 eject script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/wang90/.npm/_logs/2019-07-27T06_35_39_275Z-debug.log     
``````
属于没有提交任何内容，需要     
``````
git add .     
git commit -m 'Saving before ejecting'     
npm run eject     
```````
在成功后最好执行下
``````
rm -rf node_modules
rm package-lock.json
$npm install
``````
  
react 使用ant     
  https://ant.design/docs/react/introduce-cn
``````
npm install antd --save
``````
如果想使用ant中的less    
 引入antd中less    
 ``````
 @import '~antd/dist/antd.less';
 @impotr 'xxx.less';
 ``````
 下载less  less-loader     
 ``````
 npm install less less-loader --save-dev
 ``````
 修改webpack.config.js中      
 第42行     
 ``````
 const lessRegex = /\.(less)$/;
 const lessModuleRegex = /\.module\.(less)$/;  
 ``````
 456行
 ``````
  {
    test: lessRegex,
    exclude: lessModuleRegex,
    use: getStyleLoaders({ importLoaders: 3 }, 'less-loader'),          
   },
   {
     test: lessModuleRegex,
     use: getStyleLoaders(
          {
             importLoaders: 3,
             modules: true,
             getLocalIdent: getCSSModuleLocalIdent,
             modifyVars:{
                'primary-color': '#1DA57A',
                'link-color': '#1DA57A',  
                 'border-radius-base': '2px',
             },
             javascriptEnabled: true,
           },
           'less-loader'
          ),
    },
 ``````
 下载babel-plugin
 ``````
 npm install babel-plugin-import --save-dev
 ``````
 在package.json中babel添加
 ``````
  "plugins": [
      [
        "import",
        {
          "libraryName": "antd",
          "style": true
        }
      ]
    ]
 ``````
 此时npm start 如果如下报错
 ``````
 ./node_modules/antd/lib/grid/style/index.less (./node_modules/css-loader/dist/cjs.js??ref--6-oneOf-7-1!./node_modules/postcss-loader/src??postcss!./node_modules/less-loader/dist/cjs.js??ref--6-oneOf-7-3!./node_modules/antd/lib/grid/style/index.less)

// https://github.com/ant-design/ant-motion/issues/44
.bezierEasingMixin();
 ``````
 请修改less版本号，因为只能使用<3.0.0
 ``````
 npm install less@^2.7.3
 ``````
