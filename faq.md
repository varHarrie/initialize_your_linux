# linux常见问题

## 怎么安装deb包？

```bash
# 安装*.deb
$ sudo dpkg -i xxx.deb
# 安装失败可以尝试下面命令，再重试安装
$ sudo apt-get install -f
```

## ssh命令等待时间过长

```bash
# 编辑
$ sudo gedit /etc/ssh/ssh_config
```

找到`GSSAPIAuthentication yes`，把`yes`改为`no`，如果没有则自己添加