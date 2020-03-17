
### 捕捉页面大小
````
function getViewport(){
　　　　if (document.compatMode == "BackCompat"){
　　　　　　return {
　　　　　　　　width: document.body.clientWidth,
　　　　　　　　height: document.body.clientHeight
　　　　　　}
　　　　} else {
　　　　　　return {
　　　　　　　　width: document.documentElement.clientWidth,
　　　　　　　　height: document.documentElement.clientHeight
　　　　　　}
　　　　}
　　}
````
### 捕捉滚动视觉页面大小
````
function getPagearea(){
　　　　if (document.compatMode == "BackCompat"){
　　　　　　return {
　　　　　　　　width: Math.max(document.body.scrollWidth,
　　　　　　　　　　　　　　　　document.body.clientWidth),
　　　　　　　　height: Math.max(document.body.scrollHeight,
　　　　　　　　　　　　　　　　document.body.clientHeight)
　　　　　　}
　　　　} else {
　　　　　　return {
　　　　　　　　width: Math.max(document.documentElement.scrollWidth,
　　　　　　　　　　　　　　　　document.documentElement.clientWidth),
　　　　　　　　height: Math.max(document.documentElement.scrollHeight,
　　　　　　　　　　　　　　　　document.documentElement.clientHeight)
　　　　　　}
　　　　}
　　}
````
### 获取元素绝对定位位置
````
function getElementLeft(element){
　　　　var actualLeft = element.offsetLeft;
　　　　var current = element.offsetParent;

　　　　while (current !== null){
　　　　　　actualLeft += current.offsetLeft;
　　　　　　current = current.offsetParent;
　　　　}

　　　　return actualLeft;
　　}

　　function getElementTop(element){
　　　　var actualTop = element.offsetTop;
　　　　var current = element.offsetParent;

　　　　while (current !== null){
　　　　　　actualTop += current.offsetTop;
　　　　　　current = current.offsetParent;
　　　　}

　　　　return actualTop;
　　}
````
### 获取元素相对位置
````
function getElementViewLeft(element){
　　　　var actualLeft = element.offsetLeft;
　　　　var current = element.offsetParent;

　　　　while (current !== null){
　　　　　　actualLeft += current.offsetLeft;
　　　　　　current = current.offsetParent;
　　　　}

　　　　if (document.compatMode == "BackCompat"){
　　　　　　var elementScrollLeft=document.body.scrollLeft;
　　　　} else {
　　　　　　var elementScrollLeft=document.documentElement.scrollLeft; 
　　　　}

　　　　return actualLeft-elementScrollLeft;
　　}
function getElementViewTop(element){
    var actualTop = element.offsetTop;
    var current = element.offsetParent;
    while (current !== null){
　　　　　　actualTop += current. offsetTop;
　　　　　　current = current.offsetParent;
　　 }

　　 if (document.compatMode == "BackCompat"){
　　　　　var elementScrollTop=document.body.scrollTop;
 　　} else {
　　　　　var elementScrollTop=document.documentElement.scrollTop; 
    }
    return actualTop-elementScrollTop;
}
````
### 快速排序
````
var quickSort = function(arr) {

　　if (arr.length <= 1) { return arr; }

　　var pivotIndex = Math.floor(arr.length / 2);

　　var pivot = arr.splice(pivotIndex, 1)[0];

　　var left = [];

　　var right = [];

　　for (var i = 0; i < arr.length; i++){

　　　　if (arr[i] < pivot) {

　　　　　　left.push(arr[i]);

　　　　} else {

　　　　　　right.push(arr[i]);

　　　　}

　　}

　　return quickSort(left).concat([pivot], quickSort(right));

};
````    
### 滚动到底部   
````
    var height = window.innerHeight;
    var page = 1
    $(window).on('scroll',function(){
        if(scrollTop() + (windowHeight()==0?height:windowHeight()) >= documentHeight()){
            page ++ ;
        };
    });
    function scrollTop(){
    return Math.max(
        //chrome
        document.body.scrollTop,
        //firefox/IE
        document.documentElement.scrollTop);
}
function documentHeight(){
    //现代浏览器（IE9+和其他浏览器）和IE8的document.body.scrollHeight和document.documentElement.scrollHeight都可以
    return Math.max(document.body.scrollHeight,document.documentElement.scrollHeight);
    // return document.body.scrollHeight==0?document.documentElement.scrollHeight:document.body.scrollHeight;
}
function windowHeight(){
    return (document.compatMode == "CSS1Compat")?
        document.documentElement.clientHeight:
        document.body.clientHeight;
}
````     
### 某个div滚动到底部    
````
    var nScrollHight = 0; //滚动距离总长(注意不是滚动条的长度)
    var nScrollTop = 0;  //滚动到的当前位置
    var nDivHight = $('#hot_box').height();
    var page = 1;
    $('#hot_box').on('scroll',function(){
        nScrollHight = $(this)[0].scrollHeight;
        h_nScrollTop = $(this)[0].scrollTop;
        if(nScrollTop + nDivHight >= nScrollHight){
            page++;
        } 
    });
````
### url整理    
````
function parseURL(url) {
    var a = document.createElement('a');
    a.href = url;
    return {
        source: url,
        protocol: a.protocol.replace(':', ''),
        host: a.hostname,
        port: a.port,
        query: a.search,
        params: (function () {
            var ret = {},
                seg = a.search.replace(/^\?/, '').split('&'),
                len = seg.length,
                i = 0,
                s;
            for (; i < len; i++) {
                if (!seg[i]) {
                    continue;
                }
                s = seg[i].split('=');
                ret[s[0]] = s[1];
            }
            return ret;
        })(),
        file: (a.pathname.match(/\/([^\/?#]+)$/i) || [, ''])[1],
        hash: a.hash.replace('#', ''),
        path: a.pathname.replace(/^([^\/])/, '/$1'),
        relative: (a.href.match(/tps?:\/\/[^\/]+(.+)/) || [, ''])[1],
        segments: a.pathname.replace(/^\//, '').split('/')
    };
}
````
### xhr兼容性   
````
function createXMLHttpObject() {
    var XHRFactory = [
    function () {
            return new XMLHttpRequest();
    },
    function () {
            return new ActiveXObject('Msxml2.XMLHTTP');
    },
    function () {
            return new ActiveXObject('Msxml3.XMLHTTP');
    },
    function () {
            return new ActiveXObject('Microsoft.XMLHTTP');
    }
  ];
    var xhr = false;
    for (var i = 0; i < XHRFactory.length; i++) {
        try {
            xhr = XHRFactory[i]();
        } catch (e) {
            continue;
        }
        break;
    }
    return xhr;
}
````

### 格式化视频、音频时长     
````
function format_duration(time) {
  if (time > -1) {
    var hour = Math.floor(time / 3600);
    var min = Math.floor(time / 60) % 60;
    var sec = time % 60;
    if (hour < 10) {
      time = "0" + hour + ":";
    } else {
      time = hour + ":";
    }

    if (min < 10) {
      time += "0";
    }
    time += min + ":";

    if (sec < 10) {
      time += "0";
    }
    time += sec;
  }
  return time;
}

````
### 去除html标签
```
function delHtmlTag(str)
{
      return str.replace(/<[^>]+>/g,"");//去掉所有的html标记
}
```
### 统计字数
```
t = $('.remarktext').html().replace(/<[^>]+>/g,"").length
```

### 防抖和截流函数
```
let deBounce = (fn, delay) => {
    let timer = null;
    return function (...args) {
        if (timer) {
            clearTimeout(timer);
        }
 
        timer = setTimeout(()=> {
            fn(...args);
        }, delay)
    }
}
 
 
let throttle = (fn, delay) => {
    let flag = true;
    return function (...args) {
        if (!flag) return;
        flag = false;
        setTimeout(() => {
            fn(...args);
            flag = true;
        }, delay)
    }
}
```

