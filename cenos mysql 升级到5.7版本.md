# cenos mysql 升级 操作 步骤

- 停止MySQL运行服务

```shell
systemctl stop mysqld.service
```

- 查看所有mysql 安装包

```shell
rpm -qa | grep mysql
```

- 卸载所有mysql安装包

```shell
yum remove mysql-community*
```

- 下载 需要安装的 MySQL 安装包

```shell
wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
```

- 编译

```shell
rpm -ivh mysql57-community-release-el7-11.noarch.rpm
```

- 安装

```shell
yum -y install mysql-community-server
```

- 启动服务

```shell
service mysqld start
```

- 更新 MySQL 配置

```shell
mysql_upgrade -u root -p 
```

