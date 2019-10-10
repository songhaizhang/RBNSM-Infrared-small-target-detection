**# 1. 必装插件
1. markdown preview enhance -- markdown预览工具
2. markdown all in one -- markdown必备工具之一
3. Bracket Pair Colorizer. 对括号对进行着色，再也不会搞不清状况了。
4. Path Intellisense. 智能路径提示
5. vscode icon. 文件图标

# 2. 个性化设置
## 1. 编辑器设置
### 1. 字体、行距等设置
工作空间使用 Noto serif CJK JP，markdown 预览使用方正轻刻本悦宋 FZQingKeBenYueSongS-R-GB，源代码使用 Fixedsys 字体（或者 Source Code Pro），终端显示字体为 Source Code Pro
> 以上字体在个人数据库中皆有备份

### 2. 自动保存设置
```xml
    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 300
```

## 2. 工作空间设置
### 1. python 设置
在使用 cv2 库时会标红提示无属性，在用户设置中添加如下代码：
```xml
 "python.linting.pylintArgs": ["--generate-members"]
```
### 2. cpp 设置
```xml
    "[cpp]": {
        "editor.quickSuggestions": false,
        "editor.fontFamily": "'Fixedsys Excelsior 3.01',  'Source Code Pro'",
        "editor.fontSize": 18,
        "editor.lineHeight": 22,
    },
```

# 3. **快捷键**
## 1. 编辑器相关
1. ctrl-shift-p 打开快速功能搜索
2. ctrl-b 开关左侧菜单树
3. ctrl-p 打开快速文件搜索

# 测试标题

#主命令框
F1 或 Ctrl+Shift+P : 打开命令面板。在打开的输入框内，可以输入任何命令，例如：

按一下 Backspace 会进入到 Ctrl+P 模式
在 Ctrl+P 下输入 > 可以进入 Ctrl+Shift+P 模式
在 Ctrl+P 窗口下还可以:
-直接输入文件名，跳转到文件
? 列出当前可执行的动作
! 显示 Errors或 Warnings，也可以 Ctrl+Shift+M
: 跳转到行数，也可以 Ctrl+G 直接进入
@ 跳转到 symbol（搜索变量或者函数），也可以 Ctrl+Shift+O 直接进入
@ 根据分类跳转 symbol，查找属性或函数，也可以 Ctrl+Shift+O 后输入:进入
根据名字查找 symbol，也可以 Ctrl+T
#常用快捷键
##编辑器与窗口管理
打开一个新窗口： Ctrl+Shift+N
关闭窗口： Ctrl+Shift+W
同时打开多个编辑器（查看多个文件）
新建文件 Ctrl+N
文件之间切换 Ctrl+Tab
切出一个新的编辑器（最多 3 个） Ctrl+\，也可以按住 Ctrl 鼠标点击 Explorer 里的文件名
左中右 3 个编辑器的快捷键 Ctrl+1 Ctrl+2 Ctrl+3
3 个编辑器之间循环切换 Ctrl+
编辑器换位置， Ctrl+k然后按 Left或 Right
#代码编辑
##格式调整
代码行缩进: Ctrl+[ 、 Ctrl+]
Ctrl+C 、 Ctrl+V 复制或剪切当前行/当前选中内容
代码格式化： Shift+Alt+F，或 Ctrl+Shift+P 后输入 format code
上下移动一行： Alt+Up 或 Alt+Down
向上向下复制一行： Shift+Alt+Up 或 Shift+Alt+Down
在当前行下边插入一行: Ctrl+Enter
在当前行上方插入一行 Ctrl+Shift+Enter
##光标相关
移动到行首： Home
移动到行尾： End
移动到文件结尾： Ctrl+End
移动到文件开头： Ctrl+Home
移动到定义处： F12
定义处缩略图：只看一眼而不跳转过去 Alt+F12
移动到后半个括号： Ctrl+Shift+]
选择从光标到行尾： Shift+End
选择从行首到光标处： Shift+Home
删除光标右侧的所有字： Ctrl+Delete
扩展/缩小选取范围： Shift+Alt+Left 和 Shift+Alt+Right
多行编辑(列编辑)：Alt+Shift+鼠标左键， Ctrl+Alt+Down/Up
同时选中所有匹配： Ctrl+Shift+L
Ctrl+D 下一个匹配的也被选中 (在 sublime 中是删除当前行，后面自定义快键键中，设置与 Ctrl+Shift+K 互换了)
回退上一个光标操作： Ctrl+U
选中所有匹配词批量编辑：鼠标高亮选中需要查找的词，按下 Ctrl + Shift + L键，即可快速选中当前文件中所有匹配的词，并在每一个词后面有一个编辑光标，可批量同步编辑
##重构代码
找到所有的引用： Shift+F12
同时修改本文件中所有匹配的： Ctrl+F12
重命名：比如要修改一个方法名，可以选中后按 F2，输入新名字，回车，则所有该方法的引用也都同步更新了
跳转到下一个 Error 或 Warning：当有多个错误时可以按 F8 逐个跳转
查看 diff： 在 explorer 里选择文件右键 Set file tocompare，然后需要对比的文件上右键选择 Compare with file_name_you_chose
查找替换
查找 Ctrl+F
查找替换 Ctrl+H
整个文件夹中查找 Ctrl+Shift+F
##显示相关
全屏：F11
zoomIn/zoomOut：Ctrl +/-
侧边栏显/隐： Ctrl+B
显示资源管理器 Ctrl+Shift+E
显示搜索 Ctrl+Shift+F
显示 Git Ctrl+Shift+G
显示 Debug Ctrl+Shift+D
显示 Output Ctrl+Shift+U
其他
自动保存：File -> AutoSave，或者 Ctrl+Shift+P，输入 auto

###打开终端:ctrl+**`**