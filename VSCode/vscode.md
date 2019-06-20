# VSCode

**03 | 如何快速上手VS Code?**



下载安装 VS Code 

- Stable 稳定版本

- Insiders “吃自己的狗粮”（eat your own dog food）

- - 尽早使用最新版本的功能
  - 深度参与 VS Code 开发过程



**“欢迎使用”页面**，首次启动 VS Code 

- 最近打开的文件、文件夹

- 快捷键速查表

- **学习**

- - 命令面板（**CTRL + SHIFT + P | F1**）：可快速搜索命令并执行，简体中文版下，可使用中英文关键字 → **摆脱鼠标的一大利器**。
  - 界面预览：工作区的几个快捷键
  - 交互演示场：高级代码编辑功能场景化学习

- 终端：CTRL + ` 调出、CTRL + L 清空终端（cls OR clear）



**最基础命令行的使用：**配置 VS Code 安装目录到 PATH 环境变量

- *code -help*
- *code 文件|文件夹路径*：打开一个新的 VS Code 窗口
- *code -r 文件|文件夹路径*：重用当前 VS Code 窗口
- *code -r -g pom.xml:38* ：打开 pom.xml ，并定位到 38 行
- *code -r -d a.txt b.txt* ：比较 a.txt、b.txt 文件差异 
- *echo Hello World | code* *-* ：接收管道中的数据，展示在 VS Code 中编辑



**命令行高阶用法**

- **插件****管理**
- **行为定制**
- **运行性能监控**
- **e.g.：--disable-extensions、--max-memory**
- **e.g.：通过创建别名（alias）配置自己的 code 命令**



**PowerShell 中文乱码问题**

- **$OutputEncoding 默认使用 US-ASCII 编码**
- **$OutputEncoding = New-Object -typename System.Text.UTF8Encoding**
- **$OutputEncoding = New-Object -typename System.Text.ASCIIEncoding**



------



**04 | 如何做到双手不离键盘？**



双手不离键盘（后面有**快捷键插件的开发**哦），核心的键盘操作：

- 光标的移动
- 文本的选择
- 文本的删除
- 如何为编辑器命令绑定快捷键



1、光标的移动

- 字符颗粒度：默认通过方向键移动光标，光标的移动颗粒度是字符。
- 单词颗粒度：CTRL 加方向键，光标的移动颗粒度就是单词。CTRL + 左方向键，向左移动一个单词，右方向键则是向右移动一个单词
- 行颗粒度：HOME、END 可移动光标到行首、行尾
- 代码块（括号）颗粒度：CTRL + SHIFT + \ 实现在代码块的始末跳转，小括号的跳转也可以
- 文档颗粒度：CTRL + HOME、CTRL + END 光标移动到文档的第一行、最后一行



2、文本的选择

- 基于单词、行、整个文档的光标操作，只需要多加一个 SHIFT，即可在移动光标的同时选中文本。

- 代码块的文本选择，VS Code 默认没有绑定快捷键。

- - CTRL + SHIFT + P 调用命令面板，运行“选择括号所有内容（Select）”，也可自定义自己的快捷键。
  - CTRL + SHIFT + ] 选择最近的代码块（不知为何来的快捷键）



3、文本的删除

- 基于文本选择，使用 DELETE or BACKSPACE 删除键删除。
- 删除光标左右两侧的字符：Windows上未绑定快捷键，命令面板运行 “删除右侧所有内容（Delete）”、“删除左侧所有内容（Delete）”





4、自定义快捷键

- 命令面板，搜索“打开键盘快捷方式（Open Keyboard | o key） ”，通过命令、快捷键进行搜索，即可修改或绑定指定按键。
- e.g.：搜索“选择括号内所有内容”，双击\ENTER键，按下“CTRL + SHIFT + ]”，按下回车键，按键绑定完成。



自定义快捷键的优先级 > 默认配置：CTRL + SHIFT + ] 默认是展开代码块，自定义为“选择...” 之后，快捷键展开无效。



------



**05 | 快捷键进阶攻略**



软件开发一个非常流行的原则：不要重复自己（Don't Repeat Yourself!），代码的编辑也是如此。



5、代码行编辑

- 删除代码行

- - 行颗粒度选中 + DELETE、BACKSPACE。
  - CTRL + SHIFT + K ，删除光标所在行，多光标时，可删除多行（默认该快捷键被系统占用）。
  - CTRL + X、CTRL + C、CTRL + V、CTRL + Z



- 添加代码行

- - ENTER 光标位置
  - CTRL + ENTER 行上
  - CTRL + SHIFT + ENTER 行下



- 移动代码行

- - ALT + 上下方向键，移动光标位置所在行
  - ALT + SHIFT + 上下方向键，复制光标位置所在行



6、编辑语言相关的命令

- 注释：VS Code 可根据文本类型添加适合文本的注释（JS // CSS /**/）

- - CTRL + / 按代码行注释
  - ALT + SHIFT + A 注释掉选中的代码

​            偶数次按键取消注释



- 格式化：VS Code 可根据文本类型实现针对性格式化，**前提**是安装了相应插件

- - ALT + SHIFT + F 格式化整个文档
  - CTRL + K CTRL + F 格式化选中代码



- 代码缩进

- - 命令面板，运行“重新缩进所选行（Reindent | re line）”、“重新缩进行”即可



- 语言模式

- - 命令面板，搜索“更改语言模式（Change Language **Mode**）”，可更改编辑器文件的语言模式，从而获得对应编程语言的语法高亮和动态提示
  - CTRL + K， M（language **M**ode）



7、其他几个小技巧：来源于社区开发者的几个未绑定快捷键的命令

- 调换字符位置，运行“转置光标处的字符（Transpose | Letters）”，光标前后字符互换位置
- 调整字符大小写，运行“转换为大写（Uppercase）”、“转换为小写（Lowercase）”、“转换为词首字母大写（Titlecase）”
- 合并行，运行“合并行（Join Lines）”，合并选择内容 or 合并光标后内容到光标所在代码行
- 行排序，运行“按降序排序（Sort）”、“按升序排序（Sort）”，排序选择的代码行
- CTRL + U：撤销光标上一次的移动





命令面板的命令搜索，可使用中文、英文关键词（关键字部分字符）搜索：“删除 Delete”、“右侧 Right”、“大写 Uppercase”、“小写 Lowercase”、“合并 Join | Merge”、“括号 Brackets”、“缩进 Indent”、“重新缩进 Reindent”、“转置 Transpose”等等



------



**06 | 拒绝重复，你一定要学会的多光标特性**





9、创建多光标

- ALT + 鼠标点击
- CTRL + ALT + 上下方向键，在当前光标正上下方创建光标



- CTRL + D 第一次按下时，选中光标附近的单词并选中，之后按下时，找到该单词第二次出现的位置，选中并在单词后创建光标。用于处理多次出现的相同单词。
- CTRL + D CTRL + K 跳过当前选择
- ALT + SHIFT + I 代码行的批处理，在选择的代码行后创建光标



**多光标移动**可基于字符（移动光标）、单词（CTRL + 移动光标）、代码行（HOME、END）、代码块（CTRL + SHIFT + \）等。退出多光标模式 **ESC**



**使用这样的功能的时候，你可以想想如果你是设计者，你会怎么样来设计多光标特性。闭着眼睛顺着这个路径思考，也许你会更容易理解和记住 VS Code 的模式。**



------



**07 | 如何快速在文件、符号、代码之间跳转？**



10、文件跳转

- CTRL + TAB 在已打开的文件列表中跳转
- CTRL + P 搜索最近打开的文件列表（更加常用），ENTER 在当前编辑窗口打开文件，CTRL + ENTER 在新的编辑窗口打开



11、行跳转

- CTRL + G ，在 : 后输入行号，即可跳转到正在编辑的文件的指定行
- CTRL + P + 完整文件名 : 行号，跳转到指定**已打开**文件的指定行



12、符号（Symbols）跳转：同格式化一样，依赖插件 go-symbols

- CTRL + SHIFT + O：调出**当前**文件的符号，可在标识符（类定义、函数定义等）之间跳转

- - @ + 文件名 | @ + 上下方向键
  - @**:** 可将文件符号分类

- CTRL + T 可在不同文件之中的符号之间跳转：**#**



13、定义（Definitions）和实现（Implementations）跳转

- CTRL + 鼠标左键点击、F12 跳转到函数、类等符号的**定义**位置

- CTRL + F12 跳转到接口等符号的实现位置

- - 没有实现的话，提示未找到实现位置
  - JavaScript 中没有接口（Interface）概念，定义和实现恰好是相同

- CTRL + ALT +  鼠标左键点击，在侧边栏中重新打开



14、引用（Reference）跳转

- SHIFT + F12 跳转到引用到符号定义的位置



15、CTRL + P 命令面板：输入框中输入不同的英文符号，实现不同的命令

- \> 等价于 CTRL + SHIFT + P 
- : 等价于 CTRL + G
- @ 等价于 CTRL + SHIFT + O
- @:
- \# 等价于 CTRL + T



------



**08 | 玩转鼠标操作**



1、文本选择

- “一点、二拖、三松手” 实现文本选择

- - 文件以字符为颗粒度
  - 拖动行号栏，选中指定代码行

- 鼠标左键四点击：单击移光标，双击选单词，三击当前行，四击全文档



2、文本编辑：拖放（Drog and Drop）功能

- 将鼠标放置在选择的文本上，按住左键，光标变成小箭头，拖拽，当光标变成虚线且到达目标位置，松开鼠标，即可实现 “剪切 + 粘贴”；拖拽鼠标时，结合 CTRL 键，可实现 “复制 + 粘贴”
- 上述操作，对于行号栏有效



3、多光标

- ALT + 鼠标左键，哪里需要点哪里，创建多光标
- 按住鼠标中键，对着一段文本拖出一个框，松开中键，框中代码被选中且代码所在行拥有独立光标



4、悬停提示窗口

- 鼠标移动到文本上，稍等片刻，出现提示窗口，包含文本描述
- 结合 CTRL 键，悬停窗口将显示标识符号定义的代码



5、代码跳转和链接

- Ctrl + 鼠标左键 到达定义处或者打开超链接



------



**09 | 编程语言支持功能：代码自动补全、快速修复和重构**



VS Code 为编程语言工作者提供了统一的 API ，即 Language Server Protocol，每种语言都能通过实现这个 API，在 VS Code 上得到类似 IDE 上的开发体验。各种语言通过这个 API 实现的服务，被称为**语言服务**。代码自动补全、快速修复、重构都依托于语言服务来提供内容。



1、VS Code 中自动代码补全



语言服务会根据当前的项目、当前的文件、以及光标所在位置，为我们提供一个建议列表。

- ESC：隐藏建议列表
- CTRL + SPACE：调出建议列表（Windows 上失效）

支持关键字模糊搜索（console.db 建议窗口提示 **d**e**b**ug）



快速预览：函数等建议列表项最右侧蓝色图标，点击即可紧靠建议窗口展示一个快速预览窗口（显示标识符的定义）

- CTRL + SPACE：调出快速预览（Windows 上失效）



参数预览：函数调用时，左侧小括号将触发参数预览窗口显示。光标在小括号中间，**CTRL + SHIFT + SPACE** 可再次调出参数预览窗口。



自动补全相关设置

- 自动补全窗口唤出设置

```json
"editor.quickSuggestions": {
    "other": true,
    "comments": false,
    "strings": false
}
"editor.quickSuggestionsDelay": 10
```

- 参数预览窗口唤出设置

```json
"editor.parameterHints.enabled": true
```



2、快速修复（Quick Fix）

触发快速修复的黄色灯泡图标：**光标移动到指定代码中时才会展示（铁律）**

- 命令面板，搜索 “Fix or 快速修复” 等可触发，但只能逐个修复
- 点击触发快速修复建议列表
- CTRL + .：调出快速修复建议列表（Windows 失效）



3、重构：**光标移动到指定代码中（铁律）**

- F2：重命名所有已打开文件中的标识符（函数、类、接口等）
- 选择一段代码，快速修复，将其抽取



基于单词的自动提示



编辑器通过分析当前的文件里的内容，进行简单的正则表达式匹配，给我们建议已经出现过的单词。如果觉得语言服务的提示足够好，不需要这么暴力、这么笨的文本提示，那你也可以通过设置 "editor.wordBasedSuggestions" 将其关闭。



------



**10 | 拒绝重复，你的代码百宝箱：如何书写 code snippet？**



代码片段（Code Snippets）：命令面板，搜索“配置用户代码片段”（Configure User Sinppets）执行。

![img](file:///C:/Users/Joian/AppData/Local/Temp/enhtmlclip/Image.png)![img](data:image/png;base64,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)

 

```json
{
    "Print to console": {
        "prefix": "log",
            "body": [
            "console.log('$1');",
            "$2"
        ],
        "description": "Log output to console"
    }
}
```

其中，自定义代码片段的键 Key （"Print to console"）需要保证唯一性，值 Value 中 prefix 和 body 是必须的，description 不是必须的。prefix 是触发关键字，输入 log 即可触发自动补全建议列表，若 description 存在，将展示在快速预览窗口中。



**Tab Stop：Tab按下时，光标可停留的位置。$1、$2即是 Tab Stop**

- Tab：跳转到下一个 Tab Stop
- SHIFT + Tab：跳转到上一个 Tab Stop
- 预设置Tab Stop和其**占位符：‘**${1:label}’、${1:i}
- ESC：退出编辑
- 多光标：相同 Tab Stop（$1、$2 等），使用代码片段时，可在占位符后（'label'、i 等）出多光标



预设变量：除了使用固定字符串的占位符，还可以使用当前上下文中内容。

- e.g.：使用剪切板中内容填充 ${1:$CLIPBOARD}



**更多内容：** <https://code.visualstudio.com/docs/editor/userdefinedsnippets#_variables>



VS Code 的代码片段语法是基于 TextMate 的，不仅 VS Code，Atom 和 Sublime 也都支持这个语法，你可以在网上找些其他人分享的代码片段，通过阅读这些他人书写的代码片段来学习和精进，相信这也会是你一个不错的学习途径。



自问自答一下，我套用了vim配置管理的方法，将snippets的文件在一个github仓库中管理，然后`ln -s`软连接到Code/User/snippets目录下面，虽然麻烦一点，不过可以在机器间同步，另外用户配置和插件配置通过一个叫`settings sync`的插件通过gist可以直接同步。



------



**11 | 一定要用好代码折叠、小地图和面包屑特性**



1、代码折叠



- 命令面板：搜索“折叠（Fold）、展开（Unfold）”，折叠、展开光标所在最内层代码块

- - CTRL + SHIFT + [ 、CTRL + SHIFT + ]

- 命令面板，搜索“以递归方式折叠、展开”，以光标所在位置开始，向上递归折叠、展开

- - CTRL + K CTRL + [
  - CTRL + K CTRL + ]

- 命令面板，搜索“全部折叠、展开”，折叠、展开所有可操作代码

- - CTRL + K CTRL + 0
  - CTRL + K CTRL + J



命令面板，搜索：“折叠级别”，折叠级别 1、2、3 等

- 作用：按照代码块层级，从外到内，对应级别从 1 开始，当进行代码块指定级别的折叠时，具有相同层级的代码块在指定层级上进行折叠
- 应用场景：阅读代码
- CTRL + K、CTRL + 1、2、3 等



基于语言定义的代码折叠

- Java: //#region and // #endregion and //<editor-fold> and //</editor-fold>



官方文档：<https://code.visualstudio.com/docs/editor/codebasics#_folding>



2、小地图（Minimap）：命令面板，搜索“打开设置（Open Settings）”

- "editor.minimap.renderCharacters": false，使用小色快而不是字符展示小地图
- "editor.minimap.enabled": false，指定是否启用小地图
- 更多其他操作...



3、面包屑（Bread Crumbs）：命令面板，搜索“打开设置（Open Settings）”

- "breadcrumbs.enabled": true，默认面包屑功能关闭，可打开



技术细节上，面包屑这个功能除了 UI 部分，它底层的服务其实都是早就存在的。

- 面包屑左侧的文件结构，来自资源管理器；
- 右侧的函数名之类的，则是来自语言服务提供的符号；
- 至于在这些文件和符号之间的快速跳转，可以当作一种新的文件、内容预览和快速跳转的方式。



------



**12 | 极速搜索有时候比 Intellisense 还重要**



单文件搜索、替换：光标所在字符串作为搜索关键字

- ESC：退出搜索

- CTRL + F：搜索后，光标在搜索框，使用 Enter 、SHIFT + Enter 从当前位置向下或者向上搜索

- F3：搜索后，光标在文件中关键字后，方便编辑，使用 F3、SHIFT + F3 从当前位置向下或者向上搜索

- 搜索框后![img](file:///C:/Users/Joian/AppData/Local/Temp/enhtmlclip/Image(1).png)![img](data:image/png;base64,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)

- - 第一个是大小写敏感，点击或 ALT + **C** ase开启或关闭，默认关闭

  - 第二个是全单词匹配，点击或 ALT + **W** ord 开启或关闭，默认关闭 

  - 第三个是正则表达式匹配（Javascript 正则引擎），点击或 ALT + **R** egular  Expression，默认关闭

  - 倒数第二个是是否在选中区域搜索，点击或者 ALT + L，默认关闭

  - 第一个小箭头是替换，点击或 CTRL + H

  - - 可单一替换，也可全文替换
    - 使用 Enter ，可逐一替换
    -  Tab、SHIFT + Tab or CTRL + F 、CTRL + H 在搜索模式和替换模式切换，配合 Enter，针对性替换



搜索设置

- "editor.find.seedSearchStringFromSelection": true，是否将选中内容作为搜索词
- "editor.find.autoFindInSelection": true，是否在选中内容中搜索，默认是全文



多文件搜索、替换：默认在当前打开的文件下搜索

- CTRL + SHIFT + F
- CTRL + SHIFT + H
- 可通过“要包含的文件”、“排除的文件”进行过滤，使用 glob 书写格式来模糊匹配



多文件搜索设置

- "search.location": "panel"，将搜索框锁定在下方，使用更大面板展示
- "search.collapseResults": "alwaysExpand"，搜索结果过多时，默认是折叠的，推荐总是展开



glob 书写格式语法



------



**13 | 优化你的编辑器设置**



编辑器看起来怎么样？

- "editor.lineNumbers": "relative"，行号显示为与光标相隔的行号
- "editor.renderWhitespace": "all"，用灰色的“点”渲染空格符、制表符
- "editor.renderIndentGuides": true，缩进参考线
- "editor.rulers": [120]，垂直标尺，每行 120 字符
- "editor.minimap.enabled": false，关闭小地图 Minimap
- "editor.cursorBlinking": "smooth"，光标闪烁
- "editor.cursorStyle": "line"，光标样式
- "editor.cursorWidth": 10，光标宽度，line 样式有效
- "editor.cursorSmoothCaretAnimation": true，是否平滑插入光标过渡动画
- "editor.renderLineHighlight": "all"，光标所在行高亮、背景色



编辑器书写体验怎么样？

- "editor.detectIndentation": false，关闭 VS Code 制表符和空格的自动检测
- "editor.insertSpaces": true，使用 4 个空格代替制表符号
- "editor.tabSize": 4
- "editor.formatOnSave": true，保存时，自动格式化代码
- "editor.formatOnType": true，写完一行后，是否自动格式化该行（有时**;**表示一行结束）
- "files.autoSave": "afterDelay"，文件推迟 1000ms 后 自动保存
- "files.autoSaveDelay": 1000
- "files.defaultLanguage": "go"，新建文件的默认语言类型



编辑器更多设置，查看 "editor."，不同类型的设置

- editor cursor， 是跟光标渲染和多光标相关的设置；
- editor find， 是与编辑器内搜索相关的设置；
- editor font， 是与字体有关的设置；
- editor format， 是代码格式化；
- editor suggest， 是和自动补全、建议窗口等相关的配置



------



**14 | 什么是工作台和命令面板？**



VS Code 整个界面统称为 **工作台 Workbench**



界面概览：查看主要 UI 组件的叠加图

- 菜单栏 

- 左侧侧边栏（活动栏 + ... ... ）

- - 文件资源管理器：CTRL + SHIFT + E

  - 跨文件搜索：CTRL + SHIFT + F

  - 源代码管理：CTRL + SHIFT + G

  - 启动和调试：CTRL + SHIFT + D

  - 管理扩展：CTRL + SHIFT + X

  - 其它插件

  - 管理（齿轮按钮）：VS Code 系统管理常用的快捷键

  - - 命令面板；设置、扩展、键盘快捷方式；用户代码片段；颜色主题；文件图标主题；检查更新

- 编辑器

- 面板（最下方）：CTRL + J 

- - 问题：CTRL + SHIFT + M，输出当前文件夹下代码里的所有问题和警告
  - 输出：CTRL + SHIFT + U，输出核心命令和插件的运行状态和结果。e.g.：GIT 插件可视化版本控制，输出 git 命令
  - 调试控制台：CTRL + SHIFT + Y，代码调试
  - **终端**：CTRL + `
  - 其它定义在面板区域显示的内容：e.g.：将**跨文件搜索**，显示在面板区域（设置 "search.location": "panel"）

- 状态栏

- - 错误、警告信息；行列值；缩进；编码；行尾序列；语言模式；反馈、通知；等等......

- 命令面板（CTRL + P）：默认隐藏的强大面板



命令面板：CTRL + P 调出面板

- ?：获取可进行的操作的帮助，分为编辑器命令、全局命令

- :：跳转到**编辑**中文件的指定行，CTRL + G

- @：跳转到**编辑**中文件的指定符号，CTRL + SHIFT + o

- @:：按类别跳转到**编辑**中文件的指定符号

- 文件名：打开指定文件

- \#：显示和跳转到工作区中指定的符号，CTRL + T

- \>：显示并运行命令（支持中英文关键字搜索），CTRL + SHIFT + P or F1 调出

- edt（edit） + SPACE：显示已经打开的文件

- edt active：显示当前活动组中的文件

- ext（extension） + SPACE：插件管理

- ext install：搜索、安装插件

- task + SPACE：任务

- debug + SPACE：调试

- term + SPACE：创建和管理终端实例

- - CTRL +` 切换终端
  - CTRL + SHIFT + ` 新建终端

- view + SPACE：打开指定 UI 组件



工作台设置

- "workbench.commandPalette.history": 10, 记录最近 10 条命令
- "workbench.commandPalette.preserveInput": true, 是否保留之前的输入



------



**15 | 了解文件管理，什么是 multi-root workspace？**



VS Code 所有操作都是基于文件和文件夹

- 打开的文件夹中存在 .git ，就启用 GIT 插件提供版本控制功能
- 发现存在 tsconfig.json ，就激活 TypeScript 插件提供语言服务



资源管理器：exployer.

- "explorer.confirmDelete": true, 资源管理器中，删除文件，是否需要确认
- "explorer.autoReveal": true, 打开一个文件时，资源管理器会自动滚动，保证这个文件滚动到屏幕中间
- "explorer.enableDragAndDrop": true, 拖放是否可用
- "explorer.confirmDragAndDrop": true, 拖放文件时，是否需要确认
- 默认都是打开的



.vscode 文件夹：存放仅对当前文件夹有效的设置文件

- 编辑器配置文件 setting.json 
- 调试设置 lauch.json ：如何调试当前文件夹下的代码
- 任务设置 task.json ：系统任务的设置文件

不希望代码管理工具管理，.gitignore 



多文件夹工作区（multi-root workspace）

- 在 VS Code 打开的文件夹或者文件，调出命令面板，搜索“工作区: or workspace:”

- 搜索“将文件夹添加到工作区（Add folder to workspace）”

- 搜索“将工作区保存为”，生成一个 .code-workspace 为后缀的工作区配置文件（JSON）

- - folders：保存了逻辑工作区中保存的多文件夹路径
  - extensions：插件设置
  - launch：调试设置
  - setting：工作区设置

- 搜索“打开工作区（Workspaces: Open Workspace）”选择 .code-workspace 打开指定工作区

- CTRL + R，也可打开最近的工作区，更简单



多工作区切换

- CTRL + W，关闭当前编辑器，无关机器可关，关闭当前工作区

- 命令面板，搜索“切换窗口（Switch Window）”，选择需要切换到的窗口

- 命令面板，搜索“快速切换窗口（Quick Switch Window）”，直接切换到的之前的窗口

- 命令面板，搜索“打开最近的文件（Files: Open Recent...）”

- - CTRL + R，选择最近的打开过的**工作区**、文件、文件夹，CTRL + Enter 在新的窗口中打开
  - CTRL + R，选择当前工作区，可实现重新加载窗口

- 命令面板，搜索“快速打开最近的文件（File: Open Recent...）”，在新窗口中打开



仅仅是切换窗口的话，个人还是觉得 CTRL + Tab 好点的说。



------



**16 | 怎么在编辑器里做好版本管理？**



VS Code 自带 GIT 版本管理的插件支持。



**VS Code 设计哲学：不想当一个黑盒子，而是尽可能开放给你**。GIT 学习成本很高，VS Code 提供了很多可视化操作，但同时，VS Code 会将这个可视化操作背后的命令，通过输出面板展示出来，以便问题排查。



VS Code 、GitLens 还是 Bash、SourceTree？



------



**17 | 如何配置终端模拟器，告别系统终端**



------



**21 | 你不知道的工作区快捷键**



------



**22 | 基于自然语言或者纯文本的设置界面**



新版本，用默认用户设置、默认键盘配置，代替了之前的编辑方式：默认设置和用户设置在编辑器并排显示。

- 命令面板，搜索“Open Default...” 可见：defaultSetting.json、默认的键绑定 
- 打开用户设置、打开设置（JSON） 对应用户设置 UI、JSON 查看方式，setting.json
- 打开键盘快捷方式，keybingings.json 



键盘快捷方式的设置 keybindings.json 中存在一个代码片段

```json
{
	"key": "ctrl+s",
	"command": "workbench.action.files.save",
	"when": "editorTextFocus"
}
```



- key：快捷键，JSON Schema 定义，key 不可为空

- command：快捷键对应的底层命令

- when：快捷键合适生效，默认是光标在编辑器文本上时有效。when 支持一下判断

- - 逻辑运算（!、==、&&）
  - 正则表达式（=~）

- 解除命令的快捷键：command 值前加“-”减号



------



**23 | 基础语言支持：JSON、Markdown**



VS Code 为配置文件们都指定了一个特殊的 JSON 文件类型：JSON with Comments，可以为 JSON 文件提供注释。



VS Code 中配置文件、任务系统、代码调试、代码片段、键绑定等，均是 JSON 语法。



JSON 语言服务支持 JSON Schema，可以对 JSON 文件内容格式的约束，并提供了对应的语法检查。



如何给 JSON 文件指定，Schema 约束

- JSON 文件中指定
- 个人设置、工作区设置中设置



Markdown 编辑存在大量的快捷键，建议使用专业第三方编辑：Typora、马克飞象



------



**24 | 编程语言语言支持：Java、Go**





更多内容：VSCode 插件开发暂时搁置

