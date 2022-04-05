(pd-code-styling)=
# Code Styling and Linting

Have you ever opened a syntax or script file two years after running an analysis only to find that you have no immediate memory of the code? Have you received analysis files from a collaborator, or downloaded them from an online repository that you have never used before? 现在想象这些文件很难读取，或者有许多变量被传递到奥术函数中。 或者更糟糕的是，你找不到有用的代码，因为它们是用没有意义的文件名保存的，例如 `analysis_1final_FINAL。 `, 或 `onethisoneforanalysis_onamonday2a.py`.

If you have not - then you are one of the lucky ones! But if you have experienced it then you might know how frustrating it is to work with those files.

This chapter will highlight ways to avoid such challenges in your projects by introducing some principals of 'code hygiene', otherwise known as *linting*.

```{figure} ../figures/zen-of-python.png
---
高度：500px
name: zen-fython
alt: The Zen of Python, by Tim Peters. 美丽胜于丑恶。 Beautiful is better than ugly. Explicit is better than implicit. Simple is better than complex. Complex is better than complicated. Flat is better than nested. Sparse is better than dense. Readability counts. Special cases aren't special enough to break the rules. Although practicality beats purity. Errors should never pass silently. Unless explicitly silenced. In the face of ambiguity, refuse the temptation to guess. There should be one-- and preferably only one --obvious way to do it. Although that way may not be obvious at first unless you're Dutch. Now is better than never. Although never is often better than *right* now. If the implementation is hard to explain, it's a bad idea. If the implementation is easy to explain, it may be a good idea. Namespaces are one honking great idea -- let's do more of those!
---
*Point 7 of the [Zen of Python](https://www.python.org/dev/peps/pep-0020/) is "Readability Counts". (可以使用 python 命令打印。 >>> 导入此命令)*
```

## Overview

链接包含 {ref}`样式准则<pd-code-styling-guidelines>` 比如命名， 并确保代码为 {ref}`可读<pd-code-styling-readability>` 例如使用有用的格式化和撰写评论。   
一些综合发展环境包括自动行号， 但有空闲的 {ref}`软件包和工具用于lining<pd-code-styling-tools>` 将为您联接代码 (例如) [autopep8](https://pypi.org/project/autopep8/)。

By keeping the following advice in mind while coding, your code will be more reusable, adaptable, and clear.
