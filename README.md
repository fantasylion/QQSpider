# QQSpider
QQSpider Fork from https://github.com/LiuXingMing/QQSpider QQSpider2

# 使用说明：

开发语言：Python 3.7 
Redis:3.2.100


## 启动前配置：

* 需要安装的软件：python 3.X版本、Redis（Redis服务启动后能连接上就行，不需要建表什么的）、Mongo 连接的远程的应用不需要本地安装。
* 需要安装的Python模块：requests、BeautifulSoup、multiprocessing、selenium、itertools、redis、pymongo。
* 我们登陆QQ要使用到phantomJS（下载地址：http://phantomjs.org/download.html），下载完将里面的 phantomjs.exe 解压到python目录下即可。


## 启动程序：

进入 myQQ.txt 写入QQ账号和密码（不同QQ换行输入，账号密码空格隔开）。如果你只是测试一下，则放三两个QQ足矣；但如果你开多线程大规模抓取的话就要用多一点QQ号（thread_num_QQ的2~10倍），账号少容易被检测为异常行为。
进入 init_messages.py 进行爬虫参数的配置，例如线程数量的多少、设置爬哪个时间段的日志，哪个时间段的说说，爬多少个说说备份一次等等。

## 运行 launch.py 启动爬虫。

## 查看数据
到官网下载 [MongoDB Compass Community](https://www.mongodb.com/download-center/community)，连接 MongoDB 65.49.204.74:27017

如下图：
![截图](https://github.com/fantasylion/QQSpider/blob/master/Document/20190211172713.png?raw=true)

## 数据库说明：
QQSpider主要爬取QQ用户的说说、日志、朋友关系、个人信息。 
数据库分别设置 Mood、Blog、Friend、Information 四张表。


