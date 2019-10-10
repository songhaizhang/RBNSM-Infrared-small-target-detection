##  拓展语法
1. [x] 这是一个任务，没有完成
2. [ ] 这是另一个任务，已经完成

**笑脸**：:smile:
**卡车**：:fa-car:
**上标**：30^th^ 
**下标**：H~2~0
**脚注**： Content [^1]
**缩略**：The HTML specification. is maintained by the W3C.
**标记**：==marked==
**斜体**：*哈哈哈*
**转义**：\*哈哈哈\*
**加粗**：**哈哈哈哈**
**加粗斜体**：***哈哈哈***
**删除线**：~~哈哈哈~~
**空格**：&nbsp;hhh
**分割线**：
***
**缩进两字符:** 
&emsp;hhh

**表格**
| 水果        | 价格    |  数量  |
| ------   | :-----:   | :----: |
| 香蕉        | $1      |   5    |
| 苹果        | $1      |   6    |
| 草莓        | $1      |   7    |


**无序列表**：
+ hhh
+ eee
+ ddd

**单行代码**：
`include<stdio.h>`

**更改代码块字体大小**：
<font size=5>
**代码块**：
```
#include<stdio.h>

```
</font>

## 数学编辑
使用 KaTeX 或者 MathJax 来渲染数学表达式。
行内显示：$ \tilde{a} $，$ \overrightarrow{AB} $，$\sqrt{\smash[b]{y}}$
块内显示：
$$\iint (x^2+x)dx$$
$sigmod=\cfrac{1}{1+e^{-x}}$
下标：$a_2$
大括号：$\lbrace \rbrace$
开方：$\sqrt[3]{6}$
希腊字母：$\alpha \beta \gamma \eta \theta \lambda \mu \sigma \phi \psi \omega$
其他符号：$\pm \times \div \mid \leq \geq \sum \int \iint $

**公式等号对齐：**
$$
    \begin{aligned}
        Cov(X,Y)=&E[(X-E[X]))(Y-E[Y])]\\
                =&E[XY]-2E[Y]E[X]+E[X]E[Y]\\
                =&E[XY]-E[X]E[Y]
    \end{aligned}
$$

**求和：** 
$$
    \begin{matrix}
        \sum_{i=1}^m
    \end{matrix}
$$

## 图像
Markdown Preview Enhanced 内部支持 flow charts, sequence diagrams, mermaid, PlantUML, WaveDrom, GraphViz，Vega & Vega-lite，Ditaa 图像渲染。 你也可以通过使用 Code Chunk 来渲染 TikZ, Python Matplotlib, Plotly 等图像。
#### Flow Charts
```flow
st=>start: 开始:>
e=>end: 结束:>
op1=>operation: 操作1
sub1=>subroutine: 子程序
cond=>condition: Yes
or No?:>
io=>inputoutput: catch something...
para=>parallel: parallel tasks

st->op1->cond
cond(yes)->io->e
cond(no)->para
para(path1, bottom)->sub1(right)->op1
para(path2, top)->op1
```
[^1]: Hi! This is a footnote
*[HTML]: 超文本标记语言
*[W3C]:  世界 Web 联盟

