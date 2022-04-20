# 玩转 Mac

### Terminal
- 不要进入休眠状态

在终端中输入 `caffeinate`，取消的话可以输入 `control + C` 指令

- 重置程序坞与状态栏

将程序栏恢复为电脑刚刚激活时的状态，输入指令 `defaults delete com.apple.dock; killall Dock`

- 程序坞添加空白分解符

输入指令：`defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'; killall Dock`

如需删除，则直接拖拉删除即可

- Terminal 里的命令如果错误的话，直接打 fuck，这个项目就会自动帮帮你修改，然后执行

  比如你打 `apt-get install XXX`
  
  然后提示 `permission denied`
  
  这个时候执行 `fuck`
  
  就会自动帮你执行 `sudo apt-get`
