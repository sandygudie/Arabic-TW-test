(cl-github-novice-firststeps)=
# First steps on GitHub

Here, we provide step-by-step instructions to get started with GitHub.

## 1. 1. Create a GitHub account

Go to [https://github.com/](https://github.com/) and create a new account using the sign up to GitHub box.

## 2. 2. 创建仓库

When you have created a new account and you are logged in, you need to create a new repository.

A repository or repo is the online space where you store all of the documents, data and other files for your project.

* To create the new repository, you need to click on the + sign in the top right corner (in the black band at the top of your window) and then click New repository. This will take you to a page that looks like a form.
* You will see the name of your account and you need to fill in a repository name next to it.
* Also, leave the box ticked for “public” (so your repository is open to all) and then tick the box to create a “README file”.
* Then click the green create repository button at the bottom.

This is what you should see now. It is the landing page for your repository. The diagram below explains what all the buttons, tabs and other things do!

```{figure} ../../figures/github-basic-diagram.jpg
---
name: github-basic-diagram
alt: Annotated diagram of repository after its creation, explaining the main features. The main features are explained in the figure legend.
align: left
---
Annotated diagram of repository after its basic creation, explaining the main features. On the left side of the webpage we have the following features:
- **1. Username:** GitHub user’s name (account). In this example, the username is “EKaroune”.
- **2. - **2. 仓库：** 项目目录（也称为仓库）。 In this example, the repository name is “trial-repo”.
- **3. - **3. 代码:** 此选项卡将您带回您的登陆页面。 It shows you the folders that you have made in the repo.
- **4. - **4. 主要:** 这是你的默认开发分支或你仓库的活动分支。
- **5. - **5. 分支:** 你的资源库的并行版本。
- **6. - **6. README.md 文件：** 此文件包含有关您项目的基本信息(在这种情况下，它只包含项目名称：“trial-repo”。 When we plan to make a website, this will be rendered as a landing (front) page for your site.

On the right side of the webpage we have the following features:
- **7. Green Code button:** click it to download your repository locally.
- **8. - **8. '+'符号：** 你可以在哪里创建新的仓库，导入仓库并创建新问题。
- **9. - **9. Fork:** 创建另一个用户仓库的个人副本。 The number shows how many forks there are of your current repository.
- **10: Add file:** create or upload a file to your repository.
- **11: Commits/clock symbol:** click to see the history of this file as a list of all the edits (commits) saved at different time points.
- **12: Edit/Pencil symbol:** click this pencil symbol to edit your README.md file.
```

## 3. 3. 编辑您的README.md文件

除非您在重建过程中添加了任何其他文件或包含了许可文件， 您现在应该在您的资源库中有一个文件 - README.md. 我们需要编辑此文件来添加仓库信息。 此文件是Markdown文件。 您可以看到这个文件，因为它在文件名称后有“.md”。 This is where you start to use the Markdown formatting. Whatever you write in this file will be shown on the landing (front) page of your project on GitHub, so use it to tell people all about your project.

### Navigating the GitHub editing interface
To edit your README.md file:

* You can click on the pencil symbol in the top right of the central box on your landing page.

**Or**

* Click on the README.md file and then click the pencil symbol.

You can now edit the file. We'll talk about how to save your changes after some pointers on writing a good README.

```{figure} ../../figures/github-readme-before-edit.jpg
---
name: github-readme-before-edit
alt: Annotated diagram of README.md file, if you click on the file name on your landing page. The main features are explained in the figure legend.
align: left
---
Annotated diagram of README.md file, if you click on the file name on your landing page.
- **1. - **1. 仓库和当前文件：** 仓库名称和您正在查看的文件的名称。
- **2. - **2. 主分支:** 当前活动的分支(默认值为“主要”)。 Use to change to different branches of your repo (if there are more branches previously created).
- **3. - **3. 贡献者:** 为您的文件贡献者数目(用户)。
- **4. - **4. README.md 文件内容：** 您README.md 文件的内容出现在这里。 This content will expand once we add more information..
- **5. Raw file:** view the raw markdown text file.
- **6. - **6. Blame:** 查看文件每行的最后一次修改。 It can be used to track when and who made changes and go back to older versions of the file to fix bugs.
**
  - **8。 - **7. 编辑文件：** 点击此铅笔来编辑您的README.md文件。
- **8. - **8. 删除文件：** 点击bin 删除此文件。
```

```{figure} ../../figures/github-readme-after-edit.jpg
---
name: github-readme-after-edit
alt: Annotated diagram of README.md file in edit mode – before editing. Explained in the title.
align: left
---
Annotated diagram of README.md file in edit mode – before editing.
- **1. - **1. 预览更改：** 点击查看您的文本渲染(如何出现在 GitHub 或网页上)。
- **2. - **2. 编辑文件：** 按此选项卡编辑您README.md文件的内容。
- **3. - **3. 将内容添加到README.md:** 为您的 README.md 文件写入Markdown文本。 You currently only have the repository title in this file.
```

### Tips for writing your README file

* Keep it simple! When you’re working in any field, whether it’s software engineering or astrophysics, you’ll learn and use jargon – terms that have a special meaning to your field but likely won’t make sense to anyone who isn’t part of that field. Too much jargon can confuse newcomers, so use simple language and define all potentially unfamiliar terms here.
* Share your project with others - describe what you are doing now and what you want to do in the future.
* Tell people who you are and how you can be contacted.


**NOTE: If you’re having trouble getting started, it’s a good idea to look at other peoples' README.md files.**

If you can’t get your raw markdown content to render in the way you want, it is also a good idea to find a file that has what you want and then look at the raw file. You can copy and paste other people’s raw file content into your README.md file and then edit it.

Here is an example of a really well formatted README.md file: [STEMM Role Models App](https://github.com/KirstieJane/STEMMRoleModels/blob/gh-pages/README.md)

If you click the link above, it will take you to their README.file. You can use this as a template for your README.md file.

* To look at the raw markdown file you need to click on the raw button (top right of the white box).
* This takes you to the markdown raw file that is rendered into a nicely formatted README.md file on GitHub.
* Now just copy and paste it into your README.md edit tab. You can now edit this for your project.
* Remember to check what it looks like by clicking on the preview changes tab.
* When you have finished editing, you need to scroll down to the bottom of the page and press the green commit changes button.

```{figure} ../../figures/github-edited-readme.jpg
---
name: /github-edited-readme
alt: Annotated diagram of README.md file in edit mode – with a template added. Features are explained in the figure legend.
align: left
---
Annotated diagram of README.md file in edit mode – with a template added.
- **1. - **1. 使用 MarkDown 添加内容到 README.md：** 您README.md文件的Markdown (由文件扩展名中的 '.md' 阅读) 文本。 This example shows the template file that has different sections (headers and subheaders are created by using one or more of ‘#’ symbol. See the {ref}`formatting consistency section of the Community Handbook<ch-consistency-formatting-hr-markdown>` for some more information on using Markdown.
```
### Committing - or saving - your changes
Committing your changes is like hitting the "save button" for a file. GitHub will not automatically save your changes, so it's important not to skip this step.

Whatever changes you have made in the file will be deposited into your repository.

It is good practice to write a descriptive commit title and a short description of what you have done in the commit changes box. So something like - commit title: ‘first edit of the readme file'; description: 'copied template from … and edited it with the details of this project’. This information about the commit is called a “commit message”, and the commit title will enable you to quickly look through the history of changes for a file (which is why making them descriptive is so important - it's like leaving a helpful note to your future self).

You can see a list of your commits (or your "commit history") by clicking the clock symbol on your landing page or within the page for each file.

## 4. 4. 将许可证添加到您的存储库

It is important that all of your work has a license from the very beginning or no one can reuse it. Licenses tell other researchers how they are able to reuse, modify and remix your work. No license implies that others are *not* allowed to use your work, even with attribution. 所以最好包括一个许可，让人们知道他们可以做什么和不能做什么，以及如何为你的工作给你功劳。 So it is better to include a license that lets people know what they can and can't do and how to give you credit for your work.

Depending on your field, much of your work may be documents with only some data or code. The standard licenses offered on GitHub are most approriate for software and won’t really be the right kind for documents.

[Creative commons](https://creativecommons.org/licenses/) licenses are the best to use for this purpose, and the most open of these is the CC BY 4.0.

To add a license to your repository, the first thing to do is create a LICENSE.md file:

* To do this, click on the Add file button, and click create file. This will give you a blank file.
* 然后，你需要给文件命名，所以请拨它LICENSE.md. 这使它变成一个Markdown文件。 This makes it into a markdown file.
* You can find all the creative commons licenses in the link above so copy the text of the license you want and then paste it into this file.
* Don’t forget to press the green commit new file button at the bottom and write a commit message to describe what you have done.
* You can also add a link to the license to the bottom of your README.md file. Here is a link to a repository that you can copy to add in a [CC BY 4.0 license](https://github.com/santisoler/cc-licenses). It has a text file for your LICENSE.md file and also a shield (or badge) that you can put at the bottom of your README.md file.

You can find more information about licenses in the {ref}`rr-licensing` chapter of The Turing Way.
