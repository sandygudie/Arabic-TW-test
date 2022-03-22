(binder)=
# 宾代尔

在本章中，我们将讨论Binder和mybinder.org项目，以此作为透明和互动分享研究成果的手段。

(binder-shar)=
## 您为什么要分享您的工作？

分享研究成果的动机在 {ref}`rr-open` 章节中更深入地探讨。

简而言之，分享您的研究代码可以通过展示您所走过的过程来帮助为您的结果提供背景。 通过共享代码， 我们还避免为了在一个研究议题上取得进展而复活轮子，因为以前的工具已经能够用在前面。

然而，共享代码的最大障碍往往是安装包和建立计算环境，我们将在下一节看到。 通过 mybinder.org 等平台分享您的工作：

- 安装软件包不再是一个挑战
- 使用不同操作系统的人具有类似的经验，因为计算是在平台上进行的，而不是他们的本地机器。
- 您的工作可以分发给更多的受众，因为技术障碍已经减少

(binder-what)=
## 什么是工程绑定？

我们已经讨论了为什么分享您的工作是重要的，我们已经到了我们决定在协作平台上发布一些带有分析代码的Jupyter 笔记本的程度。 例如GitHub

GitHub 是一个分享代码 _的强大平台。_。 如果仓库是公开的，任何人都可以导航到你的笔记本并阅读内容。 然而， _运行_ 代码要比像GitHub 那样显示更复杂得多。 运行代码需要很多相互依赖的部分，如：

- a. 守则本身的副本；
- 执行它的适当软件；
- 代码所依赖的任何额外软件包不是核心软件的一部分；
- 分析所需的任何输入数据；
- 你还需要一些硬件(一台电脑！) 来运行它。

除获得所有这些部分外，还要获得所有这些部分， 您还必须正确地安装这些软件，使它们不会受到影响或与您的机器上可能运行的其他软件发生冲突。 这是很多工作！

How much easier would it be if we could **run code in the browser**, similar to how it's displayed? 这是Binder项目的目的。

项目Binder为用户提供以下基础设施：

- 一些硬件要执行代码，通常是一个在云端托管的服务器，但也可以是前提硬件；
- a 计算环境包括：
  - approrate 软件，
  - 任何额外的软件包依赖关系，
  - 任何必需的输入数据
  - 和代码本身的副本(笔记本或脚本)；
- 一个URL到环境运行的地方，所以代码可以由您或您的合作者进行交互。

项目Binder将所有移动部件包装在一起，使得很难将计算工作共享到一个简单的界面中。 此界面有 **免费和公开的** 版本，运行在 [**mybinder.org**](https://mybinder.org)。

下面的漫画由 Juliette Taka 制作，演示了一个工作流程，使用Binder 的科学家可能采用这个工作流程。

```{figure} ../figures/binder-comic.png
---
名称：binder_comic
备选案文：一个人可以采取步骤创建一个具有绑定性的项目。
---
图积分：[Juliette Taka、Logilab 和 OpenDreamKit 项目](https://opendreamkit.org/2017/11/02/use-case-publishing-reducible-notebooks/)
```

您可以在他们的 [关于 mybinder.org 页面上找到更多关于 Project Binder 和 mybinder.org 的信息](https://mybinder.readthedocs.io/en/latest/about/about.html)。

(binder-disam)=
### 模糊化

在本节中，有一些相关的术语，为了明确起见，将在此概述：

- **Project Binder**: 一个开放的社区，能够创建清晰的、交互式的、可反应的环境。 此项目的技术输出是 {ref}`rr-binder枢纽`
- **BinderHub**: 一个基于云的基础结构，用于生成绑定。 最广泛使用的是 [mybinder.org](https://mybinder.org), 它是由 Project Binder 团队维护的。 它基于一系列开源工具，包括 [JupyterHub](https://z2jh.jupyter.org)， 通过浏览器向用户提供云计算资源； and [`repo2docker`](https://repo2docker.readthedocs.io/), for building docker images from projects. 由于这是一个开放的项目，可以创建其他BinderHubs来支持更专业化的配置。 其中一个配置可以包括身份验证，以使私人仓库能够在密切的合作者之间分享。
- **一个 Binder**: 一个可以透过浏览器在云端运行的可复现的计算环境中查看和交互的项目的可分享版本。 By automating the installation of the computing environment (as discussed in the {ref}`rr-renv` chapter), Project Binder transforms the overhead of sharing such an environment into the act of sharing a URL.
- **[mybinder.org](https://mybinder.org)**: 一个公开和免费的 BinderHub 因为它是公开的，如果您的项目需要任何个人或敏感信息(例如密码)，您不应该使用它。
- **绑定**: 从一个项目创建一个绑定器的过程。

(binder-appropriate)=
## 什么时候使用mybinder.org是适当的？

在云端维持免费的匿名服务是大量的自愿工作，需要大量资金。 为了在一定程度上降低运行成本，mybinder.org对每个运行中的Binder实例设置计算限制。 这些限制是：

- 1 CPU, 和
- 1 GB of RAM

Hence, mybinder.org is **not** an appropriate place to perform end-to-end replications of Machine Learning workflows, for example!

这也是将本章放在“通信指南”中的主要原因。 由于这些计算限制，mybinder.org很适合主办交互式演示和学习资源用于软件包或研究分析。 在这种情况下，人们点击Binder链接可能想要学习一些东西， 而且通过耗费时间的模式培训过程可能无助于他们实现这一目标。 Instead, you could provide pre-trained models or instructions on how to train the models on their own hardware and _come back_ to the Binder for the remainder of the interactive tutorial.

那么，什么时候使用mybinder.org是适当的？

- 当您想要 _以交互方式交流_ 个东西，如简短分析、教程甚至博客！ 查看 [Achintya Rao 由mybinder.org 提供动力的博客](https://blog.achintyarao.in/about/)！
- 当代码和相关数据(如果相关的话)公开可用
- 当你想要交互运行的代码不需要很多资源或专家资源 (例如GPU)

(binder-faqs)=
## 常见问题

在 [关于 mybinder.org 页面](https://mybinder.readthedocs.io/en/latest/about/about.html) 上回答了许多常见问题。

### 如何将我的更改保存到我的仓库？

不幸的是，你不能做到。 至少在运行中的 Binder 实例的命令行中不能。

写回托管仓库，无论是在 GitHub 上还是其他平台， 将需要某种凭据授权您写入该仓库。 正如已经提到的那样，我是有约束力的。 rg 是一种完全的公共服务，不应在任何情况下向运行中的Binder实例提供任何敏感信息。

然而，这一条是有约束力的。 rg 运行一个名为 [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) 的附加组件提供了一个下载按钮以保存本地笔记本。 _即使您的浏览器已经失去了与提供计算机的云端基础设施的连接！_ 这意味着您可以在本地保存您的进度 用你保存的笔记本更新你的仓库，并用更新的笔记本重新启动你的笔记本。

```{figure} ../figures/binder_notebook_banner.jpg
---
名称：binder_notebook_banner
alt: Jupyter Notebook 控制面板的屏幕截图，一个用紫色矩形突出显示的下载按钮。
---
在运行于mybinder的Jupyter 笔记本中使用此"下载"按钮。 rg 将允许您在本地保存您的笔记本，即使在绑定实例与计算资源断开之后。
```

### 如何在 mybinder.org 上与我的对等点合作？

这不是不可能的，但与其他可用的“免费云计算”服务相比，肯定有发展这个功能的余地。

对此感兴趣者， 可以在 [此Discourse post](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) 和 [`jupyterlab-link-sharing` 版本库](https://github.com/jtpio/jupyterlab-link-share) 中找到更多信息。

### mybinder.org与Google Colab有何不同？

Google Colab提供了一个“厨房汇”计算环境，预安装了许多最受欢迎的数据科学软件包。 与此相对照，mybinder.org为每个已启动的仓库构建定制图像，特别是安装您的配置文件中列出的软件包。

### 我能连接到 `INSERT 数据` 吗？

就安全和防止滥用而言，在mybinder.org上的网络连接非常有限。 因此，只要符合以下两项标准，您就应该能够连接到外部数据提供者：

- 可以通过 HTTP/HTTPS 连接访问
- 您无需凭据才能访问数据

Remember, mybinder.org 完全是一种公共服务，在任何情况下都不应向Binder公司提供诸如全权证书等机密信息。

(binder-segue)=
## 如何创建一个准备绑定的项目

下一章包含 [零到零教程](z2b) ，该教程将引导您在 GitHub 上创建您的第一个准备绑定的项目。
