# TmuxConfigure
Tmux 自定义配置文件

# 重新定义Prefix，把默认的Ctr+b换成Ctr+a，便于单手操作 unbind C-b
set -g prefix C-a

# 重新定义Ctr+a，按下两次Ctr+a，就实现原有的Ctr+a功能
bind C-a send-prefix

# 定义新的快捷键，Prefix+r，重新加载Tmux配置文件
bind r source-file ~/.tmux.conf \; display "tmux.conf reload!"

# 重新定义分屏按键，垂直分屏Ctr+|，水平分屏Ctr+-
bind | split-window -h
bind - split-window -v

# 重新定义上下左右方向键
# bind h select-pane -L
# bind j select-pane -D
# bind k select-pane -U
# bind l select-pane -R

# 把window和pane的起始下标设为1，因为键盘的0在9后面，切换不方便
set -g base-index 1
set -g pane-base-index 1

# 启用鼠标
# set-window-option -g mode-mouse on
# 支持鼠标选择pane
# set -g mouse-select-pane on
# 支持鼠标调整pane大小
# set -g mouse-resize-pane on
# 支持鼠标选择window
# set -g mouse-select-window on

# UI样式调整
# 状态栏中window标签的高亮样式，默认绿底黑字，设置为红底白字显示
setw -g window-status-current-fg white
setw -g window-status-current-bg red
setw -g window-status-current-attr bright

# 状态栏中window列表左对齐排列
set -g status-justify left

# 非当前window有内容更新时显示在状态栏
setw -g monitor-activity on
