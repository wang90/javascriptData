# nginx 修改配置    

### 1.下载nginx   
```````
yum install nginx -y   
```````

### 2.执行   
```````
nginx  
```````

### 3.创建文件
```````
mkdir /data/www   
```````

### 4.修改   
``````
vi  /etc/nginx/nginx.conf   
root /usr/share/nginx/html; 修改为: root /data/www;  
``````

### 5.重启   
``````
nginx -s reload  
``````

#### 可执行文件权限   
``````
chmod +xLiunx 
``````
