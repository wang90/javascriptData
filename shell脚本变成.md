一.变量替换  
 ${变量#匹配规则}   从头开始匹配，最短删除    
 ${变量##匹配规则}  从头开始匹配，最长删除    
 ${变量%匹配规则}   从尾开始匹配，最短删除  
 ${变量%%匹配规则}  从尾开始匹配，最长删除  
 ${变量/旧字符串/新字符串}  替换变量内的旧字符串为新字符串,只替换题第一个  
 ${变量//旧字符串/新字符串} 替换变量内的就字符串为薪资复还，全部替换  
   
二.字符串处理    
（1）计算字符串长度    
${#string}  
expr length "$string"  
(2)获取子串在字符中的索引位置  
expr index $string $substring  
(3)获取子串长度  
expr match $string substr   
(4)抽取子串   
${string:position}         从string中的position开始     
${string:position:length}  从position开始，匹配长度为length    
${string:-position}        从右边开始匹配     
${string:(position)}       从左边开始匹配  
expr substr $string $position $length 从position开始，匹配长度为length  
注：expr 索引从1开始 ，${str}索引长度从0开始


练习：
需求描述：变量string="Bigdata process framework is Hadoop,Hadoop is an open source project"
(1).打印string长度
(2).删除字符串汇总所有的Hadoop
(3).替换第一个Hadoop为Mapreduce
(4).替换全部Hadoop为Mapreduce
用户输入数字1|2|3|4，可以执行对应项目的功能：输入q|Q则为退出交互模式

 思路分析：
 1.将不同的功能模块划分，并比编写函数
  function print_tips    
  function len_of_string    
  function del_hadoop  
  function rep_hadoop_mapreduce_first  
  function rep_hadoop_mapreduce_all   
 2.实现第一步所定义的功能函数
 3.程序主流的设计
 
 
 (1)vim example.sh    
 (2)  
 ``````
 #!/bin/bash

string="bigdata process framework is Hadoop,Hadoop is an open source project"
function print_tips
{
	echo "**************"
	echo "(1).打印string长度"
	echo "(2).删除字符串汇总所有的Hadoop"
	echo "(3).替换第一个Hadoop为Mapreduce"
	echo "(4).替换全部Hadoop为Mapreduce"
	echo "*****************"	
}
function len_of_string
{
	echo "${#string}"
}
function del_hadoop
{
	echo "${string//Hadoop/}"
}
function rep_hadoop_mapreduce_first
{
	echo "${string/Hadoop/Mapreduce}"
}
function rep_hadoop_mapreduce_all
{
	echo "${string//Hadoop/Mapreduce}"
}

while true
do 
	echo "[string=$string]"
	echo
	print_tips
	read -p "Pls input your choice(1|2|3|4|q|Q): " choice
	
	case $choice in 
		1)
			len_of_string
			;;
		2)
			del_hadoop
			;;
		3)
			rep_hadoop_mapreduce_first
			;;
		4)
			rep_hadoop_mapreduce_all
			;;
		q|Q)
			exit
			;;
		*)
			echo "Error,input only in {1|2|3|4|q|Q}"
			;;
	esac
done
``````
(3)sh example.sh    


三.命令替换  
语法格式  
`command`  
$(command) 
例1: 获取计算机中所有用户名称    
``````
#!/bin/bash
#

index=1

for user in `cat /etc/passwd | cut -d ":" -f 1`
do 
	echo "This is $index user : $user"
	index=$(($index+1))
done
``````   

例2: 根据系统时间计算今年或明年
``````
echo "this is $(date +%Y) year"
echo "this is $(($(date +%Y)+1)) year"
``````
注：$(())算数运算，例如$((20+30))    

例3：根据系统时间获取今年还剩下多少星期，已经过了多少星期
``````
echo "this year have passed $(date +%j) days"
echo "this year have passed $(($(date +%j)/7)) weeks"
echo "there is $((365-$(date +%j))) days before new year"
echo "there is $(((365-$(date +%j))/7)) weeks before new year"
``````

例4: nginx 
``````
#!/bin/bash
#

#echo `(ps -ef | grep nginx | grep -v grep | wc -l)`

nginx_process_num=$(ps -ef | grep nginx | grep -v grep | wc -l)

if [ $nginx_process_num -eq 0 ];then
	systemctl start nginx
fi
``````
  
  
  
  
  
  
