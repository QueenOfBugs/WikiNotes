## Centos部署scrapy-redis

### 软件安装:

```
yum install git python3.8 mysql mysql-server redis
```
- git用来下载项目源码
- python3.8是我爬虫用的版本
- mysql和mysql-server一起才有完整的数据库客户端和服务器端
- redis数据库

#### 软件配置:

- MYSQL:[Centos8_安装配置MYSQL](Centos8_安装配置MYSQL) 参考博文:https://www.cnblogs.com/kasnti/p/11929030.html
- REDIS:修改redis.conf文件
    - 允许远程访问:
        - `# bind 127.0.0.1`
        - `protected-mode no`
- 开放服务器远程连接的端口:
    - redis:
        - `firewall-cmd --add-port=6379/tcp --permanent`
    - mysql:
        - `firewall-cmd --add-port=3306/tcp --permanent`
    - 重启防火墙设置:
        - `firewall-cmd --reload`

### 程序准备:

**下载项目代码:**

```
$ git clone https://github.com/QueenOfBugs/biqugeSpider.git
```

**安装python虚拟环境**
```
$ pip3 install pipenv
```

**同步使用的包**
```
$ cd biqugeSpider
$ pipenv update
```

### 运行程序:

#### 打开redis数据库:

```
# 按照指定配置启动redis
$ redis-server /etc/redis.conf
```

#### 运行爬虫
```
$ cd biqugeSpider/biqugePro/biqugePro/spiders/
$ scrapy runspider biquge.py
```
运行后不会和平时的爬虫一样运行程序，而是等待redis数据库加入起始爬取url

加入起始url
```
$ redis-cli
127.0.0.1:6379> lpush biquge https://www.biquge.info/paihangbang_allvisit/1.html
```
程序就开始运行了.

**本机的爬虫程序:**
- 修改要链接的redis数据库:
    - `REDIS_HOST = '198.13.46.22'`
    - `REDIS_PORT = 6379`
- 修改mysql数据库链接:
```
self.connect = pymysql.Connect(
    #  host='127.0.0.1', port=3306, user='root', password='kamisama', db='spider'
    host='198.13.46.22', port=3306, user='root', password='kamisama', db='spider'
                            )
```
- 运行爬虫程序:
    - `scrapy runspider biquge.py`

------------

分析总结:

最开始尝试时租用的服务器是单核，1G内存的服务器，并且启用了scrapy-redis的pipeline，这个pipeling会将爬取的数据(ITEM)发送到redis数据库，由于redis是基于内存的，所以运行一段时间后内存被占满，ssh连接直接卡死。
换了四核8G的服务器，并将爬取到的数据直接通过链接服务器端的mysql数据库进行存储后可以一直正常运行,服务器端的爬取速度和在本地测试的差不多，可能是网速原因，本地的爬取速度就比之间单机测试的时候慢多了，毕竟服务器是从自己本机的redis获取请求，而我本地的需要连接到它日本机房的服务器上的redis数据库才能获取请求
