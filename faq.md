# linux常见问题

## 怎么安装deb包？

```bash
# 安装*.deb
$ sudo dpkg -i xxx.deb
# 安装失败可以尝试下面命令，再重试安装
$ sudo apt-get install -f
```

## 压缩解压缩tar包

```bash
# 压缩
$ tar -zcvf 压缩包名称 文件1 文件2 ...
# 解压缩
$ tar -zxvf 压缩包名称
# 查看压缩包文件列表
$ tar -ztvf 压缩包名称

# 主选项
# c 打包（不包含压缩）
# x 拆包
# t 查看

# 辅选项
# z 压缩或解压
# v 压缩或解压过程显示文件名
# f 后面紧跟压缩包名称

# 其他参数可用 man tar 命令查看
```

## ssh命令等待时间过长

```bash
# 编辑
$ sudo gedit /etc/ssh/ssh_config
```

找到`GSSAPIAuthentication yes`，把`yes`改为`no`，如果没有则自己添加