(ch-风格-更高功能)=
# 词汇，特殊模块和更多样式

Jupyter 书提供了更多的选项来设计其章节并创建一本更全面的书。 在这个小章中，我们讨论了我们推荐在 _Ting ways_ 中使用的更多功能。

(ch-风格-更高功能-词汇)=
## Glossary

_诱惑路径_ 有一个 {ref}`词汇` 文件存放在书的后边。 它包括按字母顺序排列的不同术语的定义。 此文件可以用新术语的定义更新。 然后可以将其与该术语出现的书中的任何章节联系起来。

为新术语添加一条目， 请跳至 {ref}`词汇表` 文件的右侧字母部分，然后使用以下语法：

```
新术语-1
  定义该术语的短句。 这一句缩进下文。
```

例如， [个以“A”开头的术语](https://the-turing-way.netlify.app/afterword/afterword.html#a) 写在同一个文本块中，如下所示：
```

## A

```{glossary}

接受测试
 一个软件测试过程的水平，在这个过程中，一个系统被测试为可接受。 这次测试的目的是评价该系统是否符合项目要求，并评估它是否可以接受。

添加
 个命令用于将文件添加到暂存区域。 允许用户指定在下次提交中包含哪些文件或目录。

作者
  在这种情况下的作者是_Ting Way_project 的贡献者，他们为该项目作出了巨大贡献，例如撰写了一个小章， 促进社区互动，维持项目的基础设施，并通过辅导捐助支持其他人的参与。 所有作者都在整个书上被点名为共同作者。

```

要在术语表中引用术语，请使用语法 ``[{term}`def<Term>`]``

例如，将“作者”一词与其术语表文件中的定义联系起来， 请使用语法 ``[{term}`def<Authors>`]`` 此术语出现的旁边， 应该像这样渲染在线的作者: "*作者 [{term}`def<Authors>`] 已经在这里被引用。*"

(ch样式-更高功能-块)=
## 特殊内容块

在撰写新章节或修改现有章节时， 你不妨增添不符合该章其余部分的说明，但可能对读者有用，有助于他们更好地理解该章。

Jupyter 书允许使用特殊内容块来突出显示需要在页面上与其他内容不同的文字内容。 这个视觉地将文本块与页面其余部分分开，并确保它能够轻松地抓住读者的注意。

要将特殊内容块 (笔记、警告或警告) 添加到您的页面，请使用以下指令：

````
``{note}
这是一个示例说明！
```
````
变成：

```{note}
这是一个示例说明！
```

您可以给内容块自定义标题和样式来强化您的预定消息。 例如，如果你想要警告读者注意什么，你可以使用以下指令进行警告块：

````
``{warning}
这是一个严厉的警告！
```
````
请注意新的标题、图标和彩色方案。

```{warning}
这是一个严厉的警告！
```

有更多的方法自定义内容块以适应您的写作。 请参阅 [Jupyter 书文档](https://jupyterbook.org/content/content-blocks.html#notes-warnings-and-other-admonitions) and [Admonudy Demo 页面](https://sphinx-book-theme.readthedocs.io/en/latest/reference/demo.html#admonitions) 以了解更多建议。