摸不清头脑的javascript
````
var x = .3 - .2  
var y = .2 - .1  
x === y ?   
x === 0.1?  
y === 0.1?  
````
计算1-4的随机数
````
Math.floor(Math.random()*4) + 1   
````
空数组，空对象为true   
[]==true   
{}==true   

x+'' //等价于String(x);   
+x //等价于Number(x)，可以写成x-0;  
!!x //等价于Boolean(x);  

变量名提升  
````
var scope = 'global';
function f(){
  console.log(scope); //undefined
  var scope 'local';  //变量名提升
  console.log(scope); //local
}
````

左值  
=左边的是左值，如 var age=30，age变量可以作为左值，但不能 30=age  。30不是左值   
