(rr-open-source)=
# Open Source Software

(rr-open-source-whatis)=
## What Is Open Source Software?

When a project is open-source [{term}`def<Open Source Software>`], anybody can view, use, modify, and distribute the project for any purpose. These permissions are enforced through an open-source licence. Open source is powerful because it lowers the barriers to adoption, allowing ideas to spread quickly. In its most basic form, open-sourcing your software means putting your code online where it can be viewed and reused by others.

Many of the most widely used research software is open source. Perhaps the paradigmatic example is the scikit-learn Python package for machine learning (Pedregosa et al., 2011), which, in the space of just over five years, has attracted over 500 unique contributors, 20,000 individual code contributions, and 2,500 article citations. Producing a comparable package using a traditional closed-source approach would likely not be feasible. It would, at the very least, require a budget of tens of millions of dollars. While scikit-learn is an outlier, hundreds of other open-source packages that support much more domain-specific needs depend similarly on unsolicited community contributions; for example, the NIPY (neuroimaging in Python) group of projects in neuroimaging (Gorgolewski et al., 2016). Notably, such contributions not only result in new functionality from which the broader community can benefit, but also regularly provide their respective authors with greater community recognition, and lead to new project and employment opportunities.

Researchers that make use of open-source software often make changes to them, such as adding features they need for their research, or fixing bugs. They can then contribute these improvements back to the main project so the wider community can take advantage of them.

(rr-open-source-benefitsyou)=
## How Running and Contributing to Open-Source Software Projects Benefits You

- _Improve existing skills_: Whether it is coding, user interface design, graphic design, writing, or organizing, if you are looking for practice, there is a task for you on an open-source software project. Further, open source necessitates cleaner, more maintainable code to enable collaboration between potentially thousands of people who may never meet. This helps to build and maintain good coding habits. Not to be underestimated are the people skills you can develop on open source software projects. Open source offers opportunities to practice leadership and management skills, such as resolving conflicts, organising teams of people, and prioritising work.
- _Advance your career_: By definition, all of your open source work is public, and this presents opportunities:
  - _Demonstrate technical ability_: Technical interviews traditionally involve working on a simulated problem that can be tackled in a set amount of time with little additional context. Such simulations, by definition, are not real-world use cases, nor do they show what working with an applicant would be like. Open source provides visibility into both how a candidate solves problems, and how they work with others. You make a much more appealing employee if an employer can see the quality of your work and see you working with others over a long period rather than taking a chance on a single short, high-stress case which may not play to your strengths.
  - _Reputation_: Becoming an active member of the open source community can gain you a favourable reputation which may bolster future job prospects.
- _Meet people with similar interests_: Open source software projects with warm, welcoming communities keep people coming back for years, and many people form lifelong friendships through their participation in open source.
- _Find mentors and teach others_: Working with others on a shared project means you will have to explain how you do things, as well as ask other people for help. The acts of learning and teaching can be a fulfilling activity for everyone involved.

### Making Your Work Open Source

- _Re-usability_: Making your work openly available for re-use makes it easier for others to incorporate into their research. If you make your software citeable, via a DOI [{term}`def<Digital Object Identifier>`] for example, this can increase your citations.
- _Contribution_: When you write closed source software, the only developers that can potentially detect, diagnose, triage, and resolve software bugs are those that have a copy of the code. If your project is open, the number of potential contributing developers and thus the potential knowledge pool is orders of magnitude larger.
- _Feedback_: Making your work open enables you to get feedback and improve your project in a way you may never have thought of alone.
- _Accountability_: There is an argument that any software developed using government money should be open source by default; if the public has paid for its development they have a right to make use of it. If your work is government-funded, making it open is a step you can take towards government openness and accountability.

### Contributing to Others' Open Source Software Projects

- _It is empowering to be able to make changes, even small ones_: You do not have to become a lifelong contributor to enjoy participating in open source. Have you ever seen a typo on a website, and wished someone would fix it? On an open source software project, you can do just that. Open source helps people feel agency over their lives and how they experience the world, and that in itself is gratifying.
- _它是有趣的_: 开放源码提供了一套没完没了的、不断变化的 Rubix 立方体，供您在周末解决。 Just like puzzles, both crossword and jigsaw, open source provides bite-sized intellectual escapes.

(rr-open-source-benefitsresearch)=
## How Open Source Software Benefits Research

开放源码软件有几种有益于研究的方式：

(rr-open-source-benefitsresearch-reusable)=
### Re-usable

Open source software projects allow researchers to take advantage of each others’ work. This enables researchers to apply their efforts to high-value work. It is sometimes said that “all the easy problems have already been solved”. Blogging, content management, and operating systems are all problems with established (and mainstream) open-source solutions, to name a few. While developers could spend their time reinventing wheels that the open-source community has already perfected, it is highly preferable to use the world’s best wheel, especially when that wheel comes at no cost to you. This reduces duplication of effort and allows researchers to focus on yet-unsolved challenges.

The {ref}`rr-code-reuse` provides a more in-depth list of different aspects to consider for making your code more reusable, whether this is a small script or a library.

(rr-open-source-benefits research-check)=
### Checkable

开放源码项目使更广泛的研究界能够阅读和测试对方的代码。 这样就可以更快地找到漏洞，其他研究人员可以验证结果。

(rr-open-source-benefits research-collaborative)=
### Collaborative
公开工作还使任何数量的研究人员能够就单一研究人员/研究小组无法开发的项目进行合作。 示例包括 [Linux](https://www.linux.org/) 操作系统，Python 软件包，例如 [scipy](https://www.scipy.org/) 和 [numpy](http://www.numpy.org/), 和机器学习库 [TensorFlow](https://www.tensorflow.org/).

(rr-open-source-run)=
## How to Run Your Open Source Software Project

您可以打开源代码，一个正在进行中的工作，或者多年被关闭的源代码。 在最基本的层面，您需要做的只是将您的代码放在网上的某个地方，这可能会持续很长时间。 你可以将你的代码分配为 DOI [{term}`def<Digital Object Identifier>`] (在关于 {ref}的章节中讨论过`rr-rdmsharing`). 这有助于确保如果有人使用您的工作或以您的工作为基础，您可以获得适当的积分。 这有助于确保如果有人使用您的工作或以您的工作为基础，您可以获得适当的积分。

提供您的代码的热门地方是 GitHub [{term}`def<Github>`] (见关于 {ref}`rr-vcs` 的章节)。 您必须包含一个许可文件，说明任何人都有权限使用、复制和修改您的工作。 没有这一点，任何人都不能合法地使用你的工作，因此它不是开源的。 The {ref}`rr-licensing` chapter will help you to pick the best license for your project. 还有几个其他文件你应该包含在你的代码中，如下所述。 还有几个其他文件你应该包含在你的代码中，如下所述。

(rr-open-source-run-readme)=
### Welcome Users by Adding Information to Your README

您应该包含一个README [{term}`def<README>`] 文件，其中包含有关项目的有用信息。 如何使用它，以及如何为它作出贡献。 以下是README应该包含的主要内容列表：

- _The project name and what it is_: This will significantly help someone that comes across it to get an idea of the project. Include a few key points that describe the main features of the project and what features you are implementing. This helps to quickly compare other projects with yours and gives an idea of why the project exists in the first place.
- _Instructions on how to install the project_: The installer might be a collaborator, someone that comes across and is interested in the project, or even you - if you get a new machine and need to re-install your project. Nevertheless, it is a total waste of your resources to figure out how to get started with the project from scratch. The instructions should also include any prerequisites that will be needed to run the project. The best thing you can do is to write up the installation instructions when you first do them yourself, and you will quickly save hours of work in the future.
- _Instructions for how to run the code and any associated tests_: If you've been working on your project it may seem obvious how to run it, but this will likely not be the case for someone coming across it for the first time.
- _Links to related material_
- _List of authors/contributors to the project, possibly with contact information_
- _Acknowledgements_

假定您打算让其他人在您的项目上进行合作(而不是仅仅提供您的代码并考虑完成)。 在这种情况下，你应该包括促成准则和最有可能的行为守则。

(rr-open-source-run-guidelines)=
### Contributing Guidelines

贡献准则 [{term}`def<Contributing Guidelines>`] 告诉您的听众如何参与您的项目。 例如，您可以提供以下信息：

- How to file a bug report
- How to suggest a new feature
- Your roadmap or vision for the project
- How contributors should (or should not) get in touch with you

使用一种温暖、友好的语气，并就捐款提出具体建议(例如撰写文件)； 或建立一个网站可以大大有助于让新来者感到欢迎和兴奋地参与。 例如， [Active Admin](https://activeadmin.info/index.html) 将其 [贡献指南](https://github.com/activeadmin/activeadmin/blob/master/CONTRIBUTING.md) 开始：“先关闭，感谢您考虑为Active Admin作出贡献。 你喜欢的人会让主动管理成为一种很好的工具。”

在您的项目的最早阶段，您的贡献准则文件可以很简单。 您应该始终解释如何报告错误或文件问题，以及任何技术要求(例如测试)来做出贡献。 随着时间的推移，您可以在这里或在您的阅读文件中添加其他常见问题。 写下这个信息意味着更少的人会反复问你相同的问题。 从您的README链接到您的贡献准则文件也是一个好主意，所以更多的人看到它。

(rr-open-source-run-conduct)=
### Code of Conduct

行为代码 [{term}`def<Code of Conduct>`] 有助于为您的项目参与者设置行为基本规则。 如果你正在为社区或公司发起一个开放源码项目，这将特别有价值。 《行为守则》授权您促进健康和建设性的社区行为，这将减少您作为维护者的压力。 它传达了您期望参与者的行为方式，并描述了这些期望适用于哪些人。 如果发生违法行为，应如何处理。

像开放源码许可证一样，也正在出现行为守则，所以您不必自己写字。 [贡献者盟约](https://contributor-covenant.org/) 是一个 drop-into 行为守则，由 [40 000多个开放源码项目](https://www.contributor-covenant.org/adopters) 使用。 无论你使用什么文本，你都应该准备在必要时执行你的《行为守则》。

将文件保存在您项目的根目录中，所以它是容易查找的，并从您的README链接到它。

(rr-open-source-contribute)=
## How to Contribute to Other's Open Source Software Projects

(rr-open-source-contribute-anatomy)=
### Anatomy of an Open Source Software Project

每个开源社区都是不同的。 尽管如此，许多开放源码软件项目遵循类似的组织结构。 了解不同的社区角色和整个过程将有助于您迅速面向任何新项目。

一个典型的开放源码软件项目有以下类型的人员：

- _Author_: The person/s or organization that created the project.
- _Owner_: The person/s who has administrative ownership over the organization or repository (not always the same as the original author).
- _Maintainers_: Contributors who are responsible for driving the vision and managing the organizational aspects of the project. They may also be authors and/or owners of the project.
- _Contributors_: Everyone who has contributed something back to the project.
- _Community Members_: People who use the project. They might be active in conversations or express their opinion on the project's direction.

大型项目还可设立小组委员会或工作组，重点处理不同的任务，例如工具的使用、试用、社区节制和活动的组织。 查看一个项目的“团队”网页或治理文件库中的网站来查找这种信息。

在GitHub 上托管了许多开放源码项目(详情见关于版本控制的一章)，其设施包括：

- _Issue tracker_: Where people discuss issues related to the project.
- _Pull requests_: Where people discuss and review changes that are in progress.
- _Discussion forums or mailing lists_: Some projects may use these channels for conversational topics (for example, "How do I..." or "What do you think about..." instead of bug reports or feature requests). Others use the issue tracker for all conversations.
- _Synchronous chat channel_: Some projects use chat channels (such as Slack or IRC) for casual conversation, collaboration, and quick exchanges.

(rr-open-source-contribute-changes)=
### Contribute Your Changes

说你已经添加了一个功能或修复了一个错误，想要将此工作贡献给主项目。

1. _Read the documentation_: The main project may have contributing guidelines or information in a README instructing prospective contributors on how to supply their changes.
2. _Make sure your conventions match the style and structure of the main project_: For example, if all the variables in a project are named in some particular way yours should be too. Consistent conventions make it much easier for someone who has not seen your piece of the project before to understand it rather than having to figure out your particular set of conventions *and* what the code is doing. The project's conventions may be outlined in its documentation, or may just be evident from inspection of the code itself.
3. _Break your changes up into manageable, well-defined chunks_: For example, if you have added two separate features, do not submit them together. Keeping things "clean" in this way makes your work simpler to understand and review.
4. _Test your changes_: If the project comes with tests, run them. Make sure you are testing against an up to date version of the project as it may have evolved considerably over time. Write specific tests for your changes and submit those too.
5. _Do not just submit code, update relevant documentation too_: If your changes are incorporated, it will have to be updated. If you do not do it, someone else will have to.
6. _Ask questions_: If there are things you are unsure about, there is no harm in asking. Many larger projects have dedicated forums or other venues for questions and discussion.
7. _Be clear_: When you submit your changes, clearly describe the changes you have made, why you have made them, and how they have been implemented. This makes it as easier for someone looking at your work and deciding whether to incorporate it into the main project to do so. In the likely case the main project is hosted on GitHub, you should put this in the pull request (see the chapter {ref}`rr-vcs` for more details).

(rr-open-source-contribute-looking)=
### Looking for Projects to Contribute to and How to Contribute to Them

你不需要忽略你的第一个贡献将是什么，或者它将是如何看待的。 相反，首先考虑你已经使用或想要使用的项目。 你将积极贡献的项目是你发现自己回来的项目。 在这些项目中，每当你发现某种东西可能更好或不同时，你都会根据自己的本能行事。 您可以扫描一个README 并找到一个断开的链接或轮胎。 或者，您可能是一个新的用户，注意到某些东西已经损坏，或者找到一个你认为应该在文档中的问题。 不要忽略它，不要继续动动动，也不要让别人修理它，看看你是否可以通过跳进来帮忙。 这就是开放源码。

您也可以使用下列资源之一来帮助您发现和贡献新项目：

- [Open Source Friday](https://opensourcefriday.com/)
- [First Timers Only](https://www.firsttimersonly.com/)
- [CodeTriage](https://www.codetriage.com/)

如果你不知道如何开始，有几种其他方法可以处理它。 例如找到一个开放的问题来处理或询问您是否可以帮助撰写一个新的功能。

对开放源码贡献的一个常见误解是你需要贡献代码。 事实上，最受忽视或忽视的往往是项目的其他部分。 您将通过主动提供这些类型的贡献来完成这个项目。 您可以：

- Review code on other people's submissions.
- Write and improve the project's documentation.
- Curate a folder of examples showing how the project is used.
- Answer questions about the project on, for example, Stack Overflow,
- Keep things organized, for example, on GitHub by:
    - Linking to duplicate issues.
    - Suggesting new issue labels.
    - Going through open issues and suggesting closing old ones.
    - Ask clarifying questions on recently opened issues to move the discussion forward.

(rr-open-source-closed)=
## Closed Software

如果您正在与那些不使用开放源码模型软件的人合作怎么办？ 这种做法最初似乎是对迄今所讨论的所有原则的冒犯。 然而，通常有很好的理由说明为什么情况是如此（例如法律、商业或安全原因）。 常常仍有可能使用和作出贡献，但如何不同的细节。 “封闭式”软件中使用的做法通常是相同的。 和你可以在诱导方式中了解的概念和工具仍然适用。

然而，有时可能没有很好的理由采取封闭源码办法。 不同的研究领域有不同的文化，这些文化与开放原则的谷物格格不入，并感到非常沮丧。 克服这一障碍可能是非常棘手的，因为文化可能需要数年或数十年才能改变。

使用封闭软件可以为您的研究提供机会和威胁。 在所有情况下，理解和尊重他人的观点提供了最大的成功机会。
