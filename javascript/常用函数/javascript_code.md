
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
### url处理2
````
function getUrlParam( sUrl, sKey ) {
    if ( sUrl.indexOf("?") === -1 ){
      return null;
    }
    const left= sUrl.indexOf("?") + 1;
    const right= sUrl.lastIndexOf("#");
    const parasString = sUrl.slice(left, right);
    const paras = parasString.split('&');
    const parasjson = {};
    paras.forEach(function ( value, index, arr ) {
        var a = value.split('=');
        parasjson[a[0]] !== undefined ? parasjson[a[0]] = [].concat(parasjson[a[0]], a[1]) : parasjson[a[0]] = a[1];
    });

    const result = arguments[1] !== void 0 ? (parasjson[arguments[1]] || '') : parasjson;
    return result;
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
### 加入flash脚本
``````
<!-- [if IE]>
<object id ="move" type="application/x-shockwave-flash" width="300" height="300">
   <param name="movie" value="mymovie.swf">
</object>
<![endif]--><!--[if !IE]><-->
<embed name="movie" type="application/x-shockwave-flash"
    src="mymovie.swf" width="300" height="300">
<embed>
<!--> <![endif]-->
``````
### 生成文件并利用formdata通过ajax上传 
``````
var blob = new Blob([content], {
    type: "text/plain;charset=utf-8",
});
var file = new File([blob], filename);
var formData = new FormData();
formData.append("file", file);
$.ajax({
    type: "post",
    url: url,
    data: formData,
    processData: false,
    contentType: false,
    success: function (response) {

    },
    error: function (err) {
    },
});
``````
### 是否是手机
``````
function isPhone() {
  let check = false;
  (function(a) {
    if (
      /(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows (ce|phone)|xda|xiino/i.test(
        a
      ) ||
      /1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(
        a.substr(0, 4)
      )
    )
      check = true;
  })(navigator.userAgent || navigator.vendor || window.opera);
  return check;
}
``````
### 是否是ios
``````
function isIos() {
  if (/iPhone|iPod/i.test(navigator.userAgent)) {
    return true;
  }
  return false;
}
``````
### 是否是微信
``````
function isWeixin() {
  if (
    navigator.userAgent.toLowerCase().indexOf("micromessenger") > -1 ||
    typeof navigator.wxuserAgent !== "undefined"
  ) {
    return true;
  }
  return false;
}
``````
### 浏览器平台
``````
function getSys() {
  const Sys = {};
  const ua = navigator.userAgent.toLowerCase();
  const re = /(msie|firefox|chrome|opera|version).*?([\d.]+)/;
  const m = ua.match(re);
  Sys.browser = m[1].replace(/version/, "'safari");
  Sys.ver = m[2];
  return Sys;
}
``````
### 操作系统平台
``````
function osplant() {
  let os = "other";
  const agent = navigator.userAgent.toLowerCase();
  const isMac = /macintosh|mac os x/i.test(navigator.userAgent);
  if (agent.indexOf("win32") >= 0 || agent.indexOf("wow32") >= 0) {
    os = "win32";
  }
  if (agent.indexOf("win64") >= 0 || agent.indexOf("wow64") >= 0) {
    os = "win64";
  }
  if (isMac) {
    os = "mac";
  }
  return os;
}
``````
### 手机端长按删除
```````
let startTimer = '';
let endTimer = '';
const dom = xxx
dom.addEventListener('touchstart', function (e) {
    startTimer = +new Date();
})
dom.addEventListener('touchend',function (e) {
    endTimer = +new Date()
    if (endTimer - startTimer > 700) {
        // code 长按
    }
})
```````
### 下载图片
```````
const funDownload = function (content, filename='') {
    console.log(filename)
    const a = document.createElement('a')
    a.href = content
    a.download = ''
    a.click()
};

```````
### js升序排列
```````
function sort(arr) {
    return arr.sort(function(a, b){return a - b}); 
}
```````
### 复制去掉标签
````````
document.querySelector("div.txt").addEventListener("paste", function(e) {
  e.preventDefault();
  const text = e.clipboardData.getData("text/plain");
  document.execCommand("insertText", false, text);
});
````````

