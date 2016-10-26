# 装机后首先做的事（挂载磁盘、修改hosts）

## 开机自动挂载磁盘（仅限deepin）

1、启动器中搜索“磁盘”并打开，如果没有在深度商店中搜索下载

2、选择磁盘，选择分区，点击齿轮按钮，点击“编辑挂载选项”，取消自动挂载选项，勾选启动时挂载、显示用户界面，自定义显示名称和挂载点，点击确定

## 改hosts

1、网上找到最新的hosts（或者[这里](https://laod.cn/hosts/2016-google-hosts.html)）

2、修改hosts文件

```bash
# 备份源文件
$ sudo cp /etc/hosts /etc/hosts.backup
# 打开并将内容复制到最下面（注意保留原来内容）
$ sudo gedit /etc/hosts
```