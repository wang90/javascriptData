# vue 创建项目相关内容

## vue-cli创建
##### 下载vue-cli
``````
npm install vue-cli
``````
##### vue-cli3创建项目
``````
vue create app
cd app 
npm install 
npm run dev
npm run-script build 
``````

## 加入less
##### 下载less
``````
npm i style-resources-loader vue-cli-plugin-style-resources-loader -D
npm install --save -dev less-loader
``````
##### vue.config.js添加内容
``````
pluginOptions: {
      'style-resources-loader': {
        preProcessor: 'less',
        patterns: [path.resolve(__dirname, "src/common/less/variable.less")] // 引入全局样式变量
      }
}
``````

## 修改路径
##### vue.config.js修改路径路径
``````
outputDir: 'dist', // 输出文件路径
indexPath:"../index.html", // 输出index路径
publicPath:"./dist/", // 设置 index相对路径
``````
## 将px转化成rem

##### 下载postcss-pxtorem
```````
npm install postcss-pxtorem -D
```````
##### 创建文件postcss.config.js
```````
module.exports = {
  plugins: {
    'autoprefixer': {
      browsers: ['Android >= 4.0', 'iOS >= 7']
    },
    'postcss-pxtorem': {
      rootValue: 16,//结果为：设计稿元素尺寸/16，比如元素宽320px,最终页面会换算成 20rem
      propList: ['*']
    }
  }
}
```````
##### 创建rem.js
```````
// 设置 rem 函数
function setRem () {
    // 320 默认大小16px; 320px = 20rem ;每个元素px基础上/16
      let htmlWidth = document.documentElement.clientWidth || document.body.clientWidth;
    //得到html的Dom元素
      let htmlDom = document.getElementsByTagName('html')[0];
    //设置根元素字体大小
    htmlDom.style.fontSize= htmlWidth/20 + 'px';
}
// 初始化
setRem();
// 改变窗口大小时重新设置 rem
window.onresize = function () {
    setRem()
}
```````
##### 在main.js中引入rem.js
```````
import './libs/rem.js';
```````
   

