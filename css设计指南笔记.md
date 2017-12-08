
css设计指南笔记
一. HTML标记于文档结构  
1.文本闭合标签  
2.引用内容用自闭合标签  

非文本内容是通过自闭合标签显示的。  
闭合标签与自闭合标签的区别在于，  
闭合标 签包含的是会显示的实际内容，  
而自闭合标签只是给浏览器提供一个对要显示内容的引用。  
浏览器会在 HTML 页面加载的时候，额外向服务器发送请求，以取得自闭 合标签引用的内容。  

3.HTMl模版  
（1）<title><title>  
  搜索引擎会给<title>标签中的文字内容赋予很高的权重。  
  而且这些文字也会作为网页标题出 现在搜索结果列表中。  
  一定要让这些文字简洁明确，而且包含目标读者在搜索你的网页内容时会使用的关键词。  
  
二.css工作原理  
1.css规则命名惯例  

（1）第一种方法:多个声明包含在一条规则里。    
     p {color:red; font-size:12px; font-weight:bold;}  
（2）第二种方法:多个选择符组合在一起  
     h1, h2, h3 {color:blue; font-weight:bold;}  
（3）第三种方法:多条规则应用给一个选择符。
     h1, h2, h3 {color:blue; font-weight:bold;}  
     h3 {font-style:italic;}   
     
所有用于选择特定元素的选择符又分三种。  
 上下文选择符。基于祖先或同胞元素选择一个元素。   
 ID 和类选择符。基于 id 和 class 属性的值(你自己设定)选择元素。   
 属性选择符。基于属性的有无和特征选择元素。  

2.上下文选择符(后代组合式选择符)       
上下文选择符的格式如下:  
标签 1 标签 2 {声明}    

3.特殊的上下文选择符  
<section>
    <h2>An H2 Heading</h2>
    <p>This is paragraph 1</p>
    <p>Paragraph 2 has <a href="#">a link</a> in it.</p>
    <a href="#">Link</a>
</section>
(1)子选择符>
  标签 1 > 标签 2  
  section > h2 {font-style:italic;}   
(2)紧邻同胞选择符+   
  标签 1 + 标签 2   
  h2 + p {font-variant:small-caps;}   
(3)一般同胞选择符~   
  标签 1 ~ 标签 2   
  h2 ~ a {color:red;}   
(4)通用选择符*  
  * {color:green;}   
  p * {color:red;}   
  
4.ID 和类选择符
  
  
