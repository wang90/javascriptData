### brew
``````
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
``````
### 修改应用图标命令
- 调整每一列显示图标数量，7 表示每一列显示7个
```````
defaults write com.apple.dock springboard-rows -int 7
```````
- 调整每一行显示图标数量，这里我用的是8
```````
defaults write com.apple.dock springboard-columns -int 8
```````
- 由于修改了每一页显示图标数量，可能需要重置Launchpad
```````
defaults write com.apple.dock ResetLaunchPad -bool TRUE;killall Dock
```````
