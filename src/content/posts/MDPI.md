---
title: MDPI模板使用和LaTeX一些排版技巧	
published: 2023-01-30
#image: ''
tags: ["LaTeX技巧"]
category: Blog
draft: false 
---


最近在投MDPI旗下的RS期刊，这也是我第一次用LaTeX写正式的学术论文，之前用模板写实验报告啥的和这个玩意都不是一个难度，故此记录下这篇文章写作时的一些注意事项和排版技巧等，作为存档。

# 1. MDPI模板
本次写作是多人协同，我们采用了overleaf平台，MDPI也有提供[overleaf平台模板](https://www.overleaf.com/latex/templates/mdpi-article-template/fcpwsspfzsph)，导入后即可进行写作。
![NgpSV.png](https://i.328888.xyz/2023/02/04/NgpSV.png)

# 2. LaTeX分节写作
在写作时，最好运用分节写作，可以更清晰的对文章进行创作，操作如下：
1. 创建一个`main.tex`，在里面写入
```
\begin{document}
   \input{1-abstract}
   \input{2-introduction}
   \input{3-model}
   \input{4-data}
   \input{5-solve}
   \input{6-conclusion}
   \input{7-acknowledgment}
   \bibliography{Reference}
   \bibliographystyle{abbrv}
   \end{document}
```

其中`\input{}`就是导入其他的子章节

# 3. 表格
表格建议采用LaTeX表格编辑器，现在本地Excel上写好你的表格数据，导入[LaTeX表格编辑器](https://www.latex-tables.com/)中，或者[TablesGenerator](https://www.tablesgenerator.com/)，设置格式和颜色什么的，完成后点击`Generate`即可导出代码，粘贴到你的文章中即可。
![NgXid.png](https://i.328888.xyz/2023/02/04/NgXid.png)


## 3.1表格（图片）居中
在`\begin{figure}[htbp]`下采用以下指令：
```
\centering
```
不起作用时，可以采用
```
\begin{figure}[htbp]
\resizebox{\textwidth}{!}

}
\end{figure}
```



# 4.图片排版

图片最好选用PDF或者EPS格式的矢量图，不会糊，用[PNG转PDF工具](https://png2pdf.com/zh/)即可转换。

## 4.1 插入一张图片
```
\begin{figure}[htbp]
\centering
\includegraphics[scale=0.2]{name.pdf}
\caption{figure title}
\label{figure}
\end{figure}
```
其中，`htpb`是控制图片位置，为一般使用 [htb] 这样的组合，这样组合的意思就是Latex会尽量满足排在前面的浮动格式，就是 h-t-b 这个顺序，让排版的效果尽量好。
         [h] 表示将表格放在当前位置。
         [t] 表示将表格放置在页面的顶部。
         [b] 表示将表格放置在页面的底部。
         [p] 将表格放置在一只允许有浮动对象的页面上。

`[scale]`，表示按原图比例缩放，比如 `scale=0.2`表示将原图缩小 5 倍，如果要放大只需要将 `scale` 设置为大于 1 即可；
还可以直接设置图片宽高，比如 `[height = 1cm, width = 2cm]`。

## 4.2 插入多张图片
## 4.2.1 一横排4张
```
\begin{figure}[htbp]
\centering
\subfigure
{
    \begin{minipage}[b]{.2\linewidth}
        \centering
        \includegraphics[scale=0.1]{name.pdf}
    \end{minipage}
}
\subfigure
{
 	\begin{minipage}[b]{.2\linewidth}
        \centering
        \includegraphics[scale=0.1]{name.pdf}
    \end{minipage}
}
\subfigure
{
 	\begin{minipage}[b]{.2\linewidth}
        \centering
        \includegraphics[scale=0.1]{name.pdf}
    \end{minipage}
}
\subfigure
{
 	\begin{minipage}[b]{.2\linewidth}
        \centering
        \includegraphics[scale=0.1]{name.pdf}
    \end{minipage}
}
\caption{figure title}
\end{figure}
```

在代码中，`{.2\linewidth}`表示一行可以放5张图片，`.2`这个数字可以更改为你想要的。如你想一行三图，则改为`.3`即可。

效果如图所示：
![NxgsH.png](https://i.328888.xyz/2023/02/04/NxgsH.png)


若想为图片加入标号上例其余代码不变，只需要在 subfigure 后加一个方括号 [] 即可。

## 4.2.2多行多列排版
实现代码
```
\begin{figure}[htbp]
\centering
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\subfigure[]{
\begin{minipage}[b]{.3\linewidth}
\centering
\includegraphics[scale=0.1]{name.pdf}
\end{minipage}
}
\caption{figure title}
\end{figure}

```
效果如图所示：

![NxE8E.png](https://i.328888.xyz/2023/02/04/NxE8E.png)

这里就是简单地叠加 `subfigure`，控制一行放几张图片的关键还是在于 `minipage` 的 `{.3\linewidth}`，设置为 .3 就意味着一行至多放三张，后面的图片会自动换行。

这里将每张图片作为了一个 `subfigure`，如果有必要为每张图添加单独的序号或图例说明，根据前面讲的给 `subfigure` 加 [] 就可以。

## 4.3其他
1. 图标题格式

论文里可能要求图片标题为 `Fig. 1.`，而有的模版生成出来的是 `Figure. 1`.，此时只需要在 `\begin{document} `后面放上 `caption` 的格式控制命令：
```
\begin{document}\sloppy
\captionsetup[figure]{labelfont={bf},name={Fig.},labelsep=period}
```
`bf` 表示加粗，`name` 是要显示的名字，`labelsep` 是名称和序号之间的分隔符，`period` 表示用句号分隔，`space` 表示用空格分隔，没有参数就默认使用冒号分隔。

对于表格也同理，修改自己需要的 `name` 即可：
```
\captionsetup[table]{labelfont={bf},name={Table},labelsep=period}
```

# 5.引用格式
我采用谷歌学术进行引用，先打开[谷歌学术](https://scholar.google.com/)网站
![NxdMJ.png](https://i.328888.xyz/2023/02/04/NxdMJ.png)
对文章的标题进行搜索，得到这个界面：
![NxSmA.png](https://i.328888.xyz/2023/02/04/NxSmA.png)
点击引用图标，
[![NxvyN.png](https://i.328888.xyz/2023/02/04/NxvyN.png)](https://imgloc.com/i/NxvyN)
选择`Bibtex`，之后会跳转到一个纯黑界面
![NxJGd.png](https://i.328888.xyz/2023/02/04/NxJGd.png)
复制其中的代码到你`Overleaf`的`Reference.bib`中即可使用；

在你的文章中输入`\cite{bertinetto2016fully}`即可引用SiamFC这篇文章。若想多个引用，采用`\cite{a,b}`即可同时引用两篇文献。