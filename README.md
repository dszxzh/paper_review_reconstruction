
# IEEE-latex-template-v2

## 1. 说明

实验室IEEE论文模板。目前，模板更新为v2，原有模板Repo不再使用；新增、修改的功能、内容如下：

1. 更新为IEEE官方最新的模板，其中tex保存在\src文件夹下；当前的arcticle.tex文件，源自bare_jrnl.tex。
2. 更改math.tex的使用方法，使用更加简洁，命令的格式如下：

```latex
\newcommand{\maxwell}
{
    \begin{align}
    \nabla\times {\mathbf{E}}&=-\frac{\partial {\mathbf{B}}}{\partial t}  \\
    \nabla\times {\mathbf{H}}&={\mathbf{J}}+\frac{\partial {\mathbf{D}}}{\partial t}  \\
    \nabla\cdot {\mathbf{B}}&=0  \\
    \nabla\cdot {\mathbf{D}}&=\rho 
    \label{eq:maxwell}
    \end{align}
}
```
3. 增加sec_appdendix.tex，列出math.tex中所有的公式；
4. 增加biography.tex，可列出作者简历；


## 2. 文件夹的使用

为避免REPO文件过大，对文件夹的使用做以下约定：

1. 论文直接用到的图像文件，如pdf、jpg、png，才可以放置于figure/下，单个文件尽量不超过5MB；
2. 论文用图的源文件及各种数据文件，如visio、mp、excel、mat等，都放置在根目录的exclude文件夹下。
3. 在.gitignore文件中添加exclude，这样所有exclude文件夹下的文件都不会同步到github上，可从而避免repo过大。


## 3. 模板使用

### 3.1 题目

修改文件"article.tex"中的内容，如下：

```latex

\title{Bare Demo of IEEEtran.cls\\ for IEEE Journals}


\author{
  Ziqiang Cui,~\IEEEmembership{Member,~IEEE,}
  Andy~Lau, 
  and~Huaxiang~Wang,~\IEEEmembership{Senior~Member,~IEEE}% <-this % stops a space
\thanks{Dr. Ziqiang Cui was with the School of
of Electrical and Information Engineering, Tianjin University, Tianjin 300072, China.
Correspondance e-mail: cuiziqiang@tju.edu.cn.}% <-this % stops a space
\thanks{This research is financially supported by NSFC, Nos. 61671319 and 61627803.}% <-this % stops a space
\thanks{Manuscript updated \today and submitted Feb 28, 2020.}}

```



### 3.2 Sections
各节的tex文件位于“sections”文件夹中，如：

```latex
sections/sec_intro.tex
sections/sec_method.tex
sections/sec_results.tex
sections/sec_cons.tex
```

在文件``article.tex''中，上述tex文件的组织如下：

```latex
\input{section/sec_intro.tex}
\input{section/sec_method.tex}
```


### 3.3 图表

图像文件转到`figures`目录。
将文件放在此处，并将其包含在文档正文中。


matlab导出高清图的命令：

> print -djpeg -r600 out_file_name

参数说明 [ -djpeg 输出的照片格式，可选参数：'-djpeg' | '-dpng' | '-dtiff' | '-dpdf' | '-deps' -r600 输出的清晰度 out_file_name 输出的文件名 ]

编辑matlab生成图像の黑科技：

> 在图像输出框点击编辑-复制图形-粘贴至visio中-右键取消所有组合-编辑图像-导出图像



latex在线制作表格，自动生成代码：
> http://www.tablesgenerator.com/#

### 3.4 文献管理

文献管理推荐使用Jabref、Zotero或其他支持bibtex的软件。

IEEEtran规范要求打印文章书目，您必须至少具有
文档中的一个引用，否则您将收到编译错误。为了解决这个问题，我们
定义我们位于变量文件中的“ hasBibliography”变量：

```latex
\def \hasBibliography{1}
```
默认值指定必须生成书目。如果您不想要，只需将变量值更改为0。
要在文档中引用书目条目，可以使用以下命令：

```latex
\cite{johndoe}
```

### 3.5 首字母缩略词

首字母缩略词列表位于```acronyms / acronyms.tex```。要在文档中定义新的首字母缩写词，必须在该文件中定义新的条目：

```latex
\newacronym{<label>}{<abbreviation>}{<full>}
```
要引用首字母缩写词，可以使用：

```latex
\gls{<label>}
```
如果您是第一次使用首字母缩写词，它将在您的文档中显示```<abbreviation>```和
```<full>```标签。在其余引用中，它将仅显示```<abbreviation>```标签。

要以复数形式引用首字母缩写词，可以使用以下命令：

```latex
\glspl{<label>}
```

可以在[LaTeX词汇表Wiki]（https://en.wikibooks.org/wiki/LaTeX/Glossary）上获取“缩略语”包的完整文档。

## 4. 其他
### 4.1  TeX软件

* 建议使用最新版的TexLive软件（实验室FTP），使用pdflatex编译。
* 推荐使用VS Code（搭配插件Latex Workshop）编辑TeX文件。

### 4.2 脚本

脚本是一种高效的工作方式，化繁为简。在Windsows下，需要安装git软件（https://gitforwindows.org/）, 直接双击即可运行。在文件夹下，包含以下脚本文件：

* 0_Compile2PDF.sh: 编译为pdf文件；
* 1_clean.sh: 清除无用的文件内容；
* 2_autopush.sh: 提交文件至github。


### 4.3 检查论文

* 格式方面的问题可参考： https://github.com/etgroup/paper_checklist 
* 论文拼写错误，句法错误应当完全避免，可以使用一些带语法检查功能的软件，如Word，Grammarly等。


#  论文框架

## 1 Introduction

### 1.1 重建算法知识总体系

### 1.2 前人的综述和我们的工作

### 1.3 近年研究热点与倾向

## 2 Development of image reconstruction algorithm

### 2.1 正则化

### 2.2 边界映射

### 2.3 深度学习

### ……

## 3 Evaluation of algorithms 

### 精度、速度与适用范围

## 4 Conclusion

### 总结方法特点，建议未来发展方向




