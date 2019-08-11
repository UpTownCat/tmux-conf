# Tmux

## 介绍
Tmux是一个终端会话工具，它可以永久保存会话的状态。在一个会话可以创建多个窗口，一个窗口又可以创建多个栅格，栅格的大小随意调整。
![tmux](https://github.com/UpTownCat/tmux-conf/blob/master/tmux.png)
## 常用命令
    Tmux输入命令的时候需要使用前缀，默认前缀是Ctrl+b，如果设置了vi模式会和翻页快捷键冲突，建议使用Ctrl+z作为命令前缀。
### 基本命令
- tmux new -s test_session: 新建session
- tmux a -t test_sesion: 进入test_session
- tmux source-file ~/.tmux.conf: 加载配置文件([我的配置文件](https://github.com/UpTownCat/tmux-conf/blob/master/.tmux.conf))
- tmux ls: 列出所有session
### 会话管理
- prefix + d: 离开当前session
- prefix + s: 列出session
- prefix + $: 重命名session
### 窗口管理
- prefix + c: 创建window
- prefix + ,: 重命名window
- prefix + p: 切换前一个window
- prefix + n: 切换后一个window
### 栅格管理
- prefix + ": 竖直方向创建pane
- prefix + %: 水平方向创建pane
- prefix + h: 移动到左边的pane
- prefix + j: 移动到上边的pane
- prefix + k: 移动到下边的pane
- prefix + l: 移动到右边的pane
- prefix + z: 当前pane最大化或恢复原来大小
- prefix + q: 显示pane的编号，输入编号将会切换到对应的pane
- prefix + t: 显示时钟
- prefix + x: 强行退出pane

`正常情况下使用Ctrl + d或者exit就可以退出pane`
### 插件管理
- tmux-tpm是一个插件管理工具，使用它可以更加方便地安装和管理插件。
    1. git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
    2. 在配置文件加入这些内容
    ``` 
        set -g @plugin 'tmux-plugins/tpm'
        set -g @plugin 'tmux-plugins/tmux-sensible'

        # Other examples:
        # set -g @plugin 'github_username/plugin_name'
        # set -g @plugin 'git@github.com/user/plugin'
        # set -g @plugin 'git@bitbucket.com/user/plugin'
        # Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
        run -b '~/.tmux/plugins/tpm/tpm'
    ```
    3. tmux source-file ~/.tmux.conf
    4. 安装新插件时在配置加一行，再更新配置文件就行了
                            
    ` set -g @plugin 'git@bitbucket.com/user/plugin `
- tmux-sensible: 常用的配置
- tmux-resurrect: 恢复tmux状态
- tmux-continuum: 自动保存tmux状态，关机之后可以恢复
- tmux-copycat: 正则搜索和快速匹配
- tmux-yank: 复制高亮内容到剪贴板
- tmux-open: 快速打开高亮文件或者url
- tmux-pain-control: 控制pane的插件
- tmux-prefix-highlight: 输入前缀高亮提示
- tmux-colors-solarized: 颜色主题
## 总结
- 持久化session，断网也可以再次恢复到原来的状态
- 设置vi模式之后可以使用vim的方式控制屏幕的滚动，也可以进行复制和粘贴内容
- 同时在一个session里运行多个任务，不像平常的session只能运行一个任务
