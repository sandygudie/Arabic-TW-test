(rr-overview-barriers)=
# الحواجز التي تحول دون قابلية إعادة الإنتاج

حتى الآن شرحنا {ref}`ما نعنيه<rr-overview-definitions>` بالبحث القابل لإعادة الإنتاج، وشرحنا بعضا من {ref}`الفوائد الإضافية<rr-overview-benefits>`.

في هذا القسم نغطي بعض العوائق (الحقيقية والمتصورة) التي قد تواجهك في جعل عملك قابلاً للتكرار.

```{figure} ../../figures/barriers-reproducibility.png
---
العرض: 500px
الاسم: reproduci-barriers
بديل: شريحة من العرض التقديمي الذي يظهر مختلف الحواجز أمام قابلية إعادة الإنتاج. النص الموجود في مركز الشريحة(السلايد) يعرض "الحواجز أمام البحث القابل لإعادة الإنتاج (Reproducible research)" والحواجز التالية مرتبة حسب اتجاه دوران عقارب الساعة - ليس مرجحا للمكافأة، يقيَّم وفق معايير أعلى من الآخرين، انحياز الناشرين نحو الاكتشافات المبتكرة، التمسك بالتعديل الخامس (Plead the 5th) ، يستهلك الوقت، توفير الدعم للمستخدمين الجدد، يتطلب مهارات إضافية.
---
شريحة تبين بعض الحواجز التي تحول دون قابلية إعادة إنتاج البحث من Kirstie Whitaker [تحدث عن _The Turing Way_](https://youtu.be/wZeoZaIV0VE?t=312) في [csv,conf,v4](https://csvconf.com/2019) في مايو 2019.
Used under a CC-BY 4.0 license.
DOI: [10.5281/zenodo.2669547](https://doi.org/10.5281/zenodo.2669547).
```

يوجز هذا الفصل بعض تلك الحواجز وبضعة اقتراحات لتجاوزها. يمكن تصنيف الحواجز التي تحول دون قابلية إعادة إنتاج البحث إلى ثلاث فئات رئيسية. الفئة الأولى و الأصعب في التجاوز هي تلك الحواجز المتعلقة بالهيكلية الحالية لحوافز البحث الأكاديمي: {ref}`حوافز محدودة لتقبل النقد و كشف الأخطاء<rr-overview-barriers-incentives>` (أو "التمسك بالتعديل الخامس (Plead the fifth)") {ref}`الانحياز المعروف للناشرين نحو الاكتشافات المبتكرة<rr-overview-barriers-publication>`, حقيقة أن البحوث القابلة لإعادة الإنتاج أو البحوث المفتوحة قد تخضع {ref}`لتقييم وفق معايير أعلى من الآخرين<rr-overview-barriers-standards>`، وأن كل الجهد المبذول {ref}`ليس مرجحا للمكافأة<rr-overview-barriers-promotion>`. ثم هناك التحديات التقنية والنظرية في التعامل مع {ref}`البيانات الضخمة(big data) و البنية الحاسوبية الأساسية(Computational infrastructure) المعقدة<rr-overview-barriers-infrastructure>` و {ref}`حقيقة أن قابلية إعادة الإنتاج لا تعني أن النتائج صحيحة.<rr-overview-barriers-notright>`. و ننهي بثلاثة حواجز متعلقة بالضغوطات على علماء البيانات: يمكن النظر إلى هذا العمل على أنه {ref}`يستغرق وقتاً إضافياً<rr-overview-barriers-time>`، قد تكون مطالبا {ref}`بتوفير دعم للمستخدمين الجدد<rr-overview-barriers-support>` (تلميح: أنت لست مطالبا بذلك! ، و أنك أنت و أعضاء فريقك قد تكونون {ref}`بحاجة إلى مهارات إضافية<rr-overview-barriers-skills>`. الخبر السار هو أن _منهج تورينج (The Turing Way)_ خصص لمساعدتك على اكتساب تلك المهارات!

(rr-overview-barriers-incentives)=
## حوافز محدودة لتقبل النقد و كشف الأخطاء

يتضمن [التعديل الخامس](https://en.wikipedia.org/wiki/Fifth_Amendment_to_the_United_States_Constitution) لدستور الولايات المتحدة بندا ينص على أنه لا يجوز إجبار أي شخص في أي قضية جنائية على أن \[يكونوا] شاهدين على [أنفسهم\] (معدلة للغة محايدة جندريًا). يعني مصطلح "التمسك بالتعديل الخامس" أن شخصاً ما يختار عدم تقديم دليل على احتمال وجود خطأ ما في سلوكه السابق, They have the right to remain silent.

نحن نعلم أنه لا أحد يريد أن يورط نفسه، كما نعلم أنه لا أحد معصوم من الخطأ, و وضع برمجياتك و بياناتك على الإنترنت يمكن أن يكون أمرا فاضحا و مرهبا، و من الطبيعي للإنسان أن يخشى نقد الآخرين. بالرغم من أنه لا يوجد _قانون_ يضبط التواصل حول البحث القابل لإعادة الإنتاج (Reproducible research), إلا إذا ارتكبت احتيالا صريحا في عملك, فإن مشاركة الأخطاء التي تجدها في عملك مثبطة للغاية.

```{figure} ../../figures/make-ok-to-be-human.jpg
---
height: 500px
name: make-ok-to-be-human
alt: A cartoon of a woman holding a folder of files and looking worried. فقاعة تفكير تقول، إذا شاركت بياناتي قد يجد الناس فيها أخطاءً. النص التوضيحي على الصور يقول الحاجة يجب أن يصير من المقبول أن تكون إنسانا.
---
مثال توضيحي لحاجز "التمسك بالتعديل الخامس" حيث تثبط ثقافتنا الحالية عن الاعتراف بالأخطاء وتصحيحها.
Illustration by The Ludic Group LLP from Kirstie Whitaker's keynote presentation at Scientific Data in 2017.
Used under a CC-BY 4.0 license.
DOI: [10.6084/m9.figshare.5577340.v1](https://doi.org/10.6084/m9.figshare.5577340.v1).
```

إن كشف نفسك للنقد، خاصة إذا ما وجدت أخطاء في الأعمال المنشورة، أمر صعب ومجهد, لكننا بحاجة إلى موازنة هذه التكلفة الفردية مقابل واقع أن نشر البرمجيات يمكن أن يسمح للباحثين الآخرين بالإدلاء بملاحظات، التعلم و إمكانية مساعدتهم في بحثهم. في الواقع، يمكن الجزم تقريبا أن نشر البرمجيات و توثيق البيانات الخاصة بك من إثره أن يحفزك على إجراء تحاليل بحثك وفق معايير أعلى, إضافة إلى أن توخي الحذر بشأن ما تكتبه وتوثيق قراراتك، يمكن أن يساهم في توليد أفكار جديدة لك و لغيرك.

والأهم من ذلك، أننا في حاجة للاستغناء عن عقلية الامتناع عن نشر أي شيء أكثر أمانا من نشر _ أي شيء_. يهدف _منهج تورينج_ إلى مساعدتك على اتخاذ خطوات صغيرة نحو جعل عملك قابلا لإعادة الإنتاج بالتزامن مع تقدم حياتك المهنية, نحن لا نريد لأي شخص أن يشعر أنه وحيد، أو "ليس بالكفاءة المطلوبة" عندما يبدأ و يواصل رحلته في البحث المفتوح.

(rr-overview-barriers-publication)=
## Publication bias towards novel findings

Novel results are not necessarily accurate or interesting but they are rewarded in the academic world! Papers that do not find statistically significant relationships are hard to publish, particularly if the results *do not* reproduce previously published findings. (That includes statistically significant findings that go in the opposite direction to already published work.) Similarly, an article might be less likely to be accepted to a journal or a conference if it successfully reproduces already-published results instead of producing a new set. There's a good chance that reviewers will say "we already know this" and reject the submission.

The bias towards novelty in data science means many researchers are disincentivised from doing the work to document, test and share their code and data. John Ioannidis published an influential paper in 2005 titled "Why Most Published Research Findings Are False" {cite:ps}`Ioannidis2005False` which discusses the many factors that contribute to publication bias. Given these biases, it is very likely that there is a lot of duplicated work in data science. Too many different researchers are asking the same question, not getting the answer they expect or want, and then not telling anyone what they have found.

This barrier is not specific to computational reproducibility as we define it in _The Turing Way_. However, it is a major cultural barrier to {ref}`transparent communication<cm>`, and affects {ref}`project design<pd>`. _The Turing Way_ community are advocating in all the places we are able, for the systemic culture change that is required to dismantle the current publication and academic credit biases towards novelty over rigour.

(rr-overview-barriers-standards)=
## Held to higher standards than others

A researcher who makes their work reproducible by sharing their code and data may be held to a higher standard than other researchers. If authors share nothing at all, then all readers of a manuscript or conference paper can do is trust (or not trust) the results.

If code and data are available, peer reviewers may go looking for differences in the implementation. They may come back with new ideas on ways to analyse the data because they have been able to experiment with the work. There is a risk that they then require additional changes from the authors of the submitted manuscript before it is accepted for peer review.

و كما ذكرنا في قسم {ref}`"التمسك بالتعديل الخامس"<rr-overview-barriers-incentives>` أعلاه, فإن الحل لهذا التحدي يكمن في توحيد الحوافز المهنية حتى يكون فعل الأفضل من أجل _العلم_ مفيدا للأفراد المشتركين أيضا.

(rr-overview-barriers-promotion)=
## Not considered for promotion

In the current academic system, a primary consideration for promotion is the proven ability to be awarded grants and recruit students. Both funding bodies and prospective students value novelty and this behaviour is reflected in preferentially rewarding papers with a high [journal impact factor](https://en.wikipedia.org/wiki/Impact_factor). It is likely part of the human condition to be motivated by things that are new or surprising, but as {ref}`discussed above<rr-overview-barriers-publication>`, this bias towards novelty causes a systematic publication bias.

More broadly, the promotion system in academia tends to reward individuals who have shown themselves to be different from others in their field. That means sharing code and data to make it easy for "competitors" to do the same work ends up being discouraged by promotion and funding selection panels. A good example of this bias is the Nobel Prize award which only goes to a small number of researchers each year, and as such ["overlooks many of its important contributors"](https://www.theatlantic.com/science/archive/2017/10/the-absurdity-of-the-nobel-prizes-in-science/541863/) (Ed Yong, The Atlantic, 2017). One of the goals of _The Turing Way_ is to draw attention to the misalignment of the tenure and promotion process with collaborative and reproducible data science.

(rr-overview-barriers-infrastructure)=
## Big data and complex computational infrastructure

Big data is conceptualised in different ways by different researchers. "Big" data may be complex, come from a variety of data sources, is large in storage volume and/or be streamed at very high temporal resolution. Although there are ways to set random seeds and take snapshots of a dataset at a particular moment in time, it can be difficult to have identical data across different runs of an analysis pipeline. This is particularly relevant in the context of tools for parallel computing. For example, some data such as flight tracking or internet traffic is so big that it can not be stored and must be processed as it is streamed in real time.

A more common challenge for "big data" researchers is the variability of software performance across operating systems and how quickly the tools change over time. An almost constantly changing ecosystem of data science technologies is available, which means reproducing results in the future is highly variable and dependent on using perfectly backwards compatible tools as they develop. Very often the results of statistical tests will vary depending on the configuration of the infrastructure that was used in each of the experiments, making it very hard to independently reproduce a result. Experiments are often dependent on random initialisation for iterative algorithms and not all software includes the ability to fix a pseudorandom number without limiting parallelisation capabilities (for example in Tensorflow). These tools can require in depth technical skills which are not widely available to data scientists. The [Apache Hadoop](https://hadoop.apache.org/) framework, for instance, is extremely complex to deploy data science experiments without strong software and hardware engineering knowledge.

Even "standard" high performance computing, can be difficult to set up to be perfectly reproducible, particularly across different cloud computing providers or institutional configurations. _The Turing Way_ contains chapters to help data scientists learn skills in {ref}`reproducible computational environments<rr-renv>` including {ref}`containers<rr-renv-containers>` such as docker and ways to {ref}`version control your software libraries<rr-renv-package>`. We are always [open to more contributions](https://github.com/alan-turing-institute/the-turing-way/blob/main/CONTRIBUTING.md) as the technology to support reproducible research in very large datasets or for complex modelling evolves.

(rr-overview-barriers-notright)=
## Being reproducible does not mean the answer is right

By making the code and data used to produce a result openly available to others, our results may be **reproduced** but mistakes made by the initial author can be carried through. الحصول على نفس الإجابة الخاطئة في كل مرة هو خطوة في الاتجاه الصحيح، ولكن لا يزال هناك الكثير من الإجابة **** الخاطئة!

This barrier isn't really a _barrier_ to reproducible research as much as a caveat that investing time in reproducibility doesn't necessarily mean that you're doing better science. You can consider computational reproducibility as being necessary but not sufficient for high quality research. A critical approach is needed, rather than naively using existing software or implementing statistical methods without understanding what they do. See, for example, [a discussion](https://ryxcommar.com/2019/08/30/scikit-learns-defaults-are-wrong) in August 2019 about whether the default settings for Scikit-learn's implementation of logistic regression are misleading to new users. Interpretability and interoperability are required to properly evaluate the original research and to strengthen findings.

(rr-overview-barriers-time)=
## Takes time

Making an analysis reproducible takes time and effort, particularly at the start of the project. This may include agreeing upon a {ref}`testing framework<rr-testing>`, setting up {ref}`version control<rr-vcs>` such as a Github repository and {ref}`continuous integration<rr-ci>`, and {ref}`managing data<rr-rdm>`. Throughout the project, time may be required to maintain the reproducible pipeline.

Time may also be spent communicating with collaborators to agree on which parts of the project may be open source and when and how these outputs are shared. Researchers may find that they need to "upskill" their colleagues to allow the team to benefit from reproducibility tools such as git and GitHub, containers, Jupyter notebooks, or databases.

```{figure} ../../figures/help-you-of-the-future.jpg
---
width: 500px
name: help-you-of-the-future
alt: A cartoon of a woman passing a folder of documents back to herself. Speech bubble says You're mainly keeping records for you in the future.
---
Although making clear documentation may feel like it is taking a lot of time at the moment, you are helping your and your collaborators remember what you have done so it is easy to reuse the work or make changes in the future.
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

As you can tell from the ever-growing number of chapters in _The Turing Way_, working reproducibly requires skills that aren't always taught in training programmes. You - or someone in your team - might need to develop expertise in data engineering, research software engineering, technical writing for documentation or project management on GitHub. That is a major barrier when the current incentive structures are not aligned with learning these skills (see the barriers on {ref}`plead the fifth<rr-overview-barriers-incentives>`, {ref}`publication bias towards novel findings<rr-overview-barriers-publication>`, {ref}`held to higher standards than others<rr-overview-barriers-standards>`, and {ref}`not considered for a promotion<rr-overview-barriers-promotion>`!) However, this is the primary barrier that we at _The Turing Way_ are working to dismantle with you. We hope you enjoy learning these skills with us and that you'll help us to improve the book as you do.

> "A journey of a thousand miles begins with a single step" (Chinese philosopher [Lao Tzu](https://en.wikipedia.org/wiki/A_journey_of_a_thousand_miles_begins_with_a_single_step)).

We hope that by working towards helping you learn some of these valuable skills we also dismantle some of the more structural barriers to reproducible research.

## Further reading and additional resources

You can watch Kirstie Whitaker describe some of these barriers in [her talk about _The Turing Way_](https://youtu.be/wZeoZaIV0VE?t=312) at [csv,conf,v4](https://csvconf.com/2019) in May 2019. You can use and re-use her slides under a CC-BY licence via Zenodo (doi: [10.5281/zenodo.2669547](https://doi.org/10.5281/zenodo.2669547)). The section describing the slide below starts around 5 minutes into the video.
