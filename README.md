# pkuszdp: LaTeX template for dissertation proposals in Peking University Shenzhen

> 基于北大硕士论文模板: [Thesharing/pkuthss](https://github.com/Thesharing/pkuthss)

本项目是**非官方** LaTeX 版的北京大学深圳研究生院的开题报告，已按照官方 Word 模板进行修改。但需要注意，本模板生成的文件与 Word 版**并非完全相同**，如封面校徽改为新版，以及封面的论文题目字体按照《北京大学研究生论文写作指南》中要求改为黑体，作者等信息改为仿宋字等。

## 使用指南

1. 推荐阅读原 repo 中的 [`README.md`](https://github.com/asuith/pkuszdp#pkuthss-latex-template-for-dissertations-in-peking-university)。
2. 安装 LaTeX 环境。
3. 使用本项目编写开题报告，按需修改以下内容：

```text
thesis.tex -> 封面信息
chap/*.tex -> 各章节内容
thesis.bib -> BibTeX 格式的文献
image/*.* -> 图片，当然也可随意放置
```

在 Windows 下，双击 `Make.bat` 即可编译，大约需要 30-60s 时间，生成的 `thesis.pdf` 即为开题报告。


## 注意事项

1. LaTeX 有一定门槛，建议先简单入门之后再使用本项目。
2. 按照 Word 模板来看，《个人简介》这一章节应当和前一章节放在一起，因此用了一点丑陋的代码实现。
3. 《个人简介》中的个人照片，和右侧文本难以对齐，笔者能力有限，只能在图片下面手动添加白色空白区域，以达到视觉上的对齐。
4. 如需要转 Word 版本（如某学院查重需要提交此版本），可使用 PDF 转 Word 服务，如 Adobe 提供的 [Convert PDF to Word](https://acrobat.adobe.com/link/acrobat/pdf-to-word/)。经2022年初测试，后者的转换虽然对于单行公式的处理较差，但其他部分可以满足除列文虎克的要求。

如遇到问题，欢迎自行解决后提交 PR，毕竟笔者也不一定能解决。以下为原模板 `README.md` 内容。

---



# pkuthss: LaTeX template for dissertations in Peking University

Source: [CasperVector/pkuthss](https://github.com/CasperVector/pkuthss)

## Changes

相比于原模板有以下改动：

* 修改了copy.tex的行距
* 修改了origin.tex的勾选框和行距
* 将make.bat和Makefile中默认编译方式改为xelatex
* 将Hyperlink的颜色修改为黑色
* 为目录添加了点线
* 增加了`nopkumathfont`选项，仅将数学公式字体恢复为默认字体
* 将页眉修改为“硕士学位论文”（如果需要修改成其他的，参考pkuthss.cls的313行）
* 修改了封面标题的字体大小
* 为中英文关键字添加了缩进
* 将Bibtex模板由CapserVector改为biblatex-gb7714-2015

## Environment

参考 [VSCode + LaTeX](https://zhuanlan.zhihu.com/p/108095566)

For TeX compiler:

1. Install TeXLive 2020 [here](https://www.tug.org/texlive/).

For editor:

1. Install Visual Studio Code [here](https://code.visualstudio.com/).
2. Install LaTeX Workshop [here](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
3. Install LaTeX Untilities [here](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities).

For bibliography:

1. Install Zotero [here](https://www.zotero.org/download/).
2. Install ZotFile [here](http://zotfile.com/).
3. Install Better BibTex for Zotero [here](https://github.com/retorquere/zotero-better-bibtex).

Recommend:

Use [MathPix Snip](https://mathpix.com/) to OCR the equations.

## Compile

For Windows, run `make.bat doc`.

For Linux/macOS, run `make doc`.

## Reference

1. [TeX Live + pkuthss 安装使用傻瓜指南 v0.1.6](https://bbs.pku.edu.cn/v2/post-read-single.php?bid=346&type=0&postid=18114839)
2. [CasperVector/pkuthss](https://github.com/CasperVector/pkuthss)
3. [hushidong/biblatex-gb7714-2015](https://github.com/hushidong/biblatex-gb7714-2015)
3. [VSCode + LaTeX](https://zhuanlan.zhihu.com/p/108095566)
4. [使用VSCode编写LaTeX](https://zhuanlan.zhihu.com/p/38178015)
5. [VS Code 与 LaTeX 真乃天作之合](https://www.jianshu.com/p/57f8d1e026f5)

## Appendix

### LaTeX Workshop Setting

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }, 
        {
            "name": "biber",
            "command": "biber",
            "args": [
                "-l",
                "zh__pinyin",
                "--output-safechars",
                "%DOCFILE%"
            ],
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "Compile thesis",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        }
    ]
}
```

