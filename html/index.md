## HTML中遇见的问题
### 图片请求链接403，但正常图片链接存在
````````
// 在html中添加
<meta name="referrer" content="no-referrer" />
````````
###### 原理
默认http请求中会带有一个referrer字段，服务器端可以通过referrer值判断请求是否来自本站，若不是则返回403或者重定向返回其他信息，从而实现图片的防盗链。通过添加上面的html，告诉客户端不带这个referrer信息
