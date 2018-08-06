# 安装linxu须知

## 使用linux系统有什么新体验，或者收获？

- **培养程序员爱折腾的习惯**：作为程序员就应该要有`为了达到理想效果，不断努力尝试和总结更好的解决方案`的精神。也许在某些情况下会显得浪费时间，一旦养成一种良好的折腾方式，就再也不怕面对新问题了。

- **流畅的开发体验**：大多数情况下可以抛弃`资源管理器`了，手在鼠标和键盘之间切换的次数也减少了，无论是文件操作、使用node命令、连接远端服务器等等，全都靠一个命令行窗口可以解决，`简单、方便、快捷`。

- **强大的bash**：相对于windows的许多操作，linux可以使用一句命令搞定，比如`scp`可以将本地文件上传到远端某个目录，`rsync`可以同步本地和远端的目录，`git`操作命令等等，结合`zsh`等shell还有更加方便强大的提醒功能。

## 关于windows的软件代替

首先你必须知道的是，windows下的exe程序，在linux下是不能直接运行的（虽然有办法，但是不可靠），所以你基本可以放弃掉windows下的所有安装包了。

大多数你在windows下常用的软件，在linux下都能找到代替品，但是同时也要做好找不到代替品的心里准备，在许多情况下只会找到更加简陋的代替品。如果你不确定linux系统是否适合你，建议事先在网上寻找你日常必须使用的软件的linux版本或者是代替软件，再决定是不是要进入这个深坑。

以下是一些linux下的软件推荐：

- 浏览器： Chrome、FireFox
- 下载工具： Uget
- 编辑器： vscode、Atom、Sublime Text2/3、vim、gedit
- 翻译软件： 有道词典
- 办公软件： WPS
- 音乐： 网易云音乐
- 中文输入法： 搜狗拼音
- 聊天工具： QQ（Deepin下可用CrossOver运行，还算流畅；其他linux系统可使用Wine，简直蛋疼），微信网页版

**但是有两点一定要注意：**

1. linux下没有`微信开发者工具`，要么用实机调试，要么安装虚拟机（virtual box）

2. linux下没有`photoshop`，虽然有代替品`GIMP`，但是相差太远，常用切图设计慎入linux

## 预先了解一些linux常用命令

在linux下，你的绝大多数操作都会使用命令进行，刚开始都会觉得记不住，不好用，但是一旦你习惯了这种方式，你就会懒得动鼠标了。关于命令的学习方法，第一是多用，严禁直接copy命令（某些情况下时间紧急和为了防止写错除外）；第二是根据命令的缩写找回全称；根据全称来记忆，第三是学会百度谷歌。
