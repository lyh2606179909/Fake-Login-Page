#wifi钓鱼网页
打开终端窗口，输入下列命令：

mysql -u root
此时你将进入MySQL命令行界面，我们需要创建一个数据库来保存钓鱼网站中的数据。下列命令将创建一个名叫xeus的数据库：

create database xeus
接下来切换到我们刚刚创建完成的数据库中：

use xeus
现在，我们要创建一个表（table），并用它来存储目标用户的数据：

create table logins(network varchar(64), email varchar(64), password varchar (64));
