# debain系linux常用命令

## 安装deb包

```bash
# 安装*.deb
$ sudo dpkg -i xxx.deb
# 安装失败可以尝试下面命令，再重试安装
$ sudo apt-get install -f
```