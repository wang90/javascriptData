# 常用css代码块
### 禁止页面选中
````
    -moz-user-select: none; /*火狐*/
    -webkit-user-select: none;  /*webkit浏览器*/
    -ms-user-select: none;   /*IE10*/
    -khtml-user-select: none; /*早期浏览器*/
    user-select: none;
````
### 单行变成...
````
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
````
### 多行...
`````
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;（行数）
    -webkit-box-orient: vertical;
`````
### 手机端1像素问题   
````
  var viewport = document.querySelector("meta[name=viewport]");
  //下面是根据设备像素设置viewport
  if (window.devicePixelRatio == 1) {
    viewport.setAttribute('content', 'width=device-width,initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no');
  }
  if (window.devicePixelRatio == 2) {
     viewport.setAttribute('content', 'width=device-width,initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no');
  }
  if (window.devicePixelRatio == 3) {
     viewport.setAttribute('content', 'width=device-width,initial-scale=0.3333333333333333, maximum-scale=0.3333333333333333, minimum-scale=0.3333333333333333, user-scalable=no');
            }
  var docEl = document.documentElement;
  var fontsize = 10 * (docEl.clientWidth / 320) + 'px';
  docEl.style.fontSize = fontsize;
````
### 网站灰色css属性
``````
<style>
        <!--
          html {
            filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
            -webkit-filter: grayscale(100%);}
        -->
</style>
``````
### 常用背景阴影
``````
box-shadow: 0 0 6px 0 rgba(0,0,0,.1);
``````
