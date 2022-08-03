---
title: vscode
date: 2022-07-31 22:54:50
categories: '效率工具'
cover: 'https://agileviet.vn/content/images/2020/12/1_cn_XBD307E3lObHk511Qqg.png'
---

## VSCODE是什么

---

VSCode（全称：Visual Studio Code）是一款由微软开发且跨平台的免费源代码编辑器。该软件支持语法高亮、代码自动补全（又称 IntelliSense）、代码重构、查看定义功能，并且内置了命令行工具和 Git 版本控制系统。用户可以更改主题和键盘快捷方式实现个性化设置，也可以通过内置的扩展程序商店安装扩展以拓展软件功能。<br />VS Code 使用 Monaco Editor 作为其底层的代码编辑器。

<a name="VXmJ4"></a>
## 官网指引

---

官网地址：[https://code.visualstudio.com/](https://code.visualstudio.com/)<br />文档地址：[https://code.visualstudio.com/docs](https://code.visualstudio.com/docs)
<a name="z4keK"></a>
## 安装

---

下载安装so easy 这里不对其过多解释<br />在 VScode 官网首页下载对应系统（支持Windows、Linux、macOS）的软件，下载页面： [https://code.visualstudio.com/download](https://code.visualstudio.com/download)  稳定版（Stable）

- 解压压缩包，打开可执行文件 点击NEXT
- 选中协议 点击NEXT
- 选择安装路径 直接使用默认 点击NEXT
- 注意安装路径 环境变量默认自动添加到系统中 勾选所有选中项 点击NEXT
- 点击install 完成安装

**界面说明**<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/1427114/1643247626731-59ffd3ab-0bea-4c2a-9ad0-a8035f8499f8.png#clientId=u94a38fce-139b-4&from=paste&id=ubea5d09b&margin=%5Bobject%20Object%5D&name=image.png&originHeight=977&originWidth=2560&originalType=url&ratio=1&size=611411&status=done&style=none&taskId=ub65601a1-5000-4130-82ce-3bea8ea9a0a)
<a name="pJr6d"></a>
## 插件

---

<a name="rKjnX"></a>
#### 美化系列
`chinese` 	汉化版本<br />`vscode-icons`	文件图标<br />`Material Icon Theme`	文件图标<br />`Atom One Dark Theme`	暗色主题<br />`Live Server`	实时预览<br />`Live Server Html`	编辑器开窗预览<br />`open in Brower`		用浏览器打开脚本文件<br />`A-super-tranlate`	画词翻译<br />`Beautify`	代码美化<br />`ESlint`		代码检查<br />`Prettier`	代码格式化<br />`Editconfig`		编码格式<br />`Bracket Pair Colorizer`		给匹配括号上色<br />`Markdown Preview Enhanced`	MarkDown编写预览
<a name="JzY1b"></a>
#### 效率系列
`vscode-intellij-recent-files`	快速在最近文件间切换<br />`Code Runner`	万能语言运行环境<br />`Debugger for Chrome`	调试工具<br />`Document this`	快速注释<br />`Code Spell Checker`		代码拼写检查<br />`TODO Highlight`		备忘插件<br />`Draw.io Integration`	图表工具<br />`easy-less`		编译less文件<br />`Turbo Console Log`		快速添加console.log信息
<a name="ilKkK"></a>
#### 布局样式系列
`IntelliSense for CSS class names in HTML` 	CSS类名提示<br />`Auto Close Tag`		自动添加闭合关闭标签<br />`HTML Snippets`		html代码片段<br />`Auto Rename Tag`	自动更改标签前后名<br />`Highlight Matching`		高亮匹配标签<br />`CSS Peek`	查看css定义
<a name="Kiuu4"></a>
#### 补充系列
`px to rem&rpx`  px转换
<a name="QmvSo"></a>
#### React系列
`JavaScript(ES6) code snippets`		es6代码片段 <br />`Reactjs code snippets`		 React组件片段<br />`Typescript React code snippets` 	tsx的React组件片段
<a name="F3kWo"></a>
#### 导入系列
`Import Cost` 	显示导入包大小<br />`Path Intellisence`	智能路径提示（例如html文件中需要导入样式脚本文件）<br />`npm Intellisense`	npm智能提示导入
<a name="jUuYd"></a>
#### Vue系列
`Vetur`	开发vue2支持插件<br />`volar`	开发vue3支持插件<br />`vueDX`	vue类型检测 重命名和重构
<a name="vCz0P"></a>
## 快捷键

---

<a name="HZ9I4"></a>
#### 系统热键
这是官方提供的 [快捷键速查表(opens new window)](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)，下面是中文快捷键说明。

| 按 Press | 功能 Function |
| --- | --- |
| Ctrl + Shift + P，F1 | 显示命令面板 Show Command Palette |
| Ctrl + P | 快速打开 Quick Open |
| Ctrl + Shift + N | 新窗口/实例 New window/instance |
| Ctrl + Shift + W | 关闭窗口/实例 Close window/instance |

<a name="PLgzr"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E5%9F%BA%E7%A1%80%E7%BC%96%E8%BE%91)基础编辑
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl+X | 剪切行（空选定） Cut line (empty selection) |
| Ctrl+C | 复制行（空选定）Copy line (empty selection) |
| Alt+ ↑ / ↓ | 向上/向下移动行 Move line up/down |
| Shift+Alt + ↓ / ↑ | 向上/向下复制行 Copy line up/down |
| Ctrl+Shift+K | 删除行 Delete line |
| Ctrl+Enter | 在下面插入行 Insert line below |
| Ctrl+Shift+Enter | 在上面插入行 Insert line above |
| Ctrl+Shift+\\ | 跳到匹配的括号 Jump to matching bracket |
| Ctrl+] / [ | 缩进/缩进行 Indent/outdent line |
| Home | 转到行首 Go to beginning of line |
| End | 转到行尾 Go to end of line |
| Ctrl+Home | 转到文件开头 Go to beginning of file |
| Ctrl+End | 转到文件末尾 Go to end of file |
| Ctrl+↑ / ↓ | 向上/向下滚动行 Scroll line up/down |
| Alt+PgUp / PgDown | 向上/向下滚动页面 Scroll page up/down |
| Ctrl+Shift+[ | 折叠（折叠）区域 Fold (collapse) region |
| Ctrl+Shift+] | 展开（未折叠）区域 Unfold (uncollapse) region |
| Ctrl+K Ctrl+[ | 折叠（未折叠）所有子区域 Fold (collapse) all subregions |
| Ctrl+K Ctrl+] | 展开（未折叠）所有子区域 Unfold (uncollapse) all subregions |
| Ctrl+K Ctrl+0 | 折叠（折叠）所有区域 Fold (collapse) all regions |
| Ctrl+K Ctrl+J | 展开（未折叠）所有区域 Unfold (uncollapse) all regions |
| Ctrl+K Ctrl+C | 添加行注释 Add line comment |
| Ctrl+K Ctrl+U | 删除行注释 Remove line comment |
| Ctrl+/ | 切换行注释 Toggle line comment |
| Shift+Alt+A | 切换块注释 Toggle block comment |
| Alt+Z | 切换换行 Toggle word wrap |
| Ctrl+Alt | 键盘上向上或者向下键，使一列上出现多个光标 |
| Ctrl+Shift+l | 选择相同的词统一编辑 |
| Shift+Alt+鼠标拖动 | 选择区域进行编辑 |

<a name="nHpd3"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E5%AF%BC%E8%88%AA%E6%8E%A7%E5%88%B6)导航控制
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl + T | 显示所有符号 Show all Symbols |
| Ctrl + G | 转到行... Go to Line... |
| Ctrl + P | 转到文件... Go to File... |
| Ctrl + Shift + O | 转到符号... Go to Symbol... |
| Ctrl + Shift + M | 显示问题面板 Show Problems panel |
| F8 | 转到下一个错误或警告 Go to next error or warning |
| Shift + F8 | 转到上一个错误或警告 Go to previous error or warning |
| Ctrl + Shift + Tab | 导航编辑器组历史记录 Navigate editor group history |
| Alt + ←/→ | 返回/前进 Go back / forward |
| Ctrl + M | 切换选项卡移动焦点 Toggle Tab moves focus |

<a name="BsYp3"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E6%90%9C%E7%B4%A2%E5%92%8C%E6%9B%BF%E6%8D%A2)搜索和替换
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl + F | 查找 Find |
| Ctrl + H | 替换 Replace |
| F3 / Shift + F3 | 查找下一个/上一个 Find next/previous |
| Alt + Enter | 选择查找匹配的所有出现 Select all occurences of Find match |
| Ctrl + D | 将选择添加到下一个查找匹配 Add selection to next Find match |
| Ctrl + K Ctrl + D | 将最后一个选择移至下一个查找匹配项 Move last selection to next Find match |
| Alt + C / R / W | 切换区分大小写/正则表达式/整个词 Toggle case-sensitive / regex / whole word |

<a name="imaLL"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E5%A4%9A%E5%85%89%E6%A0%87%E5%92%8C%E9%80%89%E6%8B%A9)多光标和选择
| 按 Press | 功能 Function |
| --- | --- |
| Alt +单击 | 插入光标 Insert cursor |
| Ctrl + Alt +↑/↓ | 在上/下插入光标 Insert cursor above / below |
| Ctrl + U | 撤消上一个光标操作 Undo last cursor operation |
| Shift + Alt + I | 在选定的每一行的末尾插入光标 Insert cursor at end of each line selected |
| Ctrl + I | 选择当前行 Select current line |
| Ctrl + Shift + L | 选择当前选择的所有出现 Select all occurrences of current selection |
| Ctrl + F2 | 选择当前字的所有出现 Select all occurrences of current word |
| Shift + Alt + → | 展开选择 Expand selection |
| Shift + Alt + ← | 缩小选择 Shrink selection |
| Shift + Alt + （拖动鼠标） | 列（框）选择 Column (box) selection |
| Ctrl + Shift + Alt +（箭头键） | 列（框）选择 Column (box) selection |
| Ctrl + Shift + Alt + PgUp / PgDown | 列（框）选择页上/下 Column (box) selection page up/down |
| zc | 折叠代码块 |
| zo | 展开代码块 |
| zC | 折叠所有代码块 |
| zO | 展开所有代码块 |

<a name="NaaOI"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E8%AF%AD%E8%A8%80%E7%BC%96%E8%BE%91)语言编辑
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl + 空格 | 触发建议 Trigger suggestion |
| Ctrl + Shift + Space | 触发器参数提示 Trigger parameter hints |
| Tab | Emmet 展开缩写 Emmet expand abbreviation |
| Shift + Alt + F | 格式化文档 Format document |
| Ctrl + K Ctrl + F | 格式选定区域 Format selection |
| F12 | 转到定义 Go to Definition |
| Alt + F12 | Peek定义 Peek Definition |
| Ctrl + K F12 | 打开定义到边 Open Definition to the side |
| Ctrl + . | 快速解决 Quick Fix |
| Shift + F12 | 显示引用 Show References |
| F2 | 重命名符号 Rename Symbol |
| Ctrl + Shift + . /， | 替换为下一个/上一个值 Replace with next/previous value |
| Ctrl + K Ctrl + X | 修剪尾随空格 Trim trailing whitespace |
| Ctrl + K M | 更改文件语言 Change file language |

<a name="ZaDNK"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E7%AA%97%E5%8F%A3%E7%AE%A1%E7%90%86)窗口管理
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl+F4, Ctrl+W | 关闭编辑器 Close editor |
| Ctrl+K F | 关闭文件夹 Close folder |
| Ctrl+\\ | 拆分编辑器 Split editor |
| Ctrl+ 1 / 2 / 3 | 聚焦到第1，第2或第3编辑器组 Focus into 1st, 2nd or 3rd editor group |
| Ctrl+K Ctrl+ ←/→ | 聚焦到上一个/下一个编辑器组 Focus into previous/next editor group |
| Ctrl+Shift+PgUp / PgDown | 向左/向右移动编辑器 Move editor left/right |
| Ctrl+K ← / → | 移动活动编辑器组 Move active editor group |

<a name="lthFG"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E6%96%87%E4%BB%B6%E7%AE%A1%E7%90%86)文件管理
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl+N | 新文件 New File |
| Ctrl+O | 打开文件... Open File... |
| Ctrl+S | 保存 Save |
| Ctrl+Shift+S | 另存为... Save As... |
| Ctrl+K S | 全部保存 Save All |
| Ctrl+F4 | 关闭 Close |
| Ctrl+K Ctrl+W | 关闭所有 Close All |
| Ctrl+Shift+T | 重新打开关闭的编辑器 Reopen closed editor |
| Ctrl+K | 输入保持打开 Enter Keep Open |
| Ctrl+Tab | 打开下一个 Open next |
| Ctrl+Shift+Tab | 打开上一个 Open previous |
| Ctrl+K P | 复制活动文件的路径 Copy path of active file |
| Ctrl+K R | 显示资源管理器中的活动文件 Reveal active file in Explorer |
| Ctrl+K O | 显示新窗口/实例中的活动文件 Show active file in new window/instance |

<a name="DG23k"></a>
#### [ ](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E6%98%BE%E7%A4%BA%E6%8E%A7%E5%88%B6)显示控制
| 按 Press | 功能 Function |
| --- | --- |
| F11 | 切换全屏 Toggle full screen |
| Shift+Alt+1 | 切换编辑器布局 Toggle editor layout |
| Ctrl+ = / - | 放大/缩小 Zoom in/out |
| Ctrl+B | 切换侧栏可见性 Toggle Sidebar visibility |
| Ctrl+Shift+E | 显示浏览器/切换焦点 Show Explorer / Toggle focus |
| Ctrl+Shift+F | 显示搜索 Show Search |
| Ctrl+Shift+G | 显示Git Show Git |
| Ctrl+Shift+D | 显示调试 Show Debug |
| Ctrl+Shift+X | 显示扩展 Show Extensions |
| Ctrl+Shift+H | 替换文件 Replace in files |
| Ctrl+Shift+J | 切换搜索详细信息 Toggle Search details |
| Ctrl+Shift+C | 打开新命令提示符/终端 Open new command prompt/terminal |
| Ctrl+Shift+U | 显示输出面板 Show Output panel |
| Ctrl+Shift+V | 切换Markdown预览 Toggle Markdown preview |
| Ctrl+K V | 从旁边打开Markdown预览 Open Markdown preview to the side |

<a name="JpIxB"></a>
#### 代码调试
| 按 Press | 功能 Function |
| --- | --- |
| F9 | 切换断点 Toggle breakpoint |
| F5 | 开始/继续 Start/Continue |
| Shift+F5 | 停止 Stop |
| F11 / Shift+F11 | 下一步/上一步 Step into/out |
| F10 | 跳过 Step over |
| Ctrl+K Ctrl+I | 显示悬停 Show hover |

<a name="ET2cM"></a>
#### 集成终端
| 按 Press | 功能 Function |
| --- | --- |
| Ctrl+` | 显示集成终端 Show integrated terminal |
| Ctrl+Shift+` | 创建新终端 Create new terminal |
| Ctrl+Shift+C | 复制选定 Copy selection |
| Ctrl+Shift+V | 粘贴到活动端子 Paste into active terminal |
| Ctrl+↑ / ↓ | 向上/向下滚动 Scroll up/down |
| Shift+PgUp / PgDown | 向上/向下滚动页面 Scroll page up/down |
| Ctrl+Home / End | 滚动到顶部/底部 Scroll to top/bottom |


<a name="bOelZ"></a>
## 调试

---


<a name="Dr27T"></a>
## 配置

---




更多调试配置项查看：<br />[https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html %E4%B8%AD%E6%96%87%E8%AF%AD%E8%A8%80](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E4%B8%AD%E6%96%87%E8%AF%AD%E8%A8%80)
<a name="Phzoy"></a>
## 相关网站

---

[https://vscode.cool/](https://vscode.cool/)<br />[https://cloud.tencent.com/developer/article/1796162](https://cloud.tencent.com/developer/article/1796162) *<br />[https://www.php.cn/tool/vscode/](https://www.php.cn/tool/vscode/)  *<br />[https://aijishu.com/a/1060000000094032](https://aijishu.com/a/1060000000094032)<br />[https://www.runoob.com/w3cnote/vscode-tutorial.html](https://www.runoob.com/w3cnote/vscode-tutorial.html)<br />[https://www.axihe.com/tools/vscode/skill/vscode-add-code-comments.html](https://www.axihe.com/tools/vscode/skill/vscode-add-code-comments.html) *<br />[https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html %E4%B8%AD%E6%96%87%E8%AF%AD%E8%A8%80](https://doc.houdunren.com/vscode/1%20%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.html#%E4%B8%AD%E6%96%87%E8%AF%AD%E8%A8%80)

