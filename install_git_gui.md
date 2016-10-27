# 安装git图形化工具

[git官网](https://git-scm.com/downloads/guis)列出了一些在不同操作系统的工具。

其中Linux操作系统推荐以下几款：

## [SmartGit](https://www.syntevo.com/smartgit/)

优点：功能齐全，非商用免费

注意：
安装deb包失败，可能是缺少了jre，可以尝试以下方法，然后再重试安装：

```bash
# 更新
$ sudo apt-get update
# 安装缺少的包
$ sudo apt-get install -f
```

![图片](https://www.syntevo.com/smartgit/img/galery/git-project-s.png)

---

## [GitKraken](https://www.gitkraken.com/download)

优点：界面美观，有免费版和付费版
缺点：基于Electorn效率较低，有奇怪的Bug，但不影响正常使用

![图片](https://git-scm.com/images/guis/git-kraken@2x.png)