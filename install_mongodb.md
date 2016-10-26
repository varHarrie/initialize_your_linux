# 安装mongodb

- [官方安装文档](https://docs.mongodb.com/master/administration/install-on-linux/)
  - [Debain](https://docs.mongodb.com/master/tutorial/install-mongodb-on-debian/)
  - [Ubuntu](https://docs.mongodb.com/master/tutorial/install-mongodb-on-ubuntu/)
  - [使用源码安装](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-linux/)

> 本文以Deepin 15.3（Debain 8）为例。

## （一）使用apt-get安装

1、设置GPG Key（下次安装不用再设置）

```bash
# 设置
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
```

2、创建sources.list.d

```bash
# Debain 8：
$ echo "deb http://repo.mongodb.org/apt/debian jessie/mongodb-org/3.3 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```

3、更新包数据

```bash
# 更新
$ sudo apt-get update
```

4、安装MongoDB

```bash
# 安装最新版的MongoDB
$ sudo apt-get install -y mongodb-org
# 安装制定版本的MongoDB
$ sudo apt-get install -y mongodb-org=3.4.0-rc1 mongodb-org-server=3.4.0-rc1 mongodb-org-shell=3.4.0-rc1 mongodb-org-mongos=3.4.0-rc1 mongodb-org-tools=3.4.0-rc1
```

5、启动MongoDB

默认的数据文件和日志文件放在`/var/lib/mongodb`和`/var/log/mongodb`，可以在`/etc/mongod.conf`中配置`systemLog.path`和`storage.dbPath`来重新指定。

```bash
# 启动
$ sudo service mongod start
# 停止
$ sudo service mongod sto
# 重启
$ sudo service mongod restart
```

6、删除MongoDB

```bash
# 停止
$ sudo service mongod stop
# 删除包
$ sudo apt-get purge mongodb-org*
# 删除数据和日志
$ sudo rm -r /var/log/mongodb
$ sudo rm -r /var/lib/mongodb
```

## （二）手动安装

1、下载压缩包（[地址](https://www.mongodb.com/download-center?jmp=docs)），例如`mongodb-linux-x86_64-debian81-3.2.10.tgz`

2、解压到任意目录（长期保存），例如我的`/home/harrie/Softwares/mongodb-linux-x86_64-debian81-3.2.10`

```bash
# 解压
$ tar -zxvf mongodb-linux-x86_64-debian81-3.2.10.tgz
# 创建目录
$ mkdir -p ~/Softwares
# 移动到新目录
$ cp mongodb-linux-x86_64-debian81-3.2.10 ~/Softwares
```

3、绑定到全局

*方法一：配置环境变量*

```bash
# 编辑
$ sudo gedit ~/.bashrc
# 添加环境变量，注意更换你自己的目录
export PATH=<你的Mongodb目录>/bin:$PATH
```

*方法二：创建软链接*

```bash
# 创建软链接
$ sudo ln -s <你的Mongodb目录>/bin/mongod /usr/local/bin
$ sudo ln -s <你的Mongodb目录>/bin/mongo /usr/local/bin
```

4、启动Mongodb
创建默认的数据目录，如果需要另外指定，使用`dbpath`参数运行`mongod`

```bash
# 创建目录
$ sudo mkdir -p /data/db
```

- 默认方式运行

  ```bash
  # 默认运行
  $ mongod
  # 指定dbpath和logpath运行
  $ mongod --dbpath <数据目录> --logpath=<日志文件名>.log
  ```

- 通过配置文件运行

  创建配置文件，例如`mongodb.conf`，编写以下内容

  ```bash
  # 端口号
  # port = 27017

  # 日志路径（所在目录必须存在）
  logpath = /data/log/mongodb.log

  # 启动日志不追加，太过庞大
  logappend = false

  # 设置每个数据库将被保存在单独的目录
  # directoryperdb = true

  # 设置mongodb的db路径（所在目录必须存在）
  dbpath = /data/db

  # 后台驻留(守护)进程服务运行
  fork = true

  # 启用验证
  # auth = true

  # 安静输出
  # quiet = true
  ```

  启动mongod

  ```bash
  # 启动
  $ ./mongod -f <相对路径>/mongodb.conf
  ```

- 开机自启服务

  在/etc/init.d/目录下新建脚本文件mongodb
  ```bash
  # 新建文件
  $ sudo gedit /etc/init.d/mongodb
  ```

  文件内容如下，注意将`PROGRAM`和`CONFIG`分别改为自己的mongod路径和配置文件路径
  ```bash
  #!/bin/sh

  ### BEGIN INIT INFO
  # Provides:     mongodb
  # Required-Start:
  # Required-Stop:
  # Default-Start:        2 3 4 5
  # Default-Stop:         0 1 6
  # Short-Description: mongodb
  # Description: mongo db server
  ### END INIT INFO

  . /lib/lsb/init-functions

  PROGRAM=/home/harrie/Softwares/mongodb-linux-x86_64-debian81-3.2.10/bin/mongod
  CONFIG=/home/harrie/Softwares/mongodb-linux-x86_64-debian81-3.2.10/bin/mongodb.conf

  MONGOPID=`ps -ef | grep 'mongod' | grep -v grep | awk '{print $2}'`

  test -x $PROGRAM || exit 0

  case "$1" in
    start)
      ulimit -n 3000
      log_begin_msg "Starting MongoDB server"
      $PROGRAM -f $CONFIG
      log_end_msg 0
      ;;
    stop)
      log_begin_msg "Stopping MongoDB server"
      if [ ! -z "$MONGOPID" ]; then
          kill -15 $MONGOPID
      fi
      log_end_msg 0
      ;;
    status)
      ;;
    *)
      log_success_msg "Usage: /etc/init.d/mongodb {start|stop|status}"
      exit 1
  esac

  exit 0
  ```

  保存后修改文件权限
  ```bash
  # 修改为可执行脚步
  $ sudo chmod +x /etc/init.d/mongod
  ```

  更新注册开机脚步
  ```bash
  # 注册开机脚步
  $ sudo /usr/sbin/update-rc.d mongod defaults
  # 以后可以通过以下方法，移除开机注册脚步
  $ sudo /usr/sbin/update-rc.d -f mongod remove
  ```

  启动/停止服务
  ```bash
  # 查看服务进程
  $ ps -def | grep mongod
  # 启动进程
  $ sudo service mongod start
  # 停止进程
  $ sudo service mongod stop
  # 查看服务状态
  $ sudo service mongod status
  ```

  如果提示`Unit mongodb.service not found`错误，可以尝试以下方法
  ```bash
  # 停止进程，或通过ps -ef | grep mongod，用kill -9 xxx的方式
  $ sudo service mongod stop
  # 删除mongodb.lock（一般在/data/db下）
  $ sudo rm -rf /data/db/mongodb.lock
  # 删除日志文件
  $ sudo rm -rf /data/log/*
  # 重新启动，或先尝试通过mongod -f xxx.conf命令启动，进行验证
  $ sudo service mongod start
  ```