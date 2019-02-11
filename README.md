# QQSpider
QQSpider Fork from https://github.com/LiuXingMing/QQSpider QQSpider2

# 使用说明：

开发语言：Python 3.7 

Redis:3.2.100

Python编辑器：PyCharm 2018.3.4 (Professional Edition)

## 启动前配置：

* 需要安装的软件：python 3.X版本、Redis（Redis服务启动后能连接上就行，不需要建表什么的）、Mongo 连接的远程的应用不需要本地安装。
* 需要安装的Python模块：requests、BeautifulSoup、multiprocessing、selenium、itertools、redis、pymongo。
* 模块安装 pip3 install [指定模块] e.g. pip3 install requests
* 我们登陆QQ要使用到phantomJS（下载地址：http://phantomjs.org/download.html），下载完将里面的 phantomjs.exe 解压到python目录下即可。


## 启动程序：

* 进入 myQQ.txt 写入QQ账号和密码（不同QQ换行输入，账号密码空格隔开）。如果你只是测试一下，则放三两个QQ足矣；但如果你开多线程大规模抓取的话就要用多一点QQ号（thread_num_QQ的2~10倍），账号少容易被检测为异常行为。
* 进入 QQForSpider.txt 爬虫填写入口 QQ 号，一个 QQ 号一行
* 进入 init_messages.py 进行爬虫参数的配置，例如线程数量的多少、设置爬哪个时间段的日志，哪个时间段的说说，爬多少个说说备份一次等等。

## 运行 launch.py 启动爬虫。
python launch.py

## 查看数据
到官网下载 [MongoDB Compass Community](https://www.mongodb.com/download-center/community)，连接 MongoDB 65.49.204.74:27017

如下图：
![截图](https://github.com/fantasylion/QQSpider/blob/master/Document/20190211172713.png?raw=true)

## 数据库说明：
QQSpider主要爬取QQ用户的说说、日志、朋友关系、个人信息。 
数据库分别设置 Mood、Blog、Friend、Information 四张表。

## 表结构

__Mood 表：__
```
_id：采用 “QQ_说说id” 的形式作为说说的唯一标识。 
Co-oridinates：发说说时的定位坐标，调用地图API可直接查看具体方位，可识别到在哪一栋楼。 
Comment：说说的评论数。 
Like：说说的点赞数。 
Mood_cont：说说内容。 
PubTime：说说发表时间。 
QQ：发此说说的QQ号。 
Source：说说的根源（对于转发的说说），采用 “QQ_说说id” 的形式标识。 
Tools：发说说的工具（手机类型或者平台）。 
Transfer：说说的转发数。 
URL：说说的链接地址。 
isTransfered：此说说是否属于转发来的。
```

__Blog 表：__
```
_id：采用 “QQ_日志id” 的形式作为日志的唯一标识。 
Blog_cont：日志内容。 
Comment：日志的评论数。 
Like：日志的点赞数。 
PubTime：日志的发表时间。 
QQ：发此日志的QQ号。 
Share：日志的分享数。 
Source：日志的根源（对于转发的日志），采用 “QQ_日志id” 的形式标识。 
Title：日志的标题。 
Transfer：日志的转发数。 
URL：日志的链接地址。 
isTransfered：此日志是否属于转发来的。
```

__Friend 表：__
```
_id：采用 QQ 作为唯一标识。 
Num：此QQ的好友数（仅统计已抓取到的）。 
Fx：朋友的QQ号，x代表第几位好友，x从1开始逐渐迭加。
```

__Information 表：__
```
_id：采用 QQ 作为唯一标识。 
Age：年龄。 
Birthday：出生日期。 
Blog：已发表的日志数。 
Blogs_WeGet：我们已抓取的日志数。 
Blood_type：血型。 
Career：职业。 
Company：公司。 
Company_address：公司详细地址。 
Company_city：公司所在城市。 
Company_country：公司所在国家。 
Company_province：公司所在省份。 
Constellation：星座。 
CurrentTime：抓取当前信息的时间（不同时间信息会不同）。 
FriendsNum：好友数（仅统计已抓取的）。 
Gender：性别。 
Hometown_city：故乡所在城市。 
Hometown_country：故乡所在国家。 
Hometown_province：故乡所在省份。 
Living_city：居住的城市。 
Living_country：居住的国家。 
Living_province：居住的省份。 
Marriage：婚姻状况。 
Message：空间留言数。 
Mood：已发表的说说数。 
Mood_WeGet：我们已抓取的说说数。 
PageView：空间总访问量。 
Picture：已发表的照片数（包括相册里的照片和说说里的照片）。
```


