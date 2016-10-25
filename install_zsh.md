# 安装zsh和oh my zsh
1、安装zsh

```bash
# 查看自带shell
$ cat /etc/shells
# 下载并安装zsh
$ sudo apt-get install zsh
# 替换原shell
$ chsh -s /bin/zsh
```

2、通过git安装oh my zsh（[官网](http://ohmyz.sh/)）
```bash
$ git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
$ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

3、配置主题
[官方主题列表及预览](https://github.com/robbyrussell/oh-my-zsh/wiki/themes)
```bash
$ gedit ~/.zshrc
```
找到并修改ZSH_THEME
```
# 默认主题
ZSH_THEME=”robbyrussell”
# 个人推荐
ZSH_THEME=ys
```

4、配置命令别名
```bash
$ gedit ~/.zshrc
```

最下面加上

```
alias cls='clear'
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias grep="grep --color=auto"
alias -s html=code   # 在命令行直接输入后缀为 html 的文件名，会在vscode中打开
alias -s js=code
alias -s css=code
alias -s txt=gedit
alias -s gz='tar -xzvf'
alias -s tgz='tar -xzvf'
alias -s zip='unzip'
alias -s bz2='tar -xjvf'
```

5、配置插件

 官方插件[列表](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins)

```bash
$ gedit ~/.zshrc
```

找到并编辑plugins，添加插件到括号内，空格隔开
```
plugins=(git autojump npm zsh-syntax-highlighting sudo)
```

推荐插件（如无安装说明，添加即可使用）：
1) git：显示当前目录git状态、分支、简化git命令，例如gco=’git checkout’、gd=’git diff’、gst=’git status’、g=’git’等等
2) autojump：输入常用目录名可实现快速跳转，如`j soft`，可以快速跳转到`/xxx/xxx/software`
```bash
# 安装autojump
# 通过git下载最新autojump
$ git clone git://github.com/joelthelion/autojump.git
# 安装
cd autojump
./install.py
# 添加到.zshrc的plugins中
$ gedit ~/.zshrc
# 添加以下代码到.zshrc中
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh
```
3) npm：npm命令提示
4) fasd：功能类似autojump，据说更强大，二选一，安装说明看[官网](https://github.com/clvv/fasd)
5) zsh-syntax-highlighting：判断命令是否正确，绿色正确，红色错误
```bash
# 安装zsh-syntax-highlighting
$ git clone git://github.com/jimmijj/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
# 添加到~/.zshrc的plugins中
plugins=(zsh-syntax-highlighting)
```
6)sudo：按两下esc快速添加sudo到上一条命令