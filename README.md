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
现在，我们需要完成一些基本配置。

1.   切换到“Settings”标签页；

2.   将“Gateway”设置成路由器的IP地址（一般情况下是192.168.1.1）；

3.   将“SSID”设置成一些可信度较高的名字，例如“我绝对是正规WiFi”或者“我绝对不是流氓热点”等等…

4.   如果你想让你的流氓热点安全系数较高，或者说店家的WiFi需要输入密码（那么你的目标用户将需要输入WiFi密码），你可以开启“Enable WiFi Security”，然后输入你想要设置的密码，这样可以进一步增加热点的可信度。如果店家的WiFi不用密码就可以连的话，你就不用开启这个功能了。

5.   别忘了配置你的外置无线网卡，一般来说都是wlan0或wlan1。

6.   在“Plugins”标签页中，取消“Enable Proxy Server”的勾选。

7.   打开“Modules”（菜单栏中），选择“Phishing Manager”。IP地址可以随意设置，例如10.0.0.1（端口为80），WiFi-Pumpkin可以通过多种方式帮助你连接到你的钓鱼页面。现在我们已经设置好了伪造的登录页面，然后在“Options”设置中开启“Set Directory”，将“SetEnv PATH”设置成网站文件的存放地址（/www）。设置完成之后，点击“Start Server”。

8.   在“Modules”->“DNS Spoofer”选项中开启“Redirect traffic from all domains”，然后点击“StartAttack”。

5.png

9.   在“View”菜单中选择“Monitor NetCreds”，点击“Capture Logs”。

Ok，一切已配置完成！现在，当目标用户连接到我们的流氓热点之后，他们将会被重定向到我们的钓鱼页面，用户在该页面所输入的任何数据都将会以明文形式存储在我们之前所设置的数据库中。
