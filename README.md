# getreceipt-server
这个是个人收款的服务端，搭配receiptnotice的安卓端

### 才刚开始写
想法是用最简单的php的flight微框架


### 安装
- 将项目放到服务器，然后运行`composer install` 

- 配置服务器，将请求搞到index.php
比如apache 
```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php [QSA,L]
```
比如 Nginx
```
server {
    location / {
        try_files $uri $uri/ /index.php;
    }
}
```
- 创建数据库getreceipt，当然你也可以叫其它名字：`CREATE DATABASE getreceipt`,然后将model目录下的model.sql导入getreceipt数据库中`mysql -u 用户名 -p 数据库名 < model.sql`

- 配置config目录下的数据库配置文件，推荐用环境变量，如果不配置环境变量或者数据库连接出错，直接用下面的数组直接填写数据库帐号密码

- 拿本机localhost举例，这个时候访问`http://localhost/`会出现"愿你赚很多钱",如果数据库配置正确访问`http://localhost/database/info`会出现你的数据库信息,比如我的是：
```
{"desc":{"server":"Uptime: 11108  Threads: 1  Questions: 2304  Slow queries: 0  Opens: 238  Flush tables: 1  Open tables: 219  Queries per second avg: 0.207","driver":"mysql","client":"mysqlnd 5.0.12-dev - 20150407 - $Id: 38fea24f2847fa7519001be390c98ae0acafe387 $","version":"5.7.23-0ubuntu0.18.04.1","connection":"Localhost via UNIX socket"}}
```






##### 这个可搭配安卓客户端receiptnotice
[receiptnotice](https://github.com/WeihuaGu/receiptnotice)
