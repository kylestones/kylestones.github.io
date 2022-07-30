---
title: Learning GNU Emacs
date: 2017-01-02
---

# 1. 第一章
## 1.1. 输入命令
如果不知道一个命令对应的按键或者需要输入命令的时候，首先输入'ESC x'或者'META-x'，然后输入命令，接着回车即可。
## 1.2. 缓冲区 buffer
编辑器并不会对文件本身进行编辑，会首先将文件的内容放到一个临时性的缓冲区里（文件的一个副本），然后再对缓冲区中的东西进行编辑。缓冲区的名字通常就是正在编辑的文件的名字。
*scratch*是一个临时性的辅助性的缓冲区，类似草稿簿。
*help*是将帮助信息显示的地方
## 1.3. 编辑模式
Emacs有很多个主模式，且一个编辑缓冲区只能处于一个主模式，退出某个主模式的办法就是进入另一个主模式。
Emacs会依据文件名后缀或者文件的内容来判断文件的类型，从而尝试进入正确的模式。如果无法判断，会转入基本编辑模式。

| 模式 | 功能 |
| :--- | :--- |
| 基本模式（fundamental mode） | 默认模式，无特殊行为 |
| 文本模式（text mode） | 书写文字材料 （2） |
| 邮件模式（mail mode） | 书写电子邮件消息（6） |
| RMAIL mode | 阅读和组织电子邮件（6） |
| 只读模式（view mode） | 查看文件，但不进行编辑（5） |
| shell mode | 在Emacs里运行一个UNIX shell（5） |
| FTP模式（ange-ftp mode） | 下载或者查看远程系统上的文件（7） |
| telnet mode | 登陆到远程系统（7） |
| 大纲模式（outline mode） | 书写大纲（8） |
| 缩进文本模式（indented text mode） | 自动缩进文本（8） |
| 图形模式（pictures mode） | 绘制简单的线条图形（8） |
| nroff mode | 按nroff的要求对文件进行排版（9） |
| TEX mode | 按TEX的要求对文件进行排版（9） |
| LATEX mode | 按LATEX的要求对文件进行排版（9） |
| C mode | 书写C语言程序（12） |
| C++ mode | 书写C++程序（12） |
| FORTRAN mode | 书写FORTRAN程序（12） |
| Emacs LISP mode | 书写Emacs LISP程序（12） |
| LISP mode | 书写LISP程序（12） |
| LISP 互动模式（LISP interaction mode） | 书写和求值LISP表达式（12） |

在主模式之外还有一些副模式（minor mode），用于定义Emacs的某些特定的行为，可以在主模式里打开或者关闭。比如自动换行模式（auto-fill mode）会使文件在一个适当的位置自动插入一个换行符。

| 副模式 | 功能 |
| :--- | :--- |
| 自动换行模式（auto-fill mode） | 开启字换行（word warp）功能（2） |
| 改写模式（overwrite mode） | 打字是替换而不是插入（2） |
| 自动保存模式（auto-save mode） | 把文件按一定的按键次数自动保存到一个特殊的临时文件 |
| 行号模式（line numer mode） | 在状态行上显示当前文本行的行号（2） |
| 临时标记模式（transient mark mode） | 选取的文本区做高亮反显 |
| 缩略词语模式（abbrev mode） | 允许使用单词的简写形式（3） |
| 大纲模式（outline mode） | 书写大纲（8） |
| VC模式（VC mode） | 在Emacs下使用各种版本控制系统（15） |

大纲模式既是主模式也是副模式。还有一些不常见的或者Emacs自己使用的模式没有列出。
如果擅长LISP程序设计，可以自行增加新的编辑模式。Emacs的可扩展性似乎是无穷的。
## 1.4. 启动Emacs
在shell中输入'emacs filename'就可以打开文件，如果想在shell中打开文件可以加上参数'-nw'
光标的位置称为插入点。
编辑画面包括菜单栏、工作区、状态行、辅助输入区（minibuffer）
状态行：左边两个星号(\*\*)显示文件被修改过；接着是缓冲区的名字；然后是当前的行数（Top、Bot、45%、ALL）；然后圆括号中是当前的编辑模式；每个缓冲区都有自己的状态行。
辅助缓冲区：发出命令执行的结果、出错的信息、搜索替换等。如果困在输入缓冲区，可以使用C-g组合键。
## 1.5. Emacs命令
每个命令都有一个正式的名字，**他们是Emacs内部LISP例程的名字**。名字一般比较长。
Emacs把一个命令与一个以CTRL或者META打头的组合键关联起来，命令与组合键之间的这种联系被称为“绑定”，在X窗口，Emacs会把一些命令与鼠标动作和菜单里的某些选项绑定在一起。
Emacs的创作者们已经尽量把最常用的命令，与手指最容易接触的组合键绑定在一起：
* 最常用的命令被绑定为“C-n”（n可以是任意的字符）的形式
* 次常用的命令被绑定为“M-n”（n可以是任意的字符）
* 其他常用的命令被绑定为“C-x something”（something可能是一个或者多个字符、或者是另外一个控制组合），文件操作命令通常被绑定为“C-x something”的形式
* 某些特殊的命令被绑定为“C-c something”的形式，用于特殊的模式
* 有些无法绑定的命令，使用“M-x long-command-nam RETURN”输入，适合全部命令，但组合键通常比较容易
Emacs允许用户自己定义组合键（11章）
## 1.6. 基于文本的菜单
按下F10或者“M-`”（单反引号）将打开一个列出菜单选项的编辑缓冲区（*Completions*）,然后有三种方法来选择
* 使用PgUp键切换到*Completions*缓冲区，然后使用方向键移动到需要的选项上，再按回车键
* 上下键选择，然后回车
* 输入*Completions*缓冲区里各选项前面的首字母，就直接选中了该选项。
## 1.7. 打开一个文件
“C-x C-f”（长格式命令“find-file”），创建一个编辑缓冲区，名字同文件的名字相同。
“C-x C-f”操作允许通配符（可能较早的版本不支持），在启动Emacs时，后面使用通配符来同时打开多个文件
**只要Emacs需要进一步提供信息，它就会把光标自动放到辅助输入区，完成在辅助输入区的输入之后，需要按回车键来确认；普通编辑命令后面不需要按回车键**
对同一个文件进行两次读入操作，并不会打开一个新的缓冲区，它会进入该文件所在的缓冲区。
“C-x C-v”（“find-alternative-file”）用于读取另外一个文件来替换当前文件，缓冲区的内容会被替换
## 1.8. 插入和追加文件
首先移动光标到所需要的位置，然后按下“C-x i”来打开需要插入的文件
## 1.9. 默认目录
使用任何一个需要进一步给出文件名的命令时，Emacs会在辅助输入区给出一个默认的目录，默认为当前缓冲区文件所在的子目录。若当前缓冲区与文件没有联系，会打开一个默认的目录。在猜测用户想设置的默认目录方面，Emacs还是相当有门道的。
## 1.10. 保存问件
“C-x C-s”用于保存文件，同样可以保存“scratch”缓冲区到一个文件。
“C-x C-w”用于将缓冲区另存为一个文件，若不输入直接回车就会任然保存到原文件
## 1.11. 退出Emacs
“C-x C-c”用于退出Emacs，若没有保存修改会得到相应的提示信息，且若输入‘n’不保存的时候，会再次提示，此次必须输入完整的“yes”或“no”作为回答。
## 1.12. 自动补全
打开一个已经存在的文件或者长格式命令，只要输入头几个字母以构成唯一识别，然后按下TAB键，Emacs会自动补全剩余的部分。如果存在多个相关的文件或命令，Emacs会打开一个窗口，把以这个字符串开头的文件或命令都列出来，然后再选择确定即可。
## 1.13. 获取帮助
“C-h”组合键用于获取在线帮助信息。
Tutorial：“C-h t”组合键将启动Emacs教程，这是一个非常好的入门教程。
Describe Key（击键序列）：“C-h k”
Describe Function（函数释义）：“C-h f”
获取按键绑定对应表
访问UNIX命令的使用手册（manpage）
Emacs常见问题答疑（frequently asked questions，简称FAQ）
对当前模式的一个介绍
Info文档阅读器：“C-h i”，使用info命令来查阅Emacs在线文档的接口
# 2. 第二章 文件编辑
## 2.1 自动换行模式
“M-x auto-fill-mode RETURN”用于打开和关闭自动换行模式的开关状态。
## 2.2 光标的移动
### 2.2.1 基本的光标移动操作

| 命令 | 动作 |
| :--- | :--- |
| C-f | forward，光标向右移动一个字符的位置 |
| C-b | backward，光标向左移动一个字符的位置 |
| C-p | previous-line，光标向上移动一行 |
| C-n | next-line，光标向下移动一行 |

### 2.2.2 其他的光标移动方法

| 命令 | 动作 |
| :--- | :--- |
| M-f | 光标右移一个单词 |
| M-b | 光标左移一个单词 |
| C-a | 光标移动到一行的开始（‘a’是字母表的第一个字母） |
| C-e | 光标移动到一行的结束 |
| M-a | 光标左移一个句子 |
| M-e | 光标右移一个句子 |
| M-} | 光标下移一个段落，如果光标在一段的中间，那么光标回到该段的其实位置 |
| M-{ | 光标上移一个段落 |
| C-x ] | forward-page，光标下移一页，“C-q C-l”插入分页符 |
| C-x [ | backward-page，光标下移一页 |
| M-> | 调到缓冲区的末尾，同END键 |
| M-< | 调到缓冲区的开头，同HOME键 |
| M-x goto-line n RETURN | 光标调到第n行 |
| M-x goto-char n RETURN | 光标调到第n个字符 |

**Ctrl按键依据字符来移动，META按键依据语义来移动字符；所以Ctrl“开头的命令比“META”开头的命令移动的距离短。**
Emacs对句子和段落有较严格的规定

### 2.2.3 翻页

| 命令 | 动作 |
| :--- | :--- |
| C-v | 向下翻页，上一屏幕的最后几行会保留在屏幕的顶部。 |
| M-v | 向上翻页 |

如果输入的光标移动命令的目标位置在当前屏以外，Emacs会自动卷屏。

## 2.3 命令的重复执行

Emacs的任何命令都运行重复执行多次

“M-n order“：可以让命令执行n次，可以用于大文件的光标移动”M-x 200 C-n“光标向下移动200行
”C-u n order“：同样可以让命令执行n次，若不加”n“，将默认执行4次，且”C-u C-u order“会将命令执行16次，即重复使用”C-u“可以按4的幂次来执行随后的命令：4,16,64,256....

## 2.4 重新绘制屏显画面
”C-l“：有其他多余的信息打乱了当前的画面，该组合键会清楚无用的显示信息。同时可以将正在编辑的行放置到窗口的中心位置，方便用户查看上下文。
## 2.5 Emacs支持键盘上的标准按键
如PgDn、Home等按键均被支持
## 2.6 文本的删除
Emacs提供了向前向后删除单词、句子、段落的编辑命令，光标位于单词、句子、段落中间时，只会删除单词、句子、段落的部分内容。

| 命令 | 动作 |
| :--- | :--- |
| C-x u | 撤销最近一次的编辑，再次按下撤销上次的编辑 |
| DEL | 删除光标左侧的字符（文档上显示为DEL按键，其实是BackSpace键） |
| C-d | delete-character，删除光标所在位置处的字符 |
| M-d | kill-word，删除下一个单词（“c-d”对字符操作，“M-d”对单词操作） |
| M-DEL | backward-kill-word，删除前一个单词，光标至该单词的第一个字母。 |
| ESC-C-k | 删除行首至光标处之间的字符。（试验不成功） |
| C-k | kill-line，删除光标至行尾的文本，再次按下删除换行符。 |
| C-x DEL | backward-kill-sentence，删除光标前面的句子 |
| M-k | kill-sentence，删除光标后面的句子。 |
| C-w 或者 SHIFT-DELETE | kill-region，删除文本块 |
| 无 | backward-kill-paragraph，删除光标前面的段落 |
| 无 | kill-paragraph，删除光标后面的段落 |

## 2.7 恢复已删除的文本
被删除的文本被保存在了删除环中（kill-ring），除了DEL和“C-d”两个删除单个字符的操作不会被保存在删除环，其他的删除和复制操作都会保存到删除环。
“C-y”--“SHIFT-INSERT | yank，恢复被删除的文本
## 2.8 文本块及其编辑操作
用标记文本的方法把打算删除的东西定义为一个区域，称之为文本块。

| 命令 | 动作 |
| :--- | :--- |
| C-@ 或者 C-SPACE | 设置一个文本标记（此时在辅助输入区出现‘Mark set’字样），然后移动光标，文本标记和光标之间的文本就构成了一个文本块。（光标显示在字符上，插入点是光标所在字符与前一个字符之间的空隙） |
| C-x C-x | exchange-point-and-mark，互换插入点和文本标记的位置。 |
| M-h | mark-paragragh，把文本标记放到段落的末尾，光标放到段落的开始位置 |
| C-x h | mark-whole-buffer，标记整个缓冲区 |
| C-x C-p | 标记当前页面， |

鼠标左键拖动选中文本块；或者在开始处左键单击，结束处右键单击来标记；双击选取一个单词；三击选取一行文本；
## 2.9 文本复制

| 命令 | 动作 |
| :--- | :--- |
| M-w | kill-ring-save，用于复制选中的文本块 |
| C-y | yank，粘贴刚才复制的内容 |
| M-y | 从删除环中选择需要恢复的文本，删除环可以记录最近30次删除的东西。 |

## 2.10 段落重排

## 2.11 交换位置

| 命令 | 动作 |
| :--- | :--- |
| C-t | transpose-chars，交换两个字符的位置，当前字符与前一个字符交换 |
| M-t | transpose-words，在两个单词的中间，交换前后两个单词 |
| C-x C-t | transpose-lines，交换当前行与前一行的文本的位置 |
|  | transpose-sentences，交换两个句子的位置 |
|  | transpose-paragraphs，交换两个段落的位置 |

## 2.12 改写字母的大小写

| 命令 | 动作 |
| :--- | :--- |
| M-c | capitalize-word，单词的首字母改为大写（光标移动到单词首字母）；如果光标位于文本的中间，则Emacs只对光标位置到单词结尾之间的字母处理。 |
| M-l | downcase-word，单词的所有字母改为小写 |
| M-u | upcase-word，单词的所有字母改为大写 |
| M-\- | negtive-argument，在命令前加上该命令则不会改变光标的位置，且光标位于单词中间的时候，后面的命令只对单词的前半部分做修改。 |

## 2.13 文本的改写
按键INSERT，或者”M-x overwrite-mode RETURN“进入改写模式（overwrite mode），在状态行出现Ovwrt
## 2.14 命令的中止和修改的撤销

## 2.15 撤销修改

| 命令 | 动作 |
| :--- | :--- |
| M-x revert-buffer RETURN | 重新读取文件，仅对当前文件有效 |
| C-g | keyboard-quit，放弃当前命令 |
| C-_ 或 C-/ | undo，撤销上次编辑 |
| C-x u | advertised-undo，撤销上一次编辑，与上一条命令的不同待考证 |

## 2.16 文件备份
Emacs会自动创建备份文件，在原文件名后加上~，也可以备份几个文件使用不同的数字后缀来表示，后缀是~n~
## 2.17 恢复丢失的修改
开启”Auto saving“模式，在原名字前后加上井字符（#），输入”M-x recover-file RETURN“恢复自动保存的文件。Emacs每隔300次击键就自动存盘一次。
## 2.18 对Emacs进行定制
编辑.emacs文件可以对Emacs进行定制
# 3. 第三章 查找和替换操作
Emacs提供查找方式：简单查找、递增查找、单词查找、正则表达式查找、递增正则表达式查找；默认查找不区分大小写，但是输入一个以上的大写字母查找就会区分大小写。
替换与查找紧密相连：简单查找与替换、查询-替换、正则表达式替换

## 3.1 递增替换

| 命令 | 动作 |
| :--- | :--- |
| C-s word | isearch-foward，word就是想要查找的单词（进入Isearch），从光标位置以后开始查找。如果找到的位置错误，继续按“C-s”来继续搜索。找到后使用RETURN来确定，输入错误使用DEL来修改。取消查找使用“C-g”。 |
| C-r word | issarch-backward，向上查找 |
| C-s C-w | 把编辑缓冲区中的单词复制到查找字符串里（光标到下一个标点符号或者空格） |
| C-s C-y | 光标至行尾的文本全部复制到查找字符串 |
| C-s M-y | 把删除环中的文本复制到查找字符串，使用“M-p”查看上一个，“M-n”查看下一个。 |

## 3.2 简单查找

| 命令 | 动作 |
| :--- | :--- |
| C-s RETURN searchstring RETURN | 向前开始非递增查找 |
| C-r RETURN searchstring RETURN | 向后开始非递增查找 |

## 3.3 单词查找
不受换行符、空格、标点符号的影响，但要求查找字符串与文件里的单词完整的匹配。

| 命令 | 动作 |
| :--- | :--- |
| C-s RETURN C-w searchstring RETURN | word-search-forward，向前进行单词查找 |
| C-r RETURN C-w searchstring RETURN | word-search-forward，向后进行单词查找 |

## 3.4 基本的查找-替换

| 命令 | 动作 |
| :--- | :--- |
| M-x replace-string RETURN searchingstring RETURN newstring RETURN | 替换光标开始之后的所有字符串，若想替换所有的字符串，需要先将光标移动到文件的开始位置（M-<）。并且Emacs可以自行处理字母的大小写（句子开头首字母大写）。 |

## 3.5 查询-替换

| 命令 | 动作 |
| :--- | :--- |
| M-% oldstring RETURN newstring RETURN | 开始查询替换 |
| SPACE或y | 将新的字符串替换原字符串，然后将光标定位到下一个字符串 |
| DEL或n | 不替换，前进到下一个字符串 |
| . | 在当前位置做替换操作后退出查询-替换操作 |
| , | 替换并显示替换情况，在按空格或者y后才移动到下一个位置 |
| ! | 对后面的文件内容全部进行替换，不再继续询问是否进行替换 |
| ^ | 返回上一次进行了替换的位置 |
| RETURN或q | 退出替换-查询操作 |
| C-r | 进入递归编辑状态 |
| C-w | 删除此处内容并进入递归编辑状态 |
| ESC C-c | 退出递归编辑状态，继续完成查询-替换操作 |
| C-] | 退出递归编辑状态和查询-替换操作 |

## 3.6 执行历史命令

| 命令 | 动作 |
| :--- | :--- |
| C-x ESC ESC | 调出最后一次输入的复杂命令，使用“M-p”查询之前的命令，“M-n”查询之后的命令。 |

## 3.7 递归编辑
开始查询-替换操作，按下“C-r”之后可以进行编辑操作，编辑完后，使用“ESC C-c”继续刚才的编辑工作。
“M-x recursive-edit RETURN”可以在任何时候进入递归编辑状态，并且递归编辑可以嵌套（不明白有和作用）；“ESC C-c”退出编辑状态。
## 3.8 查询、替换操作的大小写问题
“M-x set-variable RETURN”，输入需要更改值的变量名“case-fold-search RETURN“，然后输入新值”nil“（依据输入的文本来替换）或者”t“（依据原单词的大小写来替换）代表true，更改查询时的大小写情况；变量”case-replace“更改查询替换时的大小写。
## 3.9 查找和替换中的正则表达式

| 字符 | 匹配情况 |
| :--- | :--- |
| ^ | 匹配行首 |
| $ | 匹配行尾 |
| . | 匹配任意单个字符 |
| .* | 匹配0个及以上任意字符 |
| \< | 匹配单词的开头 |
| \> | 匹配单词的结尾 |
| [] | 匹配方括号中的任何一个字符 |

正则表达式查找命令

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| ESC C-s RETURN | re-search-forward | 向前查找一个正则表达式 |
| ESC C-r RETURN | re-search-backward | 向后查找一个正则表达式 |
| ESC C-s | isearch-forward-regexp | 向前递增查找一个递增正则表达式 |
| ESC C-r | isearch-backward-regexp | 向后递增查找一个递增正则表达式 |
| 无 | query-replace-regexp | 查询-替换一个正则表达式 |
| 无 | replace-regexp | 无条件的对一个正则表达式做全局性的替换 |

## 3.10 拼写检查
Emacs提供Ispell或者UNIX操作系统的拼写检查去spell，拼写检查器有一个词汇表称为字典，如果单词没有出现在字典里就认为单词拼写错误，但其无法检查”two“误写成”too“这类错误。
### Ispell
Ispell提供了对一个编辑缓冲区、一个文本块、一条电子邮件消息、一个单词进行品写检查的操作选项。
“M-x ispell-buffer RETURN | 检查整个缓冲区，如果全部拼写正确，Ispell给出“Spell-checking done”提示；如果找到错误单词，光标会定位到第一个Ispell不认识的单词。此时可以查看帮助信息。
如果Ispell列出的单词就是需要的，按下相应的数字键即可进行替换；

| 命令 | 动作 |
| :--- | :--- |
| ? | 列出可供选择操作 |
| r | 可以自己修改那个单词，Ispell会再次检查该单词 |
| R | Ispell将开始一次查询-替换操作，以便把缓冲区里所有同样的错误都改正过来。 |
| space | 使Ispell跳过某个单词 |
| a | 使Ispell跳过缓冲区中所有的,某个拼写错误的单词； |
| A | 告诉Ispell在此次编辑工作中接受这个单词； |
| i | 让Ispell把该单词插入到个人字典里，这个字典保存在个人主目录下.ispell_<language>words文件中。 |
| u | 让Ispell把单词转换成小写，然后存入字典 |
| C-r | 开始一次递归编辑，完成后“ESC C-c”退出递归编辑 |
| R | 在编辑缓冲区对这个单词进行查询-替换 |
| ! | 把该单词的拼写错误全部改正 |
| ex | 退出拼写检查 |

#### 查单词

“M-$”：ispell-word可以让Ispell检查单词是否拼写正确
"M-TAB“：ispell-complete-word，把单词的各种补足形式列出来

#### 总结

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| M-$ | ispell-word | 检查光标上或者光标后的单词 |
| 无 | ispell-region | 检查文本块的单词 |
| 无 | ispell-buffer | 检查缓冲区里的单词 |
| 无 | ispell-emssage | 检查电子邮件正文的单词 |
| C-u M-$ | ispell-continue | 使用C-g取消后，再次重新开始继续检查 |
| 无 | ispell-kill-ispell | 杀死Ispell进程 |
| M-TAB | ispell-complete-word | 自动补全当前单词 |

### spell
测试没有发现unix的拼写检查器
spell-word
spell-buffer
spell-region
## 3.11 单词简写模式（word abbreviation mode）
简写词的作用范围是模式（文本模式、全局模式），输入某个简写词后按空格或者其他的字符，Emacs自动将其补充完整，如不想让刚输入的单词作为简写词，使用“M-x unexpand-abbrev RETURN”来取消扩展。
### 为编辑工作临时定义的一些简写词汇

“M-x abbrev-mode RETURN”进入单词简写模式，“C-x a i g”（add-inverse-global）定义全局，“C-x a i l”（add-inverse-local）定义局部性简写词。
“M-x write-abbrev-file RETURN”保存这些简写模式，一般保存在文件.abbrev_defs中。可以在.emacs文件中设置启动使加载该文件。

```
(setq-default abbrev-mode t)
(read-abbrev-file "~/.abbrev_defs")
(setq save-abbrevs t)
```

| 命令 | 动作 |
| :--- | :--- |
| M-x edit-abbrevs RETURN | 编辑简写词汇，最安全的方法是使用“C-k”删除某一行，不要手动编辑，那样比较危险，最后保存简写条目。
| M-x list-abbrevs RETURN | 查看简写词汇
| M-x kill-all-abbrevs RETURN | 在本次编辑中禁用简写词汇
| M-x unexpand-abbrev“：撤销最近一个简写词定义条目

简写词汇对字母大小写的规则

```
Here are the rules:
If the abbreviation's definition contains any uppercase letters, Emacs always inserts the
definition without changing anything. For example, if you define ora as an abbreviation for
O'Reilly Media , O'Reilly will always be capitalized exactly as shown.
If the abbreviation's definition is all lowercase, Emacs capitalizes according to the following
rules:
If you type all of the letters of the abbreviation in lowercase, Emacs inserts the
definition in lowercase.
If you type any of the letters of the abbreviation in uppercase, Emacs capitalizes the
first letter of the first word.
If you type all of the letters of the abbreviation in uppercase, Emacs capitalizes thefirst letter of every word, unless the variable abbrev-all-caps is set to t ; in this
case, it capitalizes all letters.
```
# 4. 第四章 使用编辑缓冲区和窗口
## 4.1 编辑缓冲区

| 命令 | 动作 |
| :--- | :--- |
| C-x b | 切换缓冲区 |
| C-x C-b | 列出所有缓冲区 |
| C-x s | save-some-buffers，Emacs会依次询问是否保存每个缓冲区，使用‘y’、‘n’来处理，或者‘!’来保存所有的编辑缓冲区；‘,’只保存某一个编辑缓冲区；‘q’取消该命令。 |
| C-x k | kill-buffer，关闭缓冲区，默认是当前缓冲区 |
| M-x kill-some-buffers | 依次询问是否删除每一个缓冲区 |
| M-x rename-buffer | 更改缓冲区的名字 |
| C-x C-q | 把编辑缓冲区设置为只读属性，再次按下会取消只读属性 |

## 4.2 窗口编辑
Emacs的窗口不可以重叠，可以让多个窗口显示同一个缓冲区，在一个窗口的修改将同步显示在另一个文件中。
但屏幕上只能有一个光标，即只能呆在一个窗口里；但每个窗口都有自己的插入点。
文本标记是与编辑缓冲区关联的，一个缓冲区只能有一个文本标记。

| 命令 | 动作 |
| :--- | :--- |
| C-x 2 | 创建水平排列的窗口，emacs后面接两个文件会默认打开水平排列的窗口 |
| C-x 3 | 创建左右排列的窗口 |
| C-x o | 窗口之间移动,(o代表other的意思)，顺时针方向移动窗口，“ESC n C-x o”移动窗口的命令重复n次。 |
| C-x 0 | 关闭当前窗口，不会关闭相应的缓冲区 |
| C-x 1 | 关闭其余的窗口，只保留当前窗口 |
| M-x delete-windows-on RETURN buffername RETURN | 关闭某个缓冲区的所有窗口 |
| C-x ^ | 加高当前窗口的高度 |
| C-x } | 加宽当前窗口的宽带 |
| M-x shrink-window | 降低当前窗口的高度 |
| C-x { | 减小当前窗口的宽度，“C-u"可以一次使窗口变化4行或者4列 |
| C-x + | balance-windows，让各个窗口的大小相同 |

窗口大小的上下限，依据变量window-min-height、window-min-width来确定
可以在不同的窗口之间拷贝文件
### 在当前窗口对其他窗口操作
“ESC C-v”让下一个窗口翻页
在命令中间添加数字“4”来实现，“C-x 4 f”让下一个窗口打开一个文件，“C-x 4 b”让下一个窗口打开一个缓冲区
这些命令都可以避免在窗口之间频繁移动
### 对比两个窗口中的文件
首先打开两个窗口，插入点定位到文件的开始，输入命令“compare-windows”后插入点定位到两个文件的不同之处。插入点移动过第一个不同的位置之后，再次使用该命令可以找到第二处不同，依次类推。
### 缓冲区清单
“C-x C-b”打开缓冲区清单，其中MR列字符含义：
. -> 已显示；% -> 只读；> -> 标记为待显示；
* -> 已修改；D -> 标记为待删除；S -> 标记为待存盘
切换窗口“C-x o”进入缓冲区清单，可以在缓冲区清单中对缓冲区进行显示、删除、保存等操作
在缓冲区清单中可以使用“C-n”（或者空格）、“C-p”上下移动


| 命令 | 动作 |
| :--- | :--- |
| d、k | 将某缓冲区标记为待删除，其第一列将显示D字符，且光标将移到下一行，此时使用“backspace”可以删除刚才设置的标记，或者移动光标到上一行，然后使用“u”来删除；之后按下“x”（表示execute） |
| s | 将某缓冲区标记为待存盘，显示S字符，同样使用“x”执行 |
| ~ | 将缓冲区标记为未修改，立即生效 |
| % | 缓冲区的状态改成只读，其状态行将显示%%，也可以使用“C-x C-q”来切换 |
| 1 | 将缓冲区满屏显示 |
| 2 | 将该缓冲区显示在缓冲区清单窗口 |
| f | 将该缓冲区内容在缓冲区清单窗口显示 |
| o | 将缓冲区显示到另一个窗口，且光标移动到该窗口 |
| C-o | 将缓冲区显示到另一个窗口，但光标不移动 |
| m | 表示mark，在多个窗口上标记，然后使用“v”，Emacs将自动创建一些水平窗口来显示这些缓冲区 |
| q | 关闭缓冲区清单 |

## 4.3 书签

| 命令 | 动作 |
| :--- | :--- |
| C-x r m | bookmark-set，在光标处设置书签书签名长度没有限制，且可以有空格 |
| C-x r b | bookmark-jump，跳转到某个书签 |
| bookmark-rename | 对书签重命名 |
| bookmark-delete | 删除书签 |
| bookmark-save | 把书签全部保存到默认的书签文件里 |
| C-x r l | bookmark-menulist，打开书签清单窗口 |
| bookmark-insert | 插入与给定书签关联文件的完整内容 |
| bookmark-write | 把书签全部保存到一个指定的文件 |
| bookmark-load | 从指定文件里加载书签 |

### 书签清单

| 命令 | 动作 |
| :--- | :--- |
| C-x r l | 打开书签清单窗口 |
| d | 添加待删除标记 |
| x | 执行待标记的操作 |
| u | 去掉书签上的待删除标记 |
| DEL | 删除刚刚标记的操作 |
| r | 对书签重命名 |
| s | 把书签全都保存起来 |
| m | 标记待打开的书签，“v”前面标记的书签 |
| v | 打开该书签 |
| f | 打开该书签 |
| t | 显示和隐藏书签所对应的文件路径 |
| w | 在状态行显示标签对应文件的路径 |
| q | 退出书签清单 |

## 4.4 临时挂起Emacs
“C-z”可以挂起Emacs，不过书中忠告：几乎永远没有任何理由离开Emacs。
## 4.4 窗格
Emacs把X窗口称为窗格frame，其操作和窗口相似。例如窗口使用“C-x 4 f”查找文件，窗格使用“C-x 5 f”查找文件

| 命令 | 动作 |
| :--- | :--- |
| C-x 5 2 | make-frame，创建一个新窗格 |
| C-x 5 0 | delete-frame，关闭一个当前的窗格 |
| C-x 5 b | switch-to-buffer-other-frame，在新窗格里打开一个缓冲区 |
| C-x 5 o | other-frame，进入另一个窗格 |
| C-x 5 r | find-file-read-only-other-frame，创建新窗格以只读方式打开文件 |
| C-x 5 f | find-file-other-frame，在一个新窗格里查找打开文件 |

# 5. 第五章 Emacs工作环境
## shell

shell-file-name变量决定使用那种shell来执行各种命令
“M-!”：执行一条shell命令，结果显示在一个编辑缓冲区中，可以对该缓冲区编辑、保存或者其他任何操作
"M-|":shell-command-on-region，先标记一段文本，然后将该文本作为输入来执行shell命令
“C-u M-!”：将shell执行的命令直接放入当前编辑缓冲区

## shell模式

| 命令 | 动作 |
| :--- | :--- |
| M-x shell | 启动shell编辑缓冲区，在该编辑缓冲区可以进行shell命令，也可以使用Emacs对缓冲区的操作，但有些shell命令需要在使用之前加上“C-c”，如“C-c”、“C-z”、“C-d”、“C-u”等 |
| M-p | 把最后输入的一条shell命令放在命令提示符之后，继续使用调出之前的命令，“M-n”配合使用，两个均是Emacs用于历史命令的操作 |
| RETURN | 可以移动插入点到某一条命令，然后使用回车来执行该命令，也可以编辑之后再执行 |
| TAB | 自动补全 |
| C-c C-o | 自动删除上一条命令的输出，假如其输出太多而影响其他的操作。但其只能删除上一条命名的输出， |
| C-c C-r | 上一条命名输出的第一行显示出来（输出太多时） |
| C-c C-e | 上一条命名输出的最后一行显示出来 |
| C-c C-p | 在各条命令的输出之间跳转，向上跳 |
| C-c C-n | 在各条命令的输出之间跳转，向下跳 |
| rename-uniquely | 重命名当前shell，然后就可以打开另一个新的shell，可以打开任意多个 |

## 文件和目录操作
Dired模式（directory editing mode）提供了对目录进行编辑的有效手段。启动Emacs可以加上一个目录名进入Dired模式，或者使用“C-x C-f”加一个目录的名字同样可以进入Dired模式，或者“C-x d”（命令名dired）进入Dired模式。所有的清单操作都几乎相同。
**Dired是直接对文件进行操作的，删除就会使一个文件永久消失**

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| s | dired-sort-toggle-or-edit | 更改文件清单以名字或者日期来排序 |
| v | dired-view-file | 以查看模式view-mode来显示该文件 |
| q |  | 查看文件后，返回目录文件清单或者退出dired |
| Q | dired-do-query-replace | 在加油待操作标记的文件里对字符串进行查找-替换操作 |
| f | dired-advertised-find-file | 查找文件，以对他编辑文件 |
| d | dired-flag-file-deletion， |  |
| u | dired-unmark | 去掉待操作标记 |
| x | dired-do-flagged-delete | 删除有待删除标记的文件 |
| m | dired-mark | 给文件添加”*“待操作操作，前面可加数字 |
| M-{ | dired-prev-marked-file | 移动到前一个有标记的文件上 |
| M-} | dired-next-marked-file | 移动到后一个有标记的文件上 |
| < | dired-priv-dirline | 移动到上一个目录 |
| > | dired-next-dirline | 移动到下一个目录 |
| # |  | 给所有自动保存的文件加上待删除标志 |
| ~ |  | 给所有的备份文件加上待删除标记 |
| D | dired-do-delete | 直接删除文件，此处大小写导致操作不同较特殊 |
| C | dired-do-copy | 复制该文件，前面可以加数字用于复制多个文件 |
| R |  | 文件重命名，等同于UNIX的移动操作 |
| e | dired-find-file | 编辑文件 |
| G | dired-do-chgrp | 改变文件的组权限 |
| k | dired-do-kill-lines | 从画面上删除当前行（不是删除文件） |
| n | dired-next-line | 移动到下一行 |
| o | dired-find-file-other-window | 移动到新窗口 |
| C-o | dired-sirplay-file | 在另一个窗口里查找文件，但不移动光标 |
| g | revert-buffer | 刷新文件缓冲区 |
| G | dired-do-chgrp | 改变文件的组权限 |
| m | dired-mark | 给文件加上”*“待操作标记，前面可加数字 |
| P | dired-do-print | 打印文件 |

### 利用Dired模式进行文件的压缩和解压
“Z”： 对文件进行压缩和解压
### 文件比对
“=”：可是利用diff来比对两个文件
### 文件上运行UNIX命令
“!”：dired-do-shell-command，对文件运行UNIX命令，复杂的命令需要文件名时可以用'*'代替

### 对文件组进行操作
#### 选取文件

| 命令 | 动作 |
| :--- | :--- |
| d | 待删除 |
| m | dired-mark，待操作，前面可加数字 |
| M-DEL | dired-unmark-all-files，去掉所有待操作文件 |
| %m”、“%d | 利用正则表达式来标记文件 |

#### 文件组上的操作
“+”：dired-cerate-directory，创建目录
“Q”：dired-do-query-replace，对选的的文件进行查询替换操作
#### 简单的目录清单
“C-u C-x C-d”：给出一个详细的文件清单
“C-x C-d”：给出一个简单的文件清单
这两条命令都只是将文件清单放到了一个文件缓冲区里，可以对其进行任意的编辑，所有操作都不会对文件有影响。
## 打印操作


## 查看UNIX在线文档
“M-x man“： 将排版好的使用手册放到一个编辑缓冲区
“M-x manual-entry RETURN command-name RETURN”:  可以随心所欲的翻阅使用手册，且显示整齐
## 时间管理工具
### 时间
"M-x display-time":在状态行显示时钟
### 日历
"M-x calender":查看日历
"g d":依次输入年份、月份、日期来跳转
有很多可以在日历之间移动的命令
**可以设置成其他的日历，不知道是否支持农历**
支持查看节假日，日出日落，月相等
### 日记

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| g d | calendar-print-day-of-year | 显示今天是本年度的第几天 |
| SPACE | scroll-other-window | 卷动另一个窗口 |
| q | exit-claender | 退出日历功能 |

# 7. 第七章 Emacs的Internet工具箱
在Emacs中可以使用Telnet模式
使用w3m浏览网页
使用DocView查看PDF文件
# 8. 第八章 简单的文字排版和特效编辑
## 8.1 文本的缩进

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| M-m | back-to-indentation | 移动到文本行的第一个非空白字符上 |
| ESC C-o | split-line | 把句子分成台阶状 |

## 8.2 文本的居中
## 8.3 插入分页符
## 8.4 矩形编辑
定义矩形：利用“C-@”在矩形的左上角设置文本块标记，然后移动到矩形的右下角之右一个字符（光标上的字符不属于文本块），

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| C-x r k | kill-rectangle | 删除一个矩形并保存 |
| C-x r d | delete-rectangle | 删除一个矩形块但不保存 |
| C-x r y | yank-rectangle | 粘贴最后一次删除的矩形 |
| C-x r c | clear-rectangle | 清楚矩形区域的内容，且不保存 |
| C-x r o | open-rectangle | 在矩形区域里插入一个空白矩形 |

## 8.5 绘制简单的图形

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| 无 | edit-picture | 进入图形模式 |
| C-c C-c | picture-mode-edit | 退出图形模式 |
| C-c ^ | picture-movement-up | 绘制方向向上 |
| C-c . | picture-movement-down | 绘制方向向下 |
| C-c > | picture-movement-right | 绘制方向向左 |
| C-c < | picture-movement-left | 绘制方向为右 |
| C-c ` | picture-movement-nw | 绘制方向右上（上北下南左西右东）
| C-c ' | picture-movement-ne | 绘制方向左上 |
| C-c / | picture-movement-sw | 绘制方向左下 |
| C-c \ | picture-movement-se | 绘制方向为右下 |
| C-c C-f | picture-motion | 按绘制方向移动 |
| C-c C-b | picture-motion-reverse | 绘制的反方向移动 |
| C-c C-p | picture | |
| C-c C-n | picture | |

## 8.6 Emacs大纲模式
大纲模式可以有选择的显示和隐藏文章内容
不要混用大纲主模式和大纲副模式

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| C-c C-n | outline-next-visible-heading | 移动到下一个标题 |
| C-c C-p | outline-previous-visible-heading | 移动到上一个标题 |
| C-c C-f | outline-forward-same-level | 移动到上一个同级标题 |
| C-c C-b | outline-backward-same-level | 移动到下一个同级标题 |
| C-c C-u | outline-up-heading | 移动到上一级别的标题 |
| C-c C-t | hide-body | 隐藏全体正文 |
| C-c C-d | hide-subtree | 隐藏某标题及其下级小标题的全部正文 |
| 无 | hide-entry | 隐藏某标题的正文，不包括其下级小标题 |
| C-c C-l | hide-leaves | 隐藏某标题及其小标题的正文部分 |
| C-c C-a | show-all | 显示所有内容 |
| C-c C-s | show-subtree | 显示某给定标题的下级小标题和正文 |
| 无 | show-entry | 显示某给定标题的正文，不包括其下级小标题 |
| C-c C-k | show-branches | 显示某标题的正文及其全体下级标题的正文 |

# 11. 第十一章 对Emacs进行定制

## 11.1 添加Emacs按键绑定
(define-key keymap "keystroke" 'command-name)
(global-set-key "keystroke" 'command-name)
(local-set-key "keystroke" 'command-name)
###  键盘的特殊键
任何键盘上的特殊按键产生的字符代码都是一个特殊字符加几个可打印字符。
###  不重启emacs就使.emacs立即生效的方法
* 用 emacs 打开 .emacs 文件，C-x C-e 光标前面的运行一条语句。立即生效。
* 选择一个 region , M-x eval-region
* M-x load-file ~/.emacs
* M-x eval-buffer

# 12. 第十二章 程序员的Emacs
## 12.5 对程序进行编译
Emacs准备了一个面向编译器和UNIX的make工具的接口，与shell模式相比，这个接口更直接、更强大，接口的核心命令是“compile”，将引发一连串的事件。默认的编译命令是“make -k”，可以通过compile-command进行修改。输入编译命令后，Emacs会自动把未存盘的编辑缓冲区保存起来，接着在一个关联窗口里创建一个名为“*compilation*”的编辑缓冲区，用于运行编译命令
Emacs使用变量compilation-error-regexp-alist对错误信息进行分析，该变量是一个由正则表达式构成的列表，用于对列出的错误信息进行匹配，Emacs会利用列表中额每一条正则表达式对一条出错信息进行尝试性分析，直到找到那条能够用来准确地提取出错误发生地点的文件名和行号的正则表达式为止。但也有可能出错，可以自己增加出错信息格式的正则表达式。
编译模式命令速查表

| 键盘操作 | 命令名称 | 动作 |
| :--- | :--- | :--- |
| C-x ` | next-error | 移动到下一条出错信息并访问与之对应的源代码；前面加上C-u可以调到第一条出错信息；且在编译的过程中也可以使用 |
| M-n | compilation-next-error | 移动到下一条出错信息 |
| M-p | compilation-previous-error | 移动到上一条出错信息，这两条命令仅用于访问出信息 |
| C-c C-c | compilation-goto-error | 访问对应于当前出错信息的源代码 |
| SPACE | scroll-down | 下卷屏幕显示内容 |
| DEL | scroll-up | 上卷屏幕显示内容；这两条卷屏命令用于所有Emacs的只读模式的卷屏 |

grep命令提供多个文件里进行查找分析的能力，查找结果的查看操作同上表。

# 13. 第十三章 用LISP语言对Emacs做进一步开发
## 13.1 LISP语言
函数、变量、原子项是LISP语言最基本的元素。
## 13.2 LISP函数
函数是LISP语言中唯一的程序单元。由基本元素组成的list构成。
一切函数都有返回值：函数最后一个列表项的值
函数调用语句：(function-name grgument1 argument2 ...)
### LISP变量
LISP变量没有类型，可以取任何类型的值。
### 原子项
原子项是任意类型的值：整数、浮点数、字符串、布尔值、符号、缓冲区、窗口、进程等等
例子：setq可以一次对多个变量赋值
(setq thisvar thisvalue
      thatvar thatvalue
      auto-save-interval 800)
### LISP函数定义
变量名、函数名使用“-”作为间隔字符
程序大量使用“()”，即列表
例子：统计缓冲区单词个数
(defun count-word-buffer ()
  "Count the number of words in the current buffers;
print a messaage in the minbuffer with the result."
  (interactive)
  (let ((count 0))
    (goto-char (point-min))
    (while (< (point) (point-max))
	      (forward-word 1)
	      (setq count (1+ count)))
     (message "buffer words %d word" count)))

defun是一个函数，调用该函数时会定义一个新函数，其返回值就是新函数的名字；
函数的参数放在变量列表里，若参数前有“&optional”代表其是可选参数，默认值为“nil”
lambda用来定义匿名函数

(let ((val1 value1) (val2 value2) ...)
     statement-body)
let首先对变量进行定义并赋值，然后执行语句块中的内容。
let创建了一个知道那些变量的语句块，let语句块也称为变量的scope

(while condition
       statement-block)
## 13.3 把LISP函数转换成Emacs命令
interactive把函数注册为Emacs的一个命令，其必须紧跟在包含defun和文档字符串的那个代码行的后面，提示字符串用于提示用户输入在defun语句里声明的参数。
(interactive "sReplace string: \nsReplace string %s with:")
提示字符串格式要求：必须为每一个输入参数准备一个提示字符串的子字符串，自字符串之间使用LINEFEED"\n"分割，每一个子字符串的第一个字母必须是一个用来表示该参数类型的代码，常用参数类型代码：

| 参数类型代码 | 参数类型 |
| :--- | :--- |
| b | 一个现有编辑缓冲区的名字 |
| B | 一个肯存在的缓冲区的名字 |
| e | 事件（鼠标动作或功能键动作） |
| f | 一个现有文件的名字 |
| F | 一个可能不存在的文件的名字 |
| n | 整数 |
| N | 。。。 |
| s | 字符串 |
| S | 符号 |

interactive同样可以使函数被其他LISP代码调用。
### 文档字符串
documentation string简称doc string是用户发出在线求助命令时将看到的帮助信息，他是可选的，且长度是任意多行，但其第一行是用来对命令功能进行介绍的一个完整而又精炼的句子，字符串中的特殊字符需要转义。
## 13.4 LISP基础函数
LISP统一使用函数实现各种操作（比如其他程序语言使用的操作符）
算数运算：
+、-、*、/（加、减、乘、除）
%（求余）
1+（递增）
1-（递减）
max（最大值）、min（最小值）
比较运算：
>、<、>=、<=
/=（不等于）
=（数字和字符的相等）
逻辑运算：
equal（字符串及其他复杂的数据对象判断相等）
### 语句块
(progn
	statement-block)
(let (var1 var2 ...)
     statement-block)
(let ((var1 value1) (var2 value2) ...)
     statement-block)
(let (var1 (var2 value2) var3)
     statement-block)
(let* (var1 ...)
      statement-block)
### 控制结构
while、if、cond
### 正则表达式
## 13.5 定制主编辑模式
列表是LISP语言的一个基本概念。
Emacs的各个主编辑模式都有一些可以把自己的代码添加上去的挂钩“mode-hooks”，C模式有c-mode-hook，shell模式有shell-mode-hook
挂钩是一种特殊的变量，这些变量的值是一些LISP代码，在相应的编辑模式启动时得到运行。负责实现某个编辑模式的LISP代码留出一个位置，使你有机会改变他已经设置好的一些东西。
使用函数add-hook，
(add-hook 'mode-name-hook
	  (lambda ()
	  	  code-for-mode-hook))
编辑模式挂钩常用于为某个编辑模式的特殊命令修改一个或者多个按键绑定。

**如果只是给变量重新设置一个值，就不需要挂钩，但如果想运行函数，就必须使用挂钩。**
诸如c-macro-preprocessor之类的变量是属于编辑模式局部范畴之内的，如果没有启动对该模式做出定义的编辑模式，他们就不会存在。但只要“.emacs”文件包含一个给这个变量赋值的setq语句，那么不管是否使用该模式，这个变量就已经存在了，之后加载该模式，Emacs注意到已经设置过这个变量的值，于是就不会再覆盖掉他。
但函数就不同了，如果“.emacs”文件里有一个属于某个编辑模式的局部函数，Emacs无法得知该函数属于哪个编辑模式，更不用说起作用了，因此函数必须挂到某个模式上，等Emacs运行挂钩时，由于已经加载了该模式，就可以得知这个函数的作用。

总之挂钩可以让你在不触动实现编辑模式的LISP代码的前提下对他们进行各种各样的定制。
## 13.6 建立自己的LISP开发库
就像Emacs自带的lisp目录一样，Emacs的内建LISP代码都在这个目录里，建立自己的开发库，就能做到只在必要的时候加载必要的LISP程序包，不用再把他们全都塞到“.emacs”文件里。
创建一个目录，经自己的LISP代码全都放进去，然后告诉Emacs有这么一个目录。一般在全局变量load-path中设置，其是一个有字符串元素组成的列表，每个字符串是一个目录名。
(setq load-path (append load-path (list ("dir-path"))))
在.emacs文件中添加改行就可以，放在加载程序包命令之前
(setq load-path (cons load-path (list ("dir-path"))))
可使得Emacs查找自己的LISP子目录
有四种方法可以加载LISP程序包
* 输入用户级命令load-library
* 在.emacs中加上(load "package-name")
* 启动Emacs时加上“-l package-name”
* 在.emacs中加上(autoload 'function "filename")将在执行给定函数时自动加载相应的程序包
## 13.7 对LISP文件进行字节编译
如果对LISP文件进行了byte-compiling，即把文件中的LISP转换成字节代码，就能更有效的加载和使用它们，对LISP文件filename.el进行字节编译将创建出一个字节代码文件filename.elc
当load-library遇到参数“filename”时查找顺序：filename.elc、filename.el、filename
**compile-defun对某个函数进行编译**
**byte-compile-file对整个LISP文件进行编译**
**byte-recompile-directory对整个LISP文件目录进行重编译，且只编译更改的文件**

