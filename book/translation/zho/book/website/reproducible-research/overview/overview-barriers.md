(rr-overview-barriers)=
# Barriers to reproducibility

So far we have explained {ref}`what we mean<rr-overview-definitions>` by reproducible research and explained some of the {ref}`additional benefits<rr-overview-benefits>`.

In this section we cover some of the (real and perceived) barriers you may face in making your work reproducible.

```{figure} ../../figures/barriers-reproducibility.png
---
width: 500px
name: reproducibility-barriers
alt: Slide from the presentation showing the different barriers to reproducibility. The text in the center says 'Barriers to reproducible research' and the following barriers are arranged clockwise around the slide - Is not considered for promotion, Held to a higher standard than others, Publication bias towards novel findings, Plead the 5th, Takes time, Support additional users, Requires additional skills.
---
A slide outlining some of the barriers to reproducible research from Kirstie Whitaker's [talk about _The Turing Way_](https://youtu.be/wZeoZaIV0VE?t=312) at [csv,conf,v4](https://csvconf.com/2019) in May 2019.
Used under a CC-BY 4.0 license.
DOI: [10.5281/zenodo.2669547](https://doi.org/10.5281/zenodo.2669547).
```

This chapter outlines some of those barriers, and a few suggestions to get around them. The barriers to reproducible research can be described in three main groups. The first, and hardest to overcome are those relating to the current incentive structure in academic research: {ref}`Limited incentives to give evidence against yourself<rr-overview-barriers-incentives>` (or "Plead the fifth"), the known {ref}`publication bias towards novel findings<rr-overview-barriers-publication>`, the fact that reproducible or open research may be {ref}`held to higher standards than others<rr-overview-barriers-standards>`, and that all this effort is {ref}`not considered for promotion<rr-overview-barriers-promotion>`. Then there are the technical and theoretical challenges of working with {ref}`big data and complex computational infrastructure<rr-overview-barriers-infrastructure>` and remembering that {ref}`being reproducible does not mean the answer is right<rr-overview-barriers-notright>`. 第一个， 最难克服的是那些与学术研究中目前的奖励结构有关的奖励办法: {ref}`提供不利于自己的证据的有限奖励办法<rr-overview-barriers-incentives>` (或“牵头第五个”), 已知的 {ref}`发布偏向于新的结果<rr-overview-barriers-publication>`, 可复制或开放的研究可能是 {ref}`被认为比其他人更高的标准<rr-overview-barriers-standards>`并且所有这一切都是 {ref}`没有被考虑升级<rr-overview-barriers-promotion>` 然后还有一些技术和理论上的挑战，即如何使用 {ref}`大数据和复杂的计算基础结构<rr-overview-barriers-infrastructure>` 并牢记 {ref}`可重现并不意味着答案是正确的<rr-overview-barriers-notright>` 考虑到个别数据科学家面临的压力，我们以三个障碍完成：这项工作可以被认为为 {ref}`需要额外时间<rr-overview-barriers-time>`您可能被要求 {ref}`支持更多用户<rr-overview-barriers-support>` (破坏者：你是！ The good news is that helping you learn those skills is exactly what _The Turing Way_ is here for!

(rr-overview-barriers-incentives)=
## Limited incentives to give evidence against yourself

The [Fifth Amendment](https://en.wikipedia.org/wiki/Fifth_Amendment_to_the_United_States_Constitution) to the United States Constitution includes a clause that no one "shall be compelled in any criminal case to be a witness against [them]sel[ves]". (Edited to gender-neutral language.) （使用不分性别的语言） “为五个国家辩护”意味着有人选择不提供证据证明他们过去的行为可能有些错误。 They have the right to remain silent.

We know that no one wants to incriminate themselves, and also that no one is infallible. Putting your code and data online can be very revealing and intimidating, and it is part of the human condition to be nervous of being judged by others. Although there is no _law_ governing the communication of reproducible research - unless you commit explicit fraud in your work - sharing errors that you find in your work is heavily disincentivised.

```{figure} ../../figures/make-ok-to-be-human.jpg
---
高度: 500px
name: make-oke-to-be-human
alt: A cartoon of a women's holding a flow of files and searche. 思考气泡说。 如果我分享我的数据，人们可能会发现错误。 The caption on the images reads Need to make it ok to be human.
---
An illustration of the "plead the fifth" barrier where our current culture disincentivises acknowledging and correcting mistakes.
Illustration by The Ludic Group LLP from Kirstie Whitaker's keynote presentation at Scientific Data in 2017.
Used under a CC-BY 4.0 license.
DOI: [10.6084/m9.figshare.5577340.v1](https://doi.org/10.6084/m9.figshare.5577340.v1).
```

Giving evidence against yourself, particularly if you find mistakes in published material, is difficult and stressful. But we need to balance that individual cost against the fact that releasing code can help other researchers provide feedback, learn and may help them in their research. In fact, you will almost certainly find that publishing your code and data documentation motivates you to conduct your analyses to a higher standard. Being careful about what you write down, and documenting your decisions, can also help generate new ideas for yourself and for others.

Most importantly, we need to move away from a culture where publishing nothing is safer than publishing _something_. _The Turing Way_ is here to help you take little steps towards being more reproducible as your career progresses. We don't want anyone to feel alone, or "not good enough" as they start and continue their open research journey.

(rr-overview-barriers-publication)=
## Publication bias towards novel findings

Novel results are not necessarily accurate or interesting but they are rewarded in the academic world! Papers that do not find statistically significant relationships are hard to publish, particularly if the results *do not* reproduce previously published findings. (That includes statistically significant findings that go in the opposite direction to already published work.) （这包括与已经公布的工作相反的具有统计意义的调查结果。） 与此相类似， 如果某一文章成功地转载已经发表的结果而不是产生新的集合，它可能不太可能被某一期刊或某一会议所接受。 There's a good chance that reviewers will say "we already know this" and reject the submission.

The bias towards novelty in data science means many researchers are disincentivised from doing the work to document, test and share their code and data. John Ioannidis published an influential paper in 2005 titled "Why Most Published Research Findings Are False" {cite:ps}`Ioannidis2005False` which discusses the many factors that contribute to publication bias. Given these biases, it is very likely that there is a lot of duplicated work in data science. Too many different researchers are asking the same question, not getting the answer they expect or want, and then not telling anyone what they have found.

This barrier is not specific to computational reproducibility as we define it in _The Turing Way_. However, it is a major cultural barrier to {ref}`transparent communication<cm>`, and affects {ref}`project design<pd>`. _The Turing Way_ community are advocating in all the places we are able, for the systemic culture change that is required to dismantle the current publication and academic credit biases towards novelty over rigour.

(rr-overview-barriers-standards)=
## Held to higher standards than others

A researcher who makes their work reproducible by sharing their code and data may be held to a higher standard than other researchers. If authors share nothing at all, then all readers of a manuscript or conference paper can do is trust (or not trust) the results.

If code and data are available, peer reviewers may go looking for differences in the implementation. They may come back with new ideas on ways to analyse the data because they have been able to experiment with the work. There is a risk that they then require additional changes from the authors of the submitted manuscript before it is accepted for peer review.

As we described in the {ref}`"Plead the Fifth"<rr-overview-barriers-incentives>` section above, the solution to this challenge is to align career incentives so that doing what is best for _science_ also benefits the individuals involved.

(rr-overview-barriers-promotion)=
## Not considered for promotion

In the current academic system, a primary consideration for promotion is the proven ability to be awarded grants and recruit students. Both funding bodies and prospective students value novelty and this behaviour is reflected in preferentially rewarding papers with a high [journal impact factor](https://en.wikipedia.org/wiki/Impact_factor). 可能是人类状况的一部分，是出于新的或令人吃惊的动因， 但正如上文&lt;rr-overview-barriers-publication&gt;</code>上面讨论过的 {ref}`那样，这种向新颖的偏向造成了系统的发布偏见。

More broadly, the promotion system in academia tends to reward individuals who have shown themselves to be different from others in their field. That means sharing code and data to make it easy for "competitors" to do the same work ends up being discouraged by promotion and funding selection panels. A good example of this bias is the Nobel Prize award which only goes to a small number of researchers each year, and as such ["overlooks many of its important contributors"](https://www.theatlantic.com/science/archive/2017/10/the-absurdity-of-the-nobel-prizes-in-science/541863/) (Ed Yong, The Atlantic, 2017). One of the goals of _The Turing Way_ is to draw attention to the misalignment of the tenure and promotion process with collaborative and reproducible data science.

(rr-overview-barriers-infrastructure)=
## Big data and complex computational infrastructure

Big data is conceptualised in different ways by different researchers. "Big" data may be complex, come from a variety of data sources, is large in storage volume and/or be streamed at very high temporal resolution. Although there are ways to set random seeds and take snapshots of a dataset at a particular moment in time, it can be difficult to have identical data across different runs of an analysis pipeline. This is particularly relevant in the context of tools for parallel computing. For example, some data such as flight tracking or internet traffic is so big that it can not be stored and must be processed as it is streamed in real time.

A more common challenge for "big data" researchers is the variability of software performance across operating systems and how quickly the tools change over time. An almost constantly changing ecosystem of data science technologies is available, which means reproducing results in the future is highly variable and dependent on using perfectly backwards compatible tools as they develop. Very often the results of statistical tests will vary depending on the configuration of the infrastructure that was used in each of the experiments, making it very hard to independently reproduce a result. Experiments are often dependent on random initialisation for iterative algorithms and not all software includes the ability to fix a pseudorandom number without limiting parallelisation capabilities (for example in Tensorflow). These tools can require in depth technical skills which are not widely available to data scientists. The [Apache Hadoop](https://hadoop.apache.org/) framework, for instance, is extremely complex to deploy data science experiments without strong software and hardware engineering knowledge.

Even "standard" high performance computing, can be difficult to set up to be perfectly reproducible, particularly across different cloud computing providers or institutional configurations.
<em x-id="4">诱惑路径</em> 含有帮助数据科学家在 {ref}学习技能的章节<code>可复制的计算环境<rr-renv>`包括 {ref}`容器 ` 我们总是 [可以提供更多的贡献](https://github.com/alan-turing-institute/the-turing-way/blob/main/CONTRIBUTING.md) ，因为支持大型数据集或复杂建模研究的技术正在演变。

(rr-overview-barriers-notright)=
## Being reproducible does not mean the answer is right

By making the code and data used to produce a result openly available to others, our results may be **reproduced** but mistakes made by the initial author can be carried through. Getting the same wrong answer each time is a step in the right direction, but still very much a **wrong** answer!

This barrier isn't really a _barrier_ to reproducible research as much as a caveat that investing time in reproducibility doesn't necessarily mean that you're doing better science. 您可以认为计算重生产是必要的，但不足以进行高质量的研究。 You can consider computational reproducibility as being necessary but not sufficient for high quality research. A critical approach is needed, rather than naively using existing software or implementing statistical methods without understanding what they do. See, for example, [a discussion](https://ryxcommar.com/2019/08/30/scikit-learns-defaults-are-wrong) in August 2019 about whether the default settings for Scikit-learn's implementation of logistic regression are misleading to new users. Interpretability and interoperability are required to properly evaluate the original research and to strengthen findings.

(rr-overview-barriers-time)=
## Takes time

Making an analysis reproducible takes time and effort, particularly at the start of the project. 这可能包括商定一个 {ref}`测试框架<rr-testing>`, 设置 {ref}`版本控制<rr-vcs>` 例如一个 Github 仓库和 {ref}`连续集成<rr-ci>`和 {ref}`管理数据<rr-rdm>` 在整个项目期间，可能需要时间来维持可再生产的管道。 Throughout the project, time may be required to maintain the reproducible pipeline.

Time may also be spent communicating with collaborators to agree on which parts of the project may be open source and when and how these outputs are shared. Researchers may find that they need to "upskill" their colleagues to allow the team to benefit from reproducibility tools such as git and GitHub, containers, Jupyter notebooks, or databases.

```{figure} ../../figures/help-you-of-the-future.jpg
---
宽度：500px
name: help-yous of future
alt: A cartoon of a women's translation of documents return to hower how. 语音泡沫说您将来主要保存您的记录。 ---
虽然清晰的文件可能会觉得目前需要很多时间。
你正在帮助你和你的合作者记住你已经做了什么，这样做很容易重新使用你的工作或在未来进行修改。
Illustration by The Ludic Group LLP from Kirstie Whitaker's keynote presentation at Scientific Data in 2017.
Used under a CC-BY 4.0 license.
DOI: [10.6084/m9.figshare.5577340.v1](https://doi.org/10.6084/m9.figshare.5577340.v1).
```

However, _The Turing Way_ community advocates that this time is more than made up for by the end of the project. Take as a thought experiment a reviewer asking for "just one more analysis" when the publication has been submitted to a journal. In many cases, this request will come 6 to 12 months after the research team have worked with the raw data. It can be very hard to go back in time to find the one part of the pipeline that the reviewer has asked you to change. If the work is fully reproducible, including version-controlled data and figure generating code, this analysis will be very fast to run and incorporate into the final research output. The analysis pipeline can be easily adapted as needed in response to co-author and reviewer requests. It can also be easily reused for future research projects.

(rr-overview-barriers-support)=
## Support additional users

Many people worry that by making their analysis reproducible they will be required to answer lots of questions from future users of their code. These questions may cover software incompatibility across operating systems and the dependencies changing over time (see the {ref}`Big data and complex computational infrastructure<rr-overview-barriers-infrastructure>` barrier above). They may also include questions about how to adjust the code for a different purpose.

This barrier is based in part on conflating "reproducible" with "open" research. The _Turing Way_ {ref}`definition of "reproducible"<rr-overview-definitions>` doesn't require authors to support the expansion and re-use of the data and code beyond running the exact analyses that generate the published results in the accompanying manuscript.

In almost all cases, making code and data open source requires better documentation than a researcher would write for themselves. This can feel like an additional barrier, although - as discussed in the previous section on reproducible research {ref}`taking extra time<rr-overview-barriers-time>` it is likely that the primary beneficiaries of well commented and tested code with detailed documentation are the research team - particularly the principal investigator of the project - themselves.

(rr-overview-barriers-skills)=
## Requires additional skills

As you can tell from the ever-growing number of chapters in _The Turing Way_, working reproducibly requires skills that aren't always taught in training programmes. You - or someone in your team - might need to develop expertise in data engineering, research software engineering, technical writing for documentation or project management on GitHub. 当当前的奖励结构与学习这些技能不一致时，这是一个主要障碍(见 {ref}的障碍`恳求第五<rr-overview-barriers-incentives>` {ref}`发布偏向于新的结果<rr-overview-barriers-publication>`, {ref}`被认为高于其他人的标准<rr-overview-barriers-standards>`和 {ref}`未被考虑促销<rr-overview-barriers-promotion>`!) 然而，这是我们在 _的主要障碍。 However, this is the primary barrier that we at _The Turing Way_ are working to dismantle with you. We hope you enjoy learning these skills with us and that you'll help us to improve the book as you do.</p>

> "A journey of a thousand miles begins with a single step" (Chinese philosopher [Lao Tzu](https://en.wikipedia.org/wiki/A_journey_of_a_thousand_miles_begins_with_a_single_step)).

We hope that by working towards helping you learn some of these valuable skills we also dismantle some of the more structural barriers to reproducible research.

## Further reading and additional resources

您可以观看Kirstie Whitaker在 [她关于 _Ting ways_](https://youtu.be/wZeoZaIV0VE?t=312) at csv中描述其中一些障碍。 You can use and re-use her slides under a CC-BY licence via Zenodo (doi: [10.5281/zenodo.2669547](https://doi.org/10.5281/zenodo.2669547)). The section describing the slide below starts around 5 minutes into the video.</p>
