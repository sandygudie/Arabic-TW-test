(cm-citable-cite)=
# Citing Research Objects

You should cite research objects directly in the paper in places where it is relevant. This is a commonly practised way of citing publications and is valid for citing other research components like data and software. A citation includes the following information:
- Author
- Title
- Year of publication
- Publisher (for data, this is often the data repository where it is housed),
- Version (if indicated)
- Access information (a URL or DOI)

A citation style is a specific arrangement, order and formatting of information necessary for a citation. For instance, the MLA style was developed by Modern Language Association (originally used in the humanities) and the APA style was developed by American Psychological Association (originally used in psychology and the social sciences).
- MLA citation style uses the following format: `Author. "Title of the Source." MLA 引文风格使用以下格式： <code>作者 “源名称” 容器的标题，其他贡献者，版本，Number，出版，出版日期，位置。 `
- APA 引文风格使用以下格式： `作者 (年份)。 (Year). Title of data set (Version number). [Retrieved from] ***OR*** [DOI]`

See [Scribbr Citation Styles Guide](https://www.scribbr.com/citing-sources/citation-styles/). See also [FORCE11 resource](https://www.force11.org/node/4771).

(cm-citable-cite-data)=
## Citing Data

When sharing a dataset, use dedicated DOIs and add a **data availability statement** at the end of the paper or in online repository details (similar to the acknowledgement section).

You can find examples of these statements in the publishers' (research data) author policies.

### Data availability statement examples:

**使用 Digital Object Identifier (DOI)：** “支持本研究结果的数据可公开查阅http://doi [repositorial name] 。

**If no DOI is issued:**
- “支持本研究结果的数据可公开查阅 \[URL\]\[仓库名称\]，参考号[参考号]。”

**When there is an embargo period you can reserve your DOI and still include a reference to the dataset in your paper:**
- “支持调查结果的数据将在公布之日起\[6个月]禁运之后，以[URL/DOI\]\[存放地名\]提供，以便使研究结果商业化。”

**When data cannot be made available:**
- “Restrictions apply to the data that support the findings of this study. ] 如果数据含有可能损害研究参与者隐私的信息，则可通过联系[姓名和联系细节]并经[第三方姓名]许可，根据合理请求提供数据。”
-  “The data that support the findings of this study are available upon request. 访问条件和程序可以在 [EASY](https://easy.dans.knaw.nl/ui/home) 等限制访问仓库的 URL。 ]”

**More Data Availability Statement examples:**

You can find more examples on the [Manchester's Data Access Statements page](https://www.library.manchester.ac.uk/using-the-library/staff/research/research-data-management/sharing/data-access-statements/), the [Cambridge Data Availability Statement examples](https://www.cambridge.org/core/services/authors/open-data/data-availability-statements), the [AMS Data Availability Statement examples](https://www.ametsoc.org/index.cfm/ams/publications/author-information/formatting-and-manuscript-components/data-availability-statement-examples/), or [Nature's Tips for writing a dazzling Data Availability Statement](https://researchdata.springernature.com/posts/tips-for-writing-a-dazzling-das-data-availability-statement).

(cm-citable-cite-software)=
## Citing Software

软件引文与上文所述的数据引文有许多相同的要素。 在 [软件引证原则](https://www.force11.org/software-citation-principles) 中详细描述. 在使用其他软件时，必须适当引述并赋予它适当的属性。

To make your code citable, you can use the integration between [Zenodo](https://zenodo.org/) and GitHub.

- Create a file to tell people how to cite your software. Use this [handy guide](https://citation-file-format.github.io/cff-initializer-javascript/) to format the file.
- Link your GitHub account with a Zenodo account. This guide explains [how](https://guides.github.com/activities/citable-code/).
- 您可以通过添加 `zenodo 来告诉Zenodo 你想要包含什么信息或元数据。 son` 文件，在这里介绍
- On Zenodo, flip the switch to the 'on' position for the GitHub repository you want to release.
- On GitHub, click the *Create a new release* button. Zenodo should automatically be notified and should make a snapshot copy of the current state of your repository (just one branch, without any history), and should also assign a persistent identifier (DOI) to that snapshot.
- Use the DOI in any citations of your software and tell any collaborators and users to do the same!
