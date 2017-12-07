# Tmux 相关笔记

### Tmux 安装

```
$ sudo apt install tmux
```

### Tmux 基础命令
**Session**
```
// 新建Session
$ tmux new -s <session_name>

// 退出Session
快捷键 ctrl+b， d

// 杀死Session
$ tmux kill-session -t <session_name>

// 查看已有的Session
$ tmux ls

// 进入某个Session
$ tmux a -t <session_name>

// 在Session间切换
首先， 进入一个Session
然后， 快捷键 ctrl+b, s
最后， 使用上下箭头选择Session， 回车进入
```
**Window**

```
// 新建窗口
快捷键 ctrl+b, c

// 关闭当前窗口, 会关闭所有panel
快捷键 ctrl+b, &

// 切换到上一个窗口
快捷键 ctrl+b, p

// 切换到下一个窗口
快捷键 ctrl+b, n

// 切换到编号为 <num> 的窗口
快捷键 ctrl+b, <num>
```

**Panel**

```
// 左右panel
快捷键 ctrl+b, %

// 上下panel
快捷键 ctrl+b, "

// 关闭当前panel
快捷键 ctrl+b, x

// panel间切换
快捷键 ctrl+b, ↑、↓、←、→
```

### Tmux 配置文件

```
$ vim ~/.tmux.conf
```

```
# 把 ctrl+b 前缀快捷键改为 ctrl+a， 方便单手操作
set-option -g prefix C-a
unbind-key C-b

# 按两次 ctrl+a 执行原意ctrl+a
bind-key C-a send-prefix

# 按住 alt 键， 使用箭头控制panel选择
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# 按住 shift 键， 使用箭头控制 window 选择
bind -n S-Left previous-window
bind -n S-Right next-window

# 开启鼠标支持， 使用鼠标直接选择 window 和 panel， 以及调整 panel 大小
set -g mode-mouse on
set -g mouse-resize-pane on
set -g mouse-select-pane on
set -g mouse-select-window on

# 前缀+v， 左右分屏， 前缀+h， 上下分屏
bind-key v split-window -h
bind-key h split-window -v

# Session内直接按前缀+r， 重新加载配置文件
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"

# 把window和pane的起始下标设为1，因为键盘的0在9后面，切换不方便
set -g base-index 1
set -g pane-base-index 1

# UI样式调整
# 状态栏中window标签的高亮样式，默认绿底黑字，设置为红底白字显示
setw -g window-status-current-fg white
setw -g window-status-current-bg red
setw -g window-status-current-attr bright

# 状态栏中window列表左对齐排列
set -g status-justify left

# 非当前window有内容更新时显示在状态栏
setw -g monitor-activity on
```

