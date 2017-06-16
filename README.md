学习Javascript 数据结构  

一.数组      
1.创建数据  
var arr = new Array()   
var arr = [];   
2.添加和删除元素  
arr.push();//添加元素到最后一位  
arr.unshift();//添加元素到第一位  
arr.pop();//删除元素的最后一个，并且返回这个元素  
arr.shift();//删除元素的第一个，并且返回这个元素  
3.二维数据  
（1）二维数组   
//创建二维数据  
````
var averageTemp = 0;    
    averageTemp[0] =[];     
    averageTemp[0][0] =72;  
    averageTemp[0][1] =75;  
    averageTemp[0][2] =79;  
    averageTemp[0][3] =79;  
    averageTemp[0][4] =81;  
    averageTemp[0][5] =81;  
    averageTemp[1] =[];         
    averageTemp[1][0] =81;  
    averageTemp[1][1] =79;  
    averageTemp[1][2] =75;  
    averageTemp[1][3] =75;  
    averageTemp[1][4] =73;  
    averageTemp[1][4] =73;  
    
function prinMatrix (myMatrix) {
    for(var i = 0 ; i<myMatrix.length;i++){
        for(var j = 0 ; j < myMatrix[i].length ;j++){
            console.log(myMatrix[i][j]);
        }
    }
}
prinMatrix (averageTemp)；
````

4.数组的方法  
concat //链接两个数组或者更多的数组，并且返回结果  
every //对数组中的每一项运行给定的函数，返回该函数的每一项返回的true,则返回true;  
filter //对数组中的每一项运行给定的函数，返回该函数会返回的true的项组成的数组  
forEach //对数组中的每一项运行给定函数，这个方法没有返回值  
join //将所有的数组元素链接成一个字符串  
indexOf //返回第一个与给定参数相等的数组元素的索引值，没有找到的则返回-1  
lastIndexOf //返回数组中搜索到的与给定参赛相同元素的索引里最大的值；  
map //对数组中的每一项运行给定函数，返回每次函数跳用的结果组成的数组  
reverse //颠倒数组的中的元素的顺序  
silce //传入索引值，将数组里对应的索引范围内的元素作为新数组返回  
some //对数组中的每一项运行给定函数，  
sort //按照字母顺序对数组排序，支持传入指定排序方法的函数作为参数  
toString//将数组作为字符串返回   
vauleOf//将数组作为字符串返回   

二.栈
栈是一种遵循从后进先出原则的有序集合  
新添加的或待删除的元素都保存在栈的末尾，称为栈顶，另一端就叫做栈底   
新元素都靠近栈顶，旧元素都接近栈底   
````
function Stock() {
    /*创建栈*/
    var items =[];
    /*添加栈内元素*/
    this.push = function (ele) {
        items.push(ele);
    }
    /*返回栈顶部的元素，不做任何处理*/
    this.peek = function () {
        return items[items.length-1];
    }
    /*移除栈顶元素，返回该元素*/
    this.pop = function () {
        return items.pop();
    }
    /*清空栈*/
    this.clear = function () {
        items =[]
    }
    /*查看栈的长度*/
    this.size = function () {
        return items.length ;
    }
    /*判断是不是为空栈，true为空*/
    this.isEmpty = function () {
        return items.length ==0;
    }
}
````
三.队列      
队列是遵循FIEO（Firt In First Out先进先出，也称为先来先服务）原则的有序的项      
队列在尾部的添加新元素，并从顶部移除元素，最新添加的元素必须排在队列的末尾      
````
function Queue(){
  var items = [];
  /*向队列尾部添加一个（或多个）新的项*/
  this.enqueue =function(ele){
     items.push(ele)
  };
  /*移除队列的第一项*/
  this.dequeue = function(){
    return items.shift();
  };
  /*返回队列中的第一个元素*/
  this.front = function(){
    return items[0];
  };
  /*队列是否为空*/
  this.isEmpty = function(){
    return items.length ==0 ;
  };
  /*队列包含的元素个数*/
  this.size = function(){
    return items.length;
  }
}

````
*队列的变形
1.优先排队  
实现优先排队有两种选项    
（1）设置优先级，然后在正确的位置添加元素    
（2）用入列操作添加元素，然后按照优先级移除他们    
````
function PriorityQueue(){
  var items = [];
  /*创建一个队列内容的对象，ele为该元素，prioity为优先等级*/
  function QueueElement (ele,priority){
    this.ele = ele;
    this.priority = priority;
  };
  /*向队列尾部添新的项*/
  this.enqueue = function(ele,priority){
    var queueElement = new QueueElement(ele,priority);
    if(this.isEmpty()){
      items.push(queueElement);
    }else{
      var added = false;
      for(var i = 0 ; i < items.length;i++){
        if(queueElement.priority < items[i].priority){
          items.slice(i,0,queueElement);
          added = true;
          break;
        }
      }
      if(!added){
        items.push(queueElement);
      }
    }
  };
  /*移除队列的第一项*/
  this.dequeue = function(){
    return items.shift();
  };
  /*返回队列中的第一个元素*/
  this.front = function(){
    return items[0];
  };
  /*队列是否为空*/
  this.isEmpty = function(){
    return items.length ==0 ;
  };
  /*队列包含的元素个数*/
  this.size = function(){
    return items.length;
  }
}
````
2.循环排队--击鼓传花     
````
function hotPotato(nameList,num){
  var queue = new Queue();
  for(var i = 0 ; i<nameList,length;i++){
    queue.enqueue(nameList[i])
  }
  var eliminated = '';
  while (queue.size()>1){
    for(var i =0 ;i<num;i++){
      queue.enqueue(queue.dequeue);
    }
  }
  return queue.dequeue();
}
````
四.链表    
存储有序的元素集合   
````
function LinkedList(){
  var Node = function(ele){
    this.ele = ele;
    this.next = null;
  }
  var length = 0;
  var head = null;
  /*添加尾部新的项*/
  this.append = function(ele){
    var node = new Node(ele),
        current;
    if(head ==null){
      head =node;
    }else{
      current = head ;
      while (current.next){
        current = current.next;
      }
      current.next = node;
    }
    length++;
  };
  /*添加插入一个新的的项*/
  this.insert = function(position,ele){
      if(position >=0 && position <=length){
        var node = new Node(ele),
        current = head ,
        previous,
        index = 0;
        if(position ==0){
           node.next =current;
           head = node ;
        }else{
          while (index ++<position){
            previous = current;
            current =current.next;
          }
          node.next = current;
          previous.next = node;
        }
        length ++;
        return true;
      }else{
        return false;
      }
  }
  /*移除列表中特定位置的一项*/
  this.removeAt = function(position){
    if(position>-1 && position<length){
      var current = head,
        previous,
        index =0;
      if(position ===0){
        head = current.next ;
      }else{
        while (index++< position){
          previous = current;
          current = current.next;
        }
      }
      length --;
      return current.element;
    }else{
      return null;
    }
  }
  /*移除列表中的一项*/
  this.remove = function(ele){
    var index = this.indexOf(ele);
    return this.removeAt(index);
  }
  /*返回元素在列表中的索引，如果没有返回-1*/
  this.indexOf = function(ele){
    var current = head,
      index=0;
    while (current){
      if(ele === current.ele){
        return index;
      }
      index ++;
      current = current.next;
    }
    return -1;
  }
  /*列表是不是为空*/
  this.isEmpty = function(){
    return length ===0;
  }
  /*列表元素的个数*/
  this.size = function(){
    return length;
  }
  /*列表的第一项*/
  this.getHead = function(){
    return head;
  };
  /*输出值*/
  this.toString = function(){
    var current = head,
      string ='';
    while (current){
      string +=","+current.element;
      current = current.next;
    }
    return string.slice(1);
  }
}
````
*双向链表
````
function DoublyLinkedList(){
  var Node = function(ele){
    this.ele = ele;
    this.next = null;
    this.prev = null;
  }
  var length = 0,
      head =null,
      tail = null;
  this.insert = function(position,ele){
    if(position >=0 && position <=length){
      var node =new Node(ele),
        current = head,
        previous,
        index =0;
      if(position ===0 ){
        if(!head ){
          head =nodex;
          tail = node;
        }else{
          node.next = current;
          current.prev = node;
          head = node;
        }
      }else if(position ===length){
        current = tail;
        current.next =node;
        node.prev =current;
        tail = node;
      }else{
        while (index++ <position){
          previous = current;
          current = current.next;
        }
        node.next = current;
        previous.next = node;

        current.prev = node;
        node.prev = previous;
      }
      length ++;
      return true;
    }else{
      return false;
    }
  };
  this.removeAt = function(position){
    if(position >-1 && position <length){
      var current =head,
        previous,
        index =0;
      if(position ===0){
        head =current.next;
        if(length ===1){
          tail = null;
        }else{
          head.prev = null;
        }
      }else if(position === length - 1){
        current = tail;
        tail = current.prev;
        tail.next = null;
      }else{
        while (index ++ < position){
          previous = current;
          current = current.next;
        }
        previous.next = current.next;
        current.next.prev = previous;
      }
      length --;
      return current.ele;
    }else{
      return null;
    }
  };
  /*移除列表中的一项*/
  this.remove = function(ele){
    var index = this.indexOf(ele);
    return this.removeAt(index);
  }
  /*返回元素在列表中的索引，如果没有返回-1*/
  this.indexOf = function(ele){
    var current = head,
      index=0;
    while (current){
      if(ele === current.ele){
        return index;
      }
      index ++;
      current = current.next;
    }
    return -1;
  }
  /*列表是不是为空*/
  this.isEmpty = function(){
    return length ===0;
  }
  /*列表元素的个数*/
  this.size = function(){
    return length;
  }
  /*列表的第一项*/
  this.getHead = function(){
    return head;
  };
  /*输出值*/
  this.toString = function(){
    var current = head,
      string ='';
    while (current){
      string +=","+current.element;
      current = current.next;
    }
    return string.slice(1);
  }
}
````
五.集合   
由一组无序且唯一（既不能重复）的项组成的   
````
function Set(){
  var items = {};
  this.add = function(value){
    if(!this.has(value)){
      items[value] = value;
       return true;
    }
    return false;
  }
  this.remove = function(value){
    if(this.has(value)){
      delete items[value];
      return true;
    }
    return false;
  }
  this.has = function(value){
    return value in items ;
  }
  this.clear = function(){
    items = {};
  }
  this.size = function(){
    return Object.keys(items).length;
  };
  /*size的兼容写法*/
  this.sizeLegacy = function(){
    var count = 0 ;
    for( var prop in items ){
      if( items.hasOwnProperty(prop))
        ++count;
    }
    return count;
  }
  this.values = function(){
    var keys = [];
    for( var key in items ){
      if(items.hasOwnProperty(key)){
        keys.push(key);
      }
    }
    return keys;
  };

  /*并集*/
  this.union = function(otherSet){
    var unionSet = new Set();
    var values = this.values();
    for( var i = 0 ; i < values,length ;i++){
      unionSet.add(values[i]);
    }
    values = otherSet.values();
    for( var i = 0 ; i <values.length ;i++){
      unionSet.add(values[i]);
    }
    return unionSet;
  }
  /*交集*/
  this.intersection =function(otherSet){
    var intersectionSet = new Set();

    var values = this.values();
    for( var i = 0 ; i < values.length ;i++){
      if( otherSet.has(values[i])){
        intersectionSet.add(values[i]);
      }
    }
    return intersectionSet;
  }
  /*差集*/
  this.difference = function(otherSet){
    var differenceSet = new Set();
    var values = this.values();
    for( var i = 0 ; i<values.length ;i++){
      if(!otherSet.has(values[i])){
        differenceSet .add(values[i]);
      }
    }
    return differenceSet;
  }
  /*子集*/
  this.subset = function(otherSet){
    if(this.size() >otherSet.size()){
      return false;
    }else{
      var values = this.values();
      for( var i = 0 ; i < values.length ; i ++){
        if(!otherSet.has(values[i])){
          return false;
        }
      }
      return true;
    }
  }
}
````
六.字典
与Set类相似，ES6同样包含了一个MAP类的实现
````
function Dictionary(){
  var items ={};
  this.set = function(key,value){
      items[key] = value;
  }
  this.remove = function(key){
      if(this.has(key)){
        delete items[key];
        return true;
      }
    return false;
  }
  this.has = function(key){
      return key in items;
  }
  this.get = function(key){
      return this.has(key) ? items[key] : undefined;
  }
  this.clear = function(){
    items ={};
  }
  this.size = function(){
    return Object.keys(items).length;
  };
  this.keys = function(){
    var values = [];
    for( var k in items ){
      if(this.hasOwnProperty(k)){
        values.push([k]);
      }
    }
    return values;
  };
  this.getItems = function(){
    return items;
  }
  this.values = function(){
    var values = [];
    for( var k in items ){
      if(this.hasOwnProperty(k)){
        values.push(items[k]);
      }
    }
    return values;
  }
}
````


