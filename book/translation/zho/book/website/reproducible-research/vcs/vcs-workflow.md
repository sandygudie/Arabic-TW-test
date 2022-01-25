(rr-vcs-workflow)=
# 一般工作流

版本控制是一种系统的方法，用以记录文件或一组文件在一段时间内所作的更改。 这使您和您的合作者能够跟踪历史，看看变化情况，并在需要时稍后重现特定版本。 使用版本控制的典型程序如下：

1. 创建文件 - 这些文件可能包含文本、代码或两者。
2. 通过更改、删除或添加新内容来处理这些文件。
3. 此时创建文件状态的快照(也称为版本)。

不同版本控制软件对创建快照的过程作了不同的描述。 例如，Git将其描述为“提交”。 有些系统称它为“时间点”或“检查站”； 并且这在其他情况下被称为“保存您的工作”，例如在 [Google 文档](https://docs.google.com/) 或 [HackMD](http://hackmd.io/) 中。

当您通过添加更改来保存您的工作时，您会制作更多的快照。 您可以将这些文件视为保存这些文件的版本，同时记录它们的历史。 如果您因错误需要返回到文件的上一个版本， 或者如果您改变了对上一次更新的主意， 您可以访问您喜欢的版本中的文件，或者将您的整个项目退回到过去的状态。

这方面的说明见下文。

```{figure} ../../figures/main-branch.png
---
名称：主分支
备选: 主分支
-
主分支的图示.
```

在许多版本控制系统中，每次保存新版本，您都可以添加评论。 这些评论应简明扼要，便于理解拟议的修改和更新的版本。 这确保了当您需要回到过去的版本时，很容易找到您正在寻找的东西。 您的合作者将感谢您，但是您自己的未来版本也将感谢您。

(rr-vcs-workflow-branches)=
## 使用 "分支" 的非线性项目开发

所以你有你的项目，你想要添加一些新项目或试试一些东西，然后才能反映主要项目文件夹中的变化。 要添加新内容，您可以继续编辑您的文件并使用拟议的更改保存它们。 假定您想要尝试一些东西而不反映中央仓库中的更改。 在这种情况下，您可以使用 Git 等高级版本控制系统的“分支”功能。 一个分支创建一个本地版本库，您可以在其中工作并尝试新的更改。 您在您的分支上所做的任何工作都不会反映在您的主要项目上(称为您的主要分支)，因此它是安全和没有错误的。 同时，您可以在本地分支中测试您的想法和故障排除点。

当您对新的更改感到满意时，您可以将它们介绍到主项目。 Git的合并功能使得本地分支的独立发展线能够并入主分支。

```{figure} ../../figures/one-branch.png
---
名称：单分支
备选案文：git
中开发和主分支的图示--
Git中开发和主分支的图示.
```

您的主副本可以有多个分支。 如果你的一个分支最终无法工作，你可以放弃它或删除它而不影响你的项目的主要分支。

```{figure} ../../figures/two-branches.png
---
名称：两个分支
备选案文：两个开发分支和一个主分支在 git
中的示例。
两个开发分支和一个主分支在 git 中。
```

如果你想要，你可以从分支中创建分支(以及这些分支的分支等等)。

```{figure} ../../figures/sub-branch.png
---
名称：子分支1
备选案文：git中开发分支的图示.
---
git中的开发分支。
```

无论你拥有多少分支，你都可以访问你过去对其中任何一个版本的版本。 如果你想知道如何在实践中使用这个功能，你会在下面找到更多的细节。