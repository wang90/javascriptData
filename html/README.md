## HTML中遇见的问题
### 图片请求链接403，但正常图片链接存在
````````
// 在html中添加
<meta name="referrer" content="no-referrer" />
````````
###### 原理
默认http请求中会带有一个referrer字段，服务器端可以通过referrer值判断请求是否来自本站，若不是则返回403或者重定向返回其他信息，从而实现图片的防盗链。通过添加上面的html，告诉客户端不带这个referrer信息

## a标签的一些使用方法
- href链接
````
<a href="https://www.baidu.com">www.baidu.com</a>
````
- 锚点
````
<div id="div"></div>
//...
<a href="#div">跳转到id="div"标签的位置</a>

<a href="#">回到顶部</a>
````
- 唤起电话
````
<a href="tel:151****1234">151****1234</a>
````
- 发送短信
````
<a href="sms:151****1234">151****1234</a>
````
- 发送邮件
````
<a href="mailto:151****1234@qq.com">151****1234@qq.com</a>
````
- 唤起其他协议
````
// 需要内置app自定义协议例如testapp:
<a href="testapp:login_app()">app登录</a>
````
