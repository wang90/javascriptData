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





