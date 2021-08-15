# $\LaTeX$ Notes

#LaTeX 

## Some Commands

### @{\extracolsep{\fill}} 

如何让表格填满
\begin{tabular*}{\linewidth}{@{\extracolsep{\fill}}c|ccccc|ccccc}
其中 @{\extracolsep{\fill}} 就是用来干这个的.

### \relax

简单来讲就是，什么都不做。防止在此之前的命令扩展到后面。

[macros - What is the difference between \relax and {}? - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/86385/what-is-the-difference-between-relax-and)

[macros - What does \relax do? - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/96501/what-does-relax-do)



## Hyperlinks 超链接

调用package：

```latex
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=blue,      
    urlcolor=blue,
    citecolor=cyan,
}
```



直接引用：

```latex
\url{https://blog.mikelyou.com}
```

链接文本与地址不同：

```latex
\href{https://blog.mikelyou.com}{采叶小火的博客}
```

邮箱：

```latex
\href{mailto:liuch259@outlook.com}{liuch259@outlook.com}
```

电话：

```latex
\href{tel:1XXXXXXXXXX}{1XX-XXXX-XXXX}
```

本地文件：

```latex
打开文件 \href{run:./file.txt}{File.txt}
```

## CLS文件

### cls文件是什么？

LaTex中常见的文件格式有.tex, .bib, .cls, .sty, .bbl等，.tex文件也就是我们写文档内容的文件，.bib是使用bibligraphy方式导入参考文献时，写参考文献的文档，.bbl是其编译之后形成的文件，.sty是包文件，通常使用\\usepackage导入，.cls是类文件，通过文档最前面的\\documentclass命令导入~ 



## Command 命令

### Defining a new command

#### Simple commands

```latex
\newcommand{\R}{\mathbb{R}}

The set of real numbers are usually represented by a blackboard bold capital r: \( \R \).
```

![](2020-10-31-latex-notes-img/CommsAndEnvsEx3.png)

The statement `\newcommand{\R}{\mathbb{R}}` has two parameters that define a new command

- `\R`

  This is the name of the new command.

- `\mathbb{R}`

  This is what the new command does. 

#### Commands with parameters

```latex
\newcommand{\bb}[1]{\mathbb{#1}}

Other numerical systems have similar notations. 
The complex numbers \( \bb{C} \), the rational 
numbers \( \bb{Q} \) and the integer numbers \( \bb{Z} \).
```

![CommsAndEnvsEx4.png](2020-10-31-latex-notes-img/CommsAndEnvsEx4.png)

The line `\newcommand{\bb}[1]{\mathbb{#1}}` defines a new command that takes one parameter.

- `\bb`

  This is the name of the new command.

- `[1]`

  The number of parameters the new command will take.

- `\mathbb{#1}`

  This is what the command actually does. In this case the parameter, referenced as #1, will be written using blackboard boldface characters. If the defined new command needs more than one parameter, **you can refer each parameter by #1, #2 and so on**, up to 9 parameters are supported.

#### Commands with optional parameters

```latex
\newcommand{\plusbinomial}[3][2]{(#2 + #3)^#1}

To save some time when writing too many expressions 
with exponents is by defining a new command to make simpler:

\[ \plusbinomial{x}{y} \]

And even the exponent can be changed

\[ \plusbinomial[4]{y}{y} \]
```

![CommsAndEnvsEx5.png](2020-10-31-latex-notes-img/CommsAndEnvsEx5.png)



Let's analyse the syntax of the line `\newcommand{\plusbinomial}[3][2]{(#2 + #3)^#1}`:

- `\plusbinomial`

  This is the name of the new command.

- `[3]`

  The number of parameters the command will take, in this case 3.

- `[2]`

  Is the default value for the first parameter. This is what makes the first parameter optional, if not passed it will use this default value.

  第一个参数的默认值。如果需要多个科学参数，看[这个](https://tex.stackexchange.com/questions/29973/more-than-one-optional-argument-for-newcommand)

- `(#2 + #3)^#1`

  This is what the command does. In this case it will put the second and third parameters in a "binomial format" to the power represented by the first parameter.

  

### Overwriting existing commands

  如果你一定要定义一个已经存在的 latex 命令，也是可以做到的。使用 `\renewcommand`，语法与 `\newcommand` 一样。

## Environments 环境

Environments are used to format blocks of text in a LATEX documents. 
环境是用来格式化LATEX文档中的文本块的。

比如最常见的 `center`

```
\begin{center}
This text will be centred since it is inside a special 
environment. Environments provide a efficient way of modifying 
blocks of text within your document.
\end{center}
```

![CommsAndEnvsEx7.png](2020-10-31-latex-notes-img/CommsAndEnvsEx7.png)

In this example all the text inside the *center* environment is centred.



Environments are delimited by an opening tag `\begin` and a closing tag `\end`. Everything inside those tags will be formatted in a special manner depending on the type of the environment. 环境由开启标签 `\begin` 和关闭标签 `\end` 定界。在两个标签之间的所有内容都会根据环境的种类被格式化。

```
\begin{tabular}{ c c c } 
  cell1 & cell2 & cell3 \\ 
  cell4 & cell5 & cell6 \\ 
  cell7 & cell8 & cell9 \\ 
 \end{tabular}
```

![CommsAndEnvsEx11.png](2020-10-31-latex-notes-img/CommsAndEnvsEx11.png)

This environment *tabular* takes an additional argument `{ c c c }` to determine the alignment of the cells (See the [Tables](https://www.overleaf.com/learn/Tables) article for more information).

### Defining a new environment

#### Defining simple environments

The new environment definition is achieved by the `\newenvironment` tag:

```latex
\newenvironment{boxed}
    {\begin{center}
    \begin{tabular}{|p{0.9\textwidth}|}
    \hline\\
    }
    { 
    \\\\\hline
    \end{tabular} 
    \end{center}
    }
%--------------------------------------------------

Below this line a boxed environment is used

\begin{boxed}
This is the text formatted by the boxed environment
\end{boxed}

This text is again outside the environment
```

![CommsAndEnvsEx8.png](2020-10-31-latex-notes-img/CommsAndEnvsEx8.png)



This environment will draw a box around the text within.

Right after the `\newenvironment`, in between braces, you must write the name of the environment, *boxed* in the example. Below that are two pairs of braces. Inside the first pair of braces is set what your new environment will do **before** the text within, then inside the second pair of braces declare what your new environment will do **after** the text.

In the example, in between the *before* braces a *tabular* environment is started to draw the vertical lines and a horizontal line is drawn. Inside the *after* braces another horizontal line is drawn and the *tabular* environment is closed. Additionally it's enclosed by a *center* environment.

## 参考文献：

1. [Hyperlinks - Overleaf, Online LaTeX Editor](https://www.overleaf.com/learn/latex/hyperlinks)
2. [LaTeX超链接hyperref - 简书](https://www.jianshu.com/p/ab7c3f3a4684)
3. [【LaTex】cls文件编写和使用入门 - 知乎](https://zhuanlan.zhihu.com/p/77537952)：