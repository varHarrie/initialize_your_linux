# 安装node和npm

## （一）通过nvm进行安装和管理（推荐）

最新版本获取方法，请查看[官方仓库](https://github.com/creationix/nvm)

下面提供的安装方法可能不是最新版本

1、通过`curl`安装`nvm`

```bash
# v0.33.1为编写该教程时（2017-03-16）最新版本
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

2、重启bash，运行`nvm`命令，显示命令帮助信息

3、如果第2步成功，请忽略该步骤

以下代码会自动添加，如果没有请手动添加到`~/.bash_profile`或`~/.zshrc`或`~/.profile`或`~/.bashrc`

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
```

4、通过`nvm`安装`node`

```bash
# 安装指定版本
$ nvm install v6.10.0
# 安装最新版本
$ nvm install node
```

其他命令请通过`nvm --help`或官方文档查看

## （二）通过已编译文件安装

1、下载node（[官网](https://nodejs.org/en/download/current/)或[国内镜像](https://cnpmjs.org/mirrors/node)），例如`node-v6.9.1-linux-x64.tar.gz`

2、解压到任意目录（保证长期保留，例如解压到`/home/harrie/Softwares/node-v6.9.1-linux-x64`）

```bash
# 解压
$ tar -zxvf node-v6.9.1-linux-x64.tar.gz
```

3、设置为全局命令

*方法一*：创建软链接到/usr/local/bin

```bash
# 软链接方式（具体目录改为你自己的）
$ sudo ln -s /home/harrie/Softwares/node-v6.9.1-linux-x64/bin/node /usr/local/bin/node
$ sudo ln -s /home/harrie/Softwares/node-v6.9.1-linux-x64/bin/npm /usr/local/bin/npm
```

*方法二*：添加bin目录到PATH环境变量中

```bash
# 打开.profile
$ sudo gedit ~/.profile
# 添加以下代码（具体目录改为你自己的）
export PATH=$PATH:/home/harrie/Softwares/node-v6.9.1-linux-x64/bin
```

注意：如果出现npm或node命令可用，但sudo npm或sudo node不可用，还需要：

1. 编辑/etc/sudoers文件，把Defaults  env_reset改成Defaults ! env_reset

2. 编辑.bashrc，最后添加alias sudo='sudo env PATH=$PATH'

## （三）通过源文件安装

1、下载node源码，下载链接同上，比如`node-v6.9.1.tar.gz`

2、解压、编译、安装

```bash
# 解压、编译、安装
$ tar -zxvf node-v6.9.1.tar.gz
$ cd node-v6.9.1
$ ./configure
$ make
$ make install
$ cp /usr/local/bin/node /usr/sbin
```

## （四）apt-get（严重不推荐，仅供警示）

注意：通过这种方式安装，不能使用node命令，只能用nodejs命令，并且不能保证最新版

```bash
# apt-get安装
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```

## 常见问题

1. `sudo npm xxx`或`sudo node`提示找不到命令

造成这个问题的根本原因是，`sudo`命令执行的目录是`/etc/sudoers`中定义的`secure_path`，要么将命令软连接到这些目录，要么修改目录路径。

解决方案一：创建软连接

```bash
$ sudo ln -s /usr/local/bin/node /usr/bin/node
$ sudo ln -s /usr/local/bin/npm /usr/bin/npm
```
解决方案二：修改sudo目录

编辑/etc/sudoers文件，把`Defaults  env_reset`改成`Defaults ! env_reset`

编辑`~/.bashrc`或`~/.zshrc`，最后添加`alias sudo='sudo env PATH=$PATH'`

执行
```bash
$ source ~/.bashrc
# 或
$ source ~/.zshrc
```
