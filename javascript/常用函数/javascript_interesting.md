# 摸不清头脑的javascript
````
var x = .3 - .2  
var y = .2 - .1  
x === y ?   
x === 0.1?  
y === 0.1?  
````
### 计算1-4的随机数
````
Math.floor(Math.random()*4) + 1   
````
### 空数组，空对象为true   
```````
[]==true   
{}==true
```````
```````
x+'' //等价于String(x);   
+x //等价于Number(x)，可以写成x-0;  
!!x //等价于Boolean(x);  
```````

### 变量名提升  
````
var scope = 'global';
function f(){
  console.log(scope); //undefined
  var scope 'local';  //变量名提升
  console.log(scope); //local
}
`````

###左值理解  
``````
=左边的是左值，如 var age=30，age变量可以作为左值，但不能 30=age  。30不是左值   

1+{} //'1[object object]'  
2+null //2  
2+ undefined //NaN
```````

## 对象  
对象是Javascript的基本数据类型，是一种复合值，它将很多值聚合在一起，可通过名字访问这些值   
每一个对象都有之间相关联的原型、类、和可扩展性  

## 数组  
数组是值的有序集合，每个值叫做一个元素，而每个元素在数组中有一个位置，以数字表示，称为索引  
````
forEach(funciton(val,i,a){
  console.log(val) //值
  console.log(i) //index
  console.log(a) //原始数组
})
````











