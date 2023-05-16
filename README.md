# QLUThesisLatexTemplate

# 说明

齐鲁工业大学本科生毕业论文 LaTeX 模版。

# 为何使用 LaTeX

在刚刚结束的毕业设计撰写中，很多使用 Word 的同学在写作过程中出现大量难以解决的格式问题，非常头疼。LaTeX 虽然学习曲线较为陡峭，但花费一个小时左右时间熟悉后即可完全专注于内容撰写而无需操心任何格式问题。本模版即旨在你只需复制粘贴修改具体内容即可作出 __基本__ 符合齐鲁工业大学现行规范的毕业设计。供后人参阅

LaTeX 加本模板可以实现：

* 无比优雅的数学公式
* 章节的自动标号
* 公式的自动标号
* 插图的自动标号
* 表格的自动标号
* 目录的自动生成
* 参考文献和标引的自动标号
* __所有格式的自动正确__

# 如何使用本模板

## 基本使用

首先请阅读文档《[一份不太简短的 LaTeX 介绍](http://www.ctan.org/tex-archive/info/lshort/chinese/)》，了解 LaTeX 的基础语法。

打开 `Thesis/preface/cover.tex`，修改封面内容。注意封面论文题目需要在format.tex处更改。

打开 `Thesis/body.tex`，开始根据示例书写你的毕业设计。绝大部分需求（标引、插图、表格、数学公式、代码环境）等均在示例中有所体现，可直接复制粘贴修改内容。

打开`Thesis/abstract.tex`，修改你的摘要信息，包括英文摘要和中文摘要。

打开`Thesis/qlumain.tex`，修改你的字体信息。包括页眉页脚，以及目录的页码改成罗马数字。

打开`Thesis/package.tex`，修改宏包。

打开`Thesis/format.tex`，修改各种各样自定义的格式。

打开`Thesis/AppendicesandAcknowledgements.tex`，加入需要添加的附录代码和致谢。

```
smile.py
\lstinputlisting[language=python]{code/smile.py}
```

在目录`code/`中添加代码。

## 参考文献

所有参考文献在 `Thesis/references/reference.bib` 中。BibTex 格式的参考文献可通过以下步骤获得：

* 打开浏览器，访问 [Google Scholar](http://scholar.google.com)

* 查找你所需的文献

* 点击文献下方 引用/cite 按钮

* 在弹出框内点击 BibTex

* 复制新窗口里的文本粘贴到 reference.bib 中

* 在 body.tex 中需要引用的地方使用`\cite{}`命令进行引用，括号里填参考文献第一行左花括号后面的 identifier。

  例如有这样一篇bib格式的参考文献：@INPROCEEDINGS{6909475,

  ```
  @INPROCEEDINGS{6909475,
  	author={Girshick, Ross and Donahue, Jeff and Darrell, Trevor and Malik, Jitendra},
  	booktitle={2014 IEEE Conference on Computer Vision and Pattern Recognition}, 
  	title={Rich Feature Hierarchies for Accurate Object Detection and Semantic Segmentation}, 
  	year={2014},
  	volume={},
  	number={},
  	pages={580-587},
  	doi={10.1109/CVPR.2014.81}}
  ```

  在文中在需要的地方添加**\cite{6909475}**（数字就是上面bib文本中的第一个数字序列，可以自定义），就能引用你需要的参考文献了。

## 目录，字体，字号，编号，序号，页码，页眉，排版...

全都是自动的。

# 关于本魔改

本魔改适用于Texstudio，使用 `xelatex->bibtex->xelatex->xelatex` 编译链。在 macOS, Windows 10 下进行修改与测试，无法完全保证其它平台的正常使用。希望 Linux 用户踊跃反馈。

## 魔改内容

* 移除 CJK，使用 ctex
* 根据现行本科生毕业论文规范修改格式
* 适应 macOS, Windows 与 xelatex
* 为适应我推荐的工具链做了一些优化

## 编译

> - 编译操作**在 `qlumain.tex` 所在目录下进行**
> - 以下编译方式任选其一即可

### Visual Studio Code

在应用推荐工具链后，打开 `qlumain.tex`，执行 Ctrl + Alt + B；或点击左侧 TEX Tab 并单击 Build LaTeX project。

### 使用`Latexmk`编译

```bash
latexmk -pvc -xelatex -file-line-error -interaction=nonstopmode -synctex=1 qlumain.tex
```

### 手动编译

**依次运行**以下四条命令：

```bash
xelatex qlumain.tex
bibtex qlumain.aux
xelatex qlumain.tex
xelatex qlumain.tex
```

注意：由于存在目录、参考文献和图表编号等，需要多次编译以保证顺序正确。

## 清理缓存及日志

### Atom

安装插件 `language-latex` 和 `latex`，提供 Build 和 Clean 的功能。

### Visual Studio Code

安装插件 `LaTeX Workshop`，提供 clean up。

### Latexmk

```bash
latexmk -c
```

### 其他

也可使用 [@Halcao](https://github.com/Halcao) 提供的小脚本 `Thesis/clean.sh`。

# 推荐工具链

* 发行版
  * macOS: MacTex
  * Windows: TeX Live
* Visual Studio Code
  * LaTeX Workshop
* Atom
  * language-latex
  * latexer
    * latextools
* Sublime Text 3
  * LatexTools
  * Latex-cwl
  * LatexWordCount

注意：直接使用 VSCode 打开本项目可以自动获得推荐插件与设置。如需自行配置，可参考本项目下 [.vscode/settings.json](https://github.com/twtstudio/TJUThesisLatexTemplate/blob/master/.vscode/settings.json)。

# 致谢

qluthesis 的原作者们作出了前人栽树的不可磨灭的贡献：

本模板主要借鉴于天津大学本科latex论文模板，在这里无比感谢前人的栽树！

* 张井 天津大学2010级管理与经济学部信息管理与信息系统专业硕士生
* 余蓝涛 天津大学2008级精密仪器与光电子工程学院测控技术与仪器专业本科生

以及北京大学孟祥溪院士。

- 李赟博 齐鲁工业大学 2019级数学与人工智能学院智能科学与技术专业本科生



# License

由于原项目使用 GNU GPL v3 协议，本项目作为基于 qluthesis 的衍生项目，仍保持 GNU GPL v3 协议。



# 5月16日更新内容

1. 取消了中英文摘要关联在封面中，单独定义了abstract.tex文件进行编译，使得摘要可以在目录之下。
2. 目录部分单独用罗马数字编码。
3. 摘要部分适配了页眉。

## 待更新内容

扉页部分尚未添加，敬请期待。可以word转pdf后插入也很方便。

目录中的摘要、参考文献、附录、致谢部分尚未顶格，敬请期待后续更新。读者可以通过修改pdf使其顶格。
