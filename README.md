#wifi钓鱼网页
打开终端窗口，输入下列命令：

mysql -u root
此时你将进入MySQL命令行界面，我们需要创建一个数据库来保存钓鱼网站中的数据。下列命令将创建一个名叫xeus的数据库：

create database xeus
接下来切换到我们刚刚创建完成的数据库中：

use xeus
现在，我们要创建一个表（table），并用它来存储目标用户的数据：

create table logins(network varchar(64), email varchar(64), password varchar (64));
设置WiFi-Pumpkin
WiFi-Pumpkin是一款专用于无线环境渗透测试的完整框架，它非常适用于我们的WiFi访问点攻击。它拥有大量的插件和模块，而且它所能做的远远不止钓鱼攻击那么简单，但我们目前只需要使用下面这三种模块：Rogue AP、Phishing Manager和DNS Spoof。在这些模块的帮助下，我们就能够将钓鱼页面连接到流氓热点上，然后将它呈现给毫不知情的用户了。那么，让我们开始吧！
