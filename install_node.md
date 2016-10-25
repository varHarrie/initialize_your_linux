# 安装node和npm
## （一）通过已编译文件安装
1) 下载node（[官网](https://nodejs.org/en/download/current/)或[国内镜像](https://cnpmjs.org/mirrors/node)），例如`node-v6.9.1-linux-x64.tar.gz`
2） 解压到任意目录（保证长期保留，例如解压到`/home/harrie/Softwares/node-v6.9.1-linux-x64`）
```bash
$ tar -zxvf node-v6.9.1-linux-x64.tar.gz
```
3) 设置为全局命令

*方法一（推荐）*：添加bin目录到PATH环境变量中
```bash
# 打开.profile
$ sudo gedit ~/.profile
# 添加以下代码（具体目录改为你自己的）
export PATH=$PATH:/home/harrie/Softwares/node-v6.9.1-linux-x64/bin
```

*方法二*：创建快捷方式到/usr/local/bin（具体目录改为你自己的）
```bash
$ ln -s /home/harrie/Softwares/node-v6.9.1-linux-x64/bin/node /usr/local/bin/node
$ ln -s /home/harrie/Softwares/node-v6.9.1-linux-x64/bin/npm /usr/local/bin/npm
```
## （二）通过源文件安装
1) 下载node源码，下载链接同上，比如`node-v6.9.1.tar.gz`
2) 解压、编译、安装
```bash
$ tar -zxvf node-v6.9.1.tar.gz
$ cd node-v6.9.1
$ ./configure
$ make
$ make install
$ cp /usr/local/bin/node /usr/sbin
```

## （三）apt-get（严重不推荐，仅供警示）
注意：通过这种方式安装，不能使用node命令，只能用nodejs命令，并且不能保证最新版
```bash
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```