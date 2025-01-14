# NUDT硕士/博士论文Latex模版

本项目提供 NUDT 硕士博士论文Latex模板。

# 更新日志
- 2019.10.17 修正英文字体渲染效果与Word不一致的问题（主tex文件去掉lmodern宏包）；将英文摘要从“ABSTRACT”改为“Abstract”；修正a3cover的字体设置；模版默认使用ttf字体。
- 2019.10.12 更新原创性声明的格式；提供ttf和otf两种字体，ttf字体可以解决macOS上TexStudio内置pdf阅读器不显示中文的问题。
- 2018.04.27 更新为二〇一八年三月版本格式
- 2019.03.31 修正参考文献缩进格式；修正英文封面格式 （之前版本仅替换nudtpaper.cls和data/resume.tex）


# 编译环境
推荐的编译环境如下：

+ 编译器：Texlive 2016。
+ 编辑器：Texstudio。项目主页：[https://sourceforge.net/projects/texstudio](https://sourceforge.net/projects/texstudio)。Ubuntu可以直接通过命令在线安装：`sudo apt-get install texstudio`。其他操作系统需要从项目主页下载程序。

## Texlive 的安装方法

- Texlive 官网：<https://www.tug.org/texlive/acquire-netinstall.html>
- Windows 安装程序（在线）：<http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe>
- Ubuntu 可以直接通过命令在线安装：`sudo apt-get install texlive-full`
- macOS 安装方法：<http://www.tug.org/mactex/>


# 依赖的字体

使用此模板需要下载安装配套字体（二选一即可）：

+ [ttf字体下载(Windows字体，与Word一致)](https://github.com/TomHeaven/nudt_thesis/releases/download/v1.1/ttf.zip)
使用ttf需要修改入口thesis.tex / thesis_blind.tex，确保documentclass的字体参数为

```
\documentclass[doctor,ttf]{nudtpaper}   % ttf字体
```

+ [otf字体下载（Adobe字体，更好看）](https://github.com/TomHeaven/nudt_thesis/releases/download/v1.1/otf.zip)
使用otf需要修改入口thesis.tex / thesis_blind.tex，确保documentclass的字体参数为

```
\documentclass[doctor,otf]{nudtpaper}   % otf字体
```

# 用法

+ 用texstudio打开 thesis.tex，设置封面相关个人信息，编译生成论文盲评版。thesis.tex包含data目录下的chap0X.tex文件为论文的各个章节。ref/refs.bib是参考文献。注意documentclass的第一个参数为`doctor`是博士论文，而为`master`则是硕士论文：

```
\documentclass[doctor,ttf]{nudtpaper} % 第一个参数表示博士论文，第二个参数表示ttf字体
```
+ 用texstudio打开 thesis_bind.tex，设置封面相关个人信息，编译生成论文盲评版。
+ 用texstudio打开 a3cover目录下的 spine.tex，，设置封面相关个人信息，编译；再打开a3cover.tex，编译，可以得到A3纸论文封面。
+ word文件夹下有官方word模版，如果发现Latex模版有任何问题可以江湖救急。



# macOS 系统 TexStudio 内置 pdf 阅读器不显示中文

macOS系统中，TexStudio内置的pdf不显示otf字体（文档本身没有问题，其他阅读器可以正常显示）。解决方案有两种：
1. 使用ttf字体。
2. 强制嵌入字体到pdf。将字体内嵌入 pdf 文件的命令如下：

```
pdf2ps  name.pdf  # pdf 转换成 ps 文件
ps2pdf14 -dPDFSETTINGS=/prepress name.ps # ps 转换成 pdf 并嵌入字体
```

据此提出以下解决方案：

+ 在 texstudio 的“选项”->“构建”中勾选“显示高级选项”，并添加用户命令“embedfonts:embedfonts”：

```
pdf2ps %.pdf | ps2pdf14 -dPDFSETTINGS=/prepress %.ps | rm %.ps
```
+ 修改默认构建命令如下：

```
txs:///xelatex | txs:///embedfonts
```

点击"编译"按钮，则论文可以正确显示了。使用此方案前请确保 pdf2ps，ps2pdf14 命令在系统 PATH 中，并且可以正确执行。注意这个方案会使得 Adobe Acrobat 对pdf 的编辑能力下降，如果最终版本不需要嵌入字体，可以先还原默认构建命令为 XeLaTex，再编译提交。

# 致谢

本模版修改自这些前辈们的工作：

+ LiuBenYuan <liubenyuan@gmail.com>：Github项目[https://github.com/liubenyuan/nudtpaper](https://github.com/liubenyuan/nudtpaper)
+ Ruini <xueruini@gmail.com> 
+ sofoot

在此表示感谢！

# 免责声明

本模板免费提供于同学们使用或修改，但 is provided "As IS"。使用本模板产生的任何问题作者不承担任何直接或者间接责任。但作者会尽力帮助有需要的同学解决问题。

