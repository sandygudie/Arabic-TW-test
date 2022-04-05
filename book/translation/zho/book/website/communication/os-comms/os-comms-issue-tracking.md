(cm-os-comms-issue-tracking)=
# Issue Tracking

Most software development projects have some kind of issue board to easily track current issues in the project, such as bug fixing, rolling out new features, or community engagement plans. [GitHub](https://github.com) (一个非常受欢迎的协作平台) 有一个内置的 [问题跟踪器](https://guides.github.com/features/issues/) 和 [项目板](https://help.github.com/en/github/managing-your-work-on-github/about-project-boards) 可以将问题一起进行比较以追踪更具体的进度。

This section is a discussion around why issue tracking is useful and where you can store them.

(os-comms-issue-tracking-purpose)=
## What is the purpose of your issues?

There are many different reasons for keeping/tracking issues related to a project. The platform for issue tracking and the features tracked by those issues can influence how your community interact with your project.

Mostly, issues are used to track bug reports, feature requests, opportunities for community members to engage, and so on, then a public issue board will allow your community to get a clear overview of what's coming down the pipeline and how they can get involved.

Let's look into centralised and decentralised/distributed issue boards and how they might engage your community.

(os-comms-issue-tracking-purpose-issues)=
### Issues per Repository (Decentralised/Distributed)

If your project is split across multiple repositories, then it's a good idea to keep the issues specifically related to that module within that repository: a decentralised system. This allows your community to focus their attention on what is important to them.

This approach has several smaller issue boards for each repository (or module) within your codebase. This method has a lot of positive outcomes, such as:

- The volume of issues is more manageable;
- Most contributors only need to be aware of issues relating to one or two repositories;
- Contributors can subscribe to notifications or updates from only the repositories that interest them;
- It feels like "divide and conquer", more people are working on more aspects to move the project as a whole forward.

(os-comms-issue-tracking-purpose-issues-case-study)=
#### Case study: mybinder.org

[mybinder。 rg](https://mybinder.org) 是一个方便用户通过云端轻松分享可重复分析和计算环境的平台。 This project is spread across a number of different repositories, each one an individual tool that can be used in isolation from the others. These are:

- [repo2docker](https://github.com/jupyter/repo2docker),
- [JupyterHub for Kubernetes](https://github.com/jupyterhub/zero-to-jupyterhub-k8s),
- [BinderHub](https://github.com/jupyterhub/binderhub).

There are also some tools in the Jupyter ecosystem that are only weakly associated with Binder. Tools which Project Binder uses and people associated with Binder contribute to, but so do other unrelated communities. Such tools are [JupyterHub](https://github.com/jupyterhub/jupyterhub) and [KubeSpawner](https://github.com/jupyterhub/kubespawner).

Each of these repositories contains hundreds of issues tracking on-going work being performed by the community and scoping future directions for each project to take.

Can you imagine trying to combine all of these issues into one place? It would become very difficult, if not impossible, for someone to find what they are looking for and would require a very clever tagging schema plus instructions for filtering by tag.

In the Project Binder team's experience, most community members contribute to just one or maybe two of these projects. So having consolidated access to all the issues for all the working parts is not a high priority for their community.

他们发现，分发问题跟踪后，社区中那些只能在朱皮特尔胡布工作的成员能够轻松地作出贡献，而不需要熟悉运行
mybinder的一切。</p> 

(os-comms-issue-tracking-purpose-issues-case-centralised-issue)=


### Centralised Issue Repository

With a big project, it can be tempting to collate all your issues into one place for the sake of easier management: a centralised system. If you are using issues to track a central service, personal to-do lists, and answering questions like if a task is high priority or if it is assigned to someone already, then issue tracking in a centralised system is a good option and it does not necessarily need to be circulated to your wider community.

However in terms of engaging your community, such a centralised system can be problematic. If your issues are elsewhere this can create a lot of barriers to entry for community members, such as:

- Issues are more difficult to discover;
- If they are hosted on another platform (for example, code is on GitHub but issues are on [Asana](https://asana.com/)), that's another tool community members need to learn how to use;
- Issues are separated from the code they are referencing.

A very large impact on the community of having a separate issue board is that when people visit your code repository, it looks like an inactive project because there are no issues or conversations going on where the code is hosted. This may cause community members to believe that the code is no longer being actively developed/maintained/supported and may choose to use another codebase or software package.

(os-comms-issue-tracking-comparative-table)=


## Comparative Table

The table below compares features of distributed and centralised issue repositories for a multi-repository project.

| Feature                                 | Centralised Issue Repo | Distributed Issue Repos |
|:--------------------------------------- |:----------------------:|:-----------------------:|
| Global issue search                     |           ✅            |                         |
| Hosted by the same platform as the code |   ❓(not guaranteed)    |            ✅            |
| Filter by repository                    |    ❓(power users*)     |            ✅            |
| Subscribe to relevant updates           |     ❓(power users)     |            ✅            |
| Easy to Discover                        |                        |            ✅            |
| Connected to the Codebase               |                        |            ✅            |
| Appears active to community             |                        |            ✅            |
| Manageable volume                       |                        |            ✅            |


*Power users = These are people who are already familiar enough with a platform to know the gotchas and tricks that make their experience more efficient



## Further Reading

- 博客文章比较邮件列表和论坛的方便性和社区近似性： [https://psychcentral.com/blog/mailing-lists-versus-forums-community-closeness/](https://psychcentral.com/blog/mailing-lists-versus-forums-community-convenience-closeness/)
- 博客文章由 [Tim Head](https://github.com/betatim):  [https://betatim.github.io/posts/posts-on-collective-thinking/](https://betatim.github.io/posts/thoughts-on-collective-thinking/)
