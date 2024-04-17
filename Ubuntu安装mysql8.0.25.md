# ubuntu安装mysql8.0.25

新建mysql文件夹

```
mkdir mysql/
```

进入mysql文件夹

```
cd mysql/
```

依赖项安装

```
sudo apt install -y libaio1 libmecab2 man-db libc-bin
```

下载mysql安装包

```
wget https://cdn.mysql.com/archives/mysql-8.0/mysql-server_8.0.25-1ubuntu21.04_amd64.deb-bundle.tar
```

解压安装包

```
tar -xf mysql-server_8.0.25-1ubuntu21.04_amd64.deb-bundle.tar
```

按照顺序安装

```
sudo dpkg -i mysql-community-client-plugins_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-community-client-core_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-common_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-community-client_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i libmysqlclient21_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i libmysqlclient-dev_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-client_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-community-server-core_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-community-server_8.0.25-1ubuntu21.04_amd64.deb
sudo dpkg -i mysql-server_8.0.25-1ubuntu21.04_amd64.deb
```

#倒数第二个mysql-community-server_8.0.25-1ubuntu21.04_amd64.deb安装时会让输入root的密码和加密方式

#正数第二个sudo dpkg -i mysql-community-client-core_8.0.25-1ubuntu21.04_amd64.deb	安装时会提示缺少libssl
#但是直接apt install libssl无法安装 一下指令可以安装

```
echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list
sudo apt-get update
sudo apt-get install libssl1.1
```

重启mysql

```
sudo service mysql restart
```

登录mysql指令

```
mysql -uroot -p#你设置的密码
```

