# 安装atom

1、下载deb包并安装（[官网](https://atom.io)或[国内镜像](https://cnpmjs.org/mirrors/atom)）

2、配置插件下镜像地址
  插件多次下载都不成功，可以尝试此方法。
  ```bash
  # 打开atom配置文件.apmrc，没有则创建
  $ sudo gedit ~/.atom/.apmrc
  # 添加以下语句
  registry = https://registry.npm.taobao.org
  ```
3、node/vue开发推荐插件

- sync-settings：使用gist备份atom插件、配置、代码段等
- block-comment：块注释插件
- double-click-tree-view：默认文件树是单击选择，加这个插件之后变成双击选择，看个人使用习惯
- activate-power-mode：写代码粒子效果
- linter/linter-eslint：两个插件一起装，代码规范插件
- language-babel：es201x语法
- language-vue：vue插件
- vue-autocomplete：vue提示
- autocomplete-modules：输入require/import时的提示
- atom-ternjs：js语法提示集合
- docblockr：生成注释文档
- emmet：快速写html
- file-icons：文件图标
- higlight-selected：双击选择代码时高亮
- minimap：预览滚动条
- minimap-higlight-selected：预览滚动条高亮显示选择的代码
- pigments：显示颜色