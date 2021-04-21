:CentOS:MYSQL:

#### CentOS服务器安装MYSQL
```
sudo yum install mysql mysql-server
```

##### 配置MYSQL

**启用mysql服务**

```
sudo systemctl enable --now mysqld
```

**确认mysql是否开启**

```
# 开启mysql
sudo systemctl start mysqld
# 查询mysql状态
sudo systemctl status mysqld
```

**初始化mysql**

```
sudo mysql_secure_installation
```

**配置远程登录**

> 上一步初始化中的是否不允许远程登录要设置为no

```
$ mysql -uroot -p
# 输入上一步设置的密码
mysql> use mysql;
mysql> update user set host='%' where user='root';
mysql> flush privileges;
mysql> exit;
Bye
# 防火墙开启3306端口
$ sudo firewall-cmd --add-port=3306/tcp --permanent
$ sudo firewall-cmd --reload
```
