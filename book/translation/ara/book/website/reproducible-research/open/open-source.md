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
- _إنه ممتع_: المصدر المفتوح يوفر مجموعة لا نهاية لها من المكعبات الروبيكس المتغيرة لحلها في عطلة نهاية الأسبوع. Just like puzzles, both crossword and jigsaw, open source provides bite-sized intellectual escapes.

(rr-open-source-benefitsresearch)=
## How Open Source Software Benefits Research

وهناك عدة طرق تفيد فيها البرمجيات المفتوحة المصدر البحث:

(rr-open-source-benefitsresearch-reusable)=
### Re-usable

Open source software projects allow researchers to take advantage of each others’ work. This enables researchers to apply their efforts to high-value work. It is sometimes said that “all the easy problems have already been solved”. Blogging, content management, and operating systems are all problems with established (and mainstream) open-source solutions, to name a few. While developers could spend their time reinventing wheels that the open-source community has already perfected, it is highly preferable to use the world’s best wheel, especially when that wheel comes at no cost to you. This reduces duplication of effort and allows researchers to focus on yet-unsolved challenges.

{ref}`إعادة استخدام rr-code` يوفر قائمة أكثر تعمقا لمختلف الجوانب التي يجب النظر فيها لجعل التعليمات البرمجية الخاصة بك أكثر قابلية لإعادة الاستخدام. سواء كان هذا النص نصياً صغيراً أو مكتبة.

(r-open-source-efitsresearch-checkable)=
### Checkable

وتسمح المشاريع المفتوحة المصدر لمجتمع البحوث الأوسع بقراءة واختبار شفرة بعضها البعض. بهذه الطريقة، يمكن العثور على الأخطاء بسرعة أكبر، والباحثون الآخرون يمكنهم التحقق من النتائج.

(r-open-source-efitsresearch-cooperative)=
### Collaborative
كما أن العمل علناً يسمح لأي عدد من الباحثين بالتعاون في المشاريع التي لا يمكن وضعها بواسطة باحثين/أفرقة بحثية منفردة. وتشمل الأمثلة [لينوكس](https://www.linux.org/) أنظمة التشغيل، حزم بايثون مثل [scipy](https://www.scipy.org/) و [numpy](http://www.numpy.org/)، ومكتبة تعلم الآلات [TensorFlow](https://www.tensorflow.org/).

(r-open-source-run)=
## How to Run Your Open Source Software Project

يمكنك أن تفتح مصدر فكرة أو عمل جاري أو بعد سنوات من غلق المصدر. في المستوى الأساسي جدا، كل ما عليك فعله هو وضع التعليمات البرمجية الخاصة بك على الإنترنت في مكان ما من المحتمل أن يستمر لفترة طويلة. يمكنك جعل التعليمات البرمجية الخاصة بك قابلة للاستشهاد بها عن طريق تعيينه معينا [{term}`def<Digital Object Identifier>`] (على النحو الذي نوقش في القسم الخاص بـ {ref}`rr-rdmsharing`). وهذا يساعد على ضمان حصولك على رصيد مناسب إذا كان الناس يستخدمون عملك أو يستندون إليه.

المكان الشائع لجعل تعليماتك البرمجية متاحة هو GitHub [{term}`def<Github>`] (انظر الفصل على {ref}`rr-vcs`). يجب عليك تضمين ملف ترخيص ينص على أن أي شخص لديه إذن لاستخدام العمل الخاص بك ونسخه وتعديله. وبدون ذلك، لا يمكن لأحد أن يستخدم عملك بصورة قانونية، وبالتالي فهو ليس مصدرا مفتوحا. الفصل {ref}`ترخيص rr-licen` سيساعدك على اختيار أفضل ترخيص لمشروعك. هناك أيضا بعض الملفات الأخرى التي يجب أن تضمنها مع الرمز الخاص بك، كما هو مبين أدناه.

(r-open-source-run-readme)=
### Welcome Users by Adding Information to Your README

يجب أن تحتوي على ملف '{term}`def<README>`حيث تحتوي على معلومات مفيدة حول ما هو المشروع، كيفية استخدامه، وكيفية المساهمة فيه. وفيما يلي قائمة بالأشياء الرئيسية التي ينبغي أن تتضمن إعادة تنظيمها:

- _The project name and what it is_: This will significantly help someone that comes across it to get an idea of the project. Include a few key points that describe the main features of the project and what features you are implementing. This helps to quickly compare other projects with yours and gives an idea of why the project exists in the first place.
- _Instructions on how to install the project_: The installer might be a collaborator, someone that comes across and is interested in the project, or even you - if you get a new machine and need to re-install your project. Nevertheless, it is a total waste of your resources to figure out how to get started with the project from scratch. The instructions should also include any prerequisites that will be needed to run the project. The best thing you can do is to write up the installation instructions when you first do them yourself, and you will quickly save hours of work in the future.
- _Instructions for how to run the code and any associated tests_: If you've been working on your project it may seem obvious how to run it, but this will likely not be the case for someone coming across it for the first time.
- _Links to related material_
- _List of authors/contributors to the project, possibly with contact information_
- _Acknowledgements_

لنفترض أنك تنوي أن يتعاون أشخاص آخرين في مشروعك (بدلاً من مجرد إتاحة التعليمات البرمجية الخاصة بك والنظر في إكمالها). في تلك الحالة، يجب أن تتضمن مبادئ توجيهية للمساهمة، وعلى الأرجح مدونة سلوك.

(r-open-sour-run-guidelines)=
### Contributing Guidelines

المبادئ التوجيهية المساهمة [{term}`def<Contributing Guidelines>`تخبر جمهورك عن كيفية المشاركة في مشروعك. على سبيل المثال قد تضمّن معلومات عن:

- How to file a bug report
- How to suggest a new feature
- Your roadmap or vision for the project
- How contributors should (or should not) get in touch with you

استخدام لهجة دافئة وودية وتقديم اقتراحات محددة للمساهمات (مثل كتابة الوثائق)، أو إنشاء موقع على شبكة الإنترنت) يمكن أن يقطع شوطا طويلا في جعل الوافدين الجدد يشعرون بالترحيب والحماس للمشاركة. على سبيل المثال ، [المشرف النشط](https://activeadmin.info/index.html) يبدأ [دليل المساهمة](https://github.com/activeadmin/activeadmin/blob/master/CONTRIBUTING.md) الخاص به : "أولاً ، شكراً لك على النظر في المساهمة في المشرف النشط. أناس مثلك هم الذين يصنعون المشرف النشط مثل هذه الأداة الرائعة."

في المراحل الأولى من مشروعك، يمكن أن يكون ملف المبادئ التوجيهية المساهم بسيطاً. يجب عليك دائماً شرح كيفية الإبلاغ عن الأخطاء أو المشكلات في الملف، وأي متطلبات تقنية (مثل الاختبارات) لتقديم المساهمة. مع مرور الوقت، قد تضيف أسئلة أخرى متكررة هنا أو في ملف القراءة الخاص بك. كتابة هذه المعلومات تعني أن عددا أقل من الناس سيوجهون إليك نفس الأسئلة مرارا وتكرارا. من الجيد أيضا ربط ملف المبادئ التوجيهية الخاص بك المساهمة من README، لذا يرى المزيد من الناس ذلك.

(r-open-source-run-conduct)=
### Code of Conduct

تساعد مدونة قواعد السلوك [{term}`def<Code of Conduct>`] على وضع قواعد أساسية للسلوك للمشاركين في مشروعك. هذا مهم بشكل خاص إذا كنت تقوم بإطلاق مشروع مفتوح المصدر لمجتمع أو شركة. وهناك مدونة لقواعد السلوك تمكنك من تيسير السلوك المجتمعي الصحي والبناء، الذي سيقلل من الإجهاد كمشرف. وهو ينقل كيف تتوقع من المشاركين أن يتصرفوا ويصف من تنطبق عليهم هذه التوقعات، وعندما يتقدمون بطلباتهم وما ينبغي أن يفعلوا في حالة حدوث انتهاك.

مثل التراخيص المفتوحة المصدر، هناك أيضا معايير ناشئة لمدونات قواعد السلوك، لذلك لا يتوجب عليك كتابة رخصتك. [العهد الخاص بالمساهم](https://contributor-covenant.org/) هو مدونة قواعد سلوك غير مسبوقة يستخدمها [أكثر من 000 40 مشروع مفتوح المصدر](https://www.contributor-covenant.org/adopters). بغض النظر عن النص الذي تستخدمه، يجب أن تكون مستعدا لإنفاذ مدونة قواعد السلوك الخاصة بك عند الضرورة.

حافظ على الملف في الدليل الجذر للمشروع الخاص بك، لذلك من السهل العثور عليه، وربطه من README.

(r-open-source-contribute)=
## How to Contribute to Other's Open Source Software Projects

(r-open-source-contribute-anatomy)=
### Anatomy of an Open Source Software Project

كل مجتمع مفتوح المصدر مختلف. ومع ذلك، فإن العديد من مشاريع برمجيات المصدر المفتوح تتبع هيكلا تنظيميا مماثلا. ففهم الأدوار المختلفة للمجتمع المحلي والعملية العامة سيساعدك على التوجُّه بسرعة نحو أي مشروع جديد.

ويضم مشروع نموذجي للبرمجيات المفتوحة المصدر الأنواع التالية من الأشخاص:

- _Author_: The person/s or organization that created the project.
- _Owner_: The person/s who has administrative ownership over the organization or repository (not always the same as the original author).
- _Maintainers_: Contributors who are responsible for driving the vision and managing the organizational aspects of the project. They may also be authors and/or owners of the project.
- _Contributors_: Everyone who has contributed something back to the project.
- _Community Members_: People who use the project. They might be active in conversations or express their opinion on the project's direction.

وقد يكون للمشاريع الكبرى أيضا لجان فرعية أو أفرقة عاملة تركز على مهام مختلفة مثل الأدوات والفرز والاعتدال المجتمعي وتنظيم المناسبات. انظر إلى موقع المشروع على شبكة الإنترنت لصفحة "الفريق"، أو في مستودع وثائق الحكم، للعثور على هذه المعلومات.

يتم استضافة عدد كبير من المشاريع المفتوحة المصدر على GitHub (انظر الفصل الخاص بالتحكم في الإصدارات لمزيد من التفاصيل)، والتي تحتوي على تسهيلات مثل:

- _Issue tracker_: Where people discuss issues related to the project.
- _Pull requests_: Where people discuss and review changes that are in progress.
- _Discussion forums or mailing lists_: Some projects may use these channels for conversational topics (for example, "How do I..." or "What do you think about..." instead of bug reports or feature requests). Others use the issue tracker for all conversations.
- _Synchronous chat channel_: Some projects use chat channels (such as Slack or IRC) for casual conversation, collaboration, and quick exchanges.

(بآلاف دولارات الولايات المتحدة)
### Contribute Your Changes

قل أنك قمت بإضافة ميزة أو إصلاح خطأ وترغب في المساهمة بهذا العمل في المشروع الرئيسي.

1. _Read the documentation_: The main project may have contributing guidelines or information in a README instructing prospective contributors on how to supply their changes.
2. _Make sure your conventions match the style and structure of the main project_: For example, if all the variables in a project are named in some particular way yours should be too. Consistent conventions make it much easier for someone who has not seen your piece of the project before to understand it rather than having to figure out your particular set of conventions *and* what the code is doing. The project's conventions may be outlined in its documentation, or may just be evident from inspection of the code itself.
3. _Break your changes up into manageable, well-defined chunks_: For example, if you have added two separate features, do not submit them together. Keeping things "clean" in this way makes your work simpler to understand and review.
4. _Test your changes_: If the project comes with tests, run them. Make sure you are testing against an up to date version of the project as it may have evolved considerably over time. Write specific tests for your changes and submit those too.
5. _Do not just submit code, update relevant documentation too_: If your changes are incorporated, it will have to be updated. If you do not do it, someone else will have to.
6. _Ask questions_: If there are things you are unsure about, there is no harm in asking. Many larger projects have dedicated forums or other venues for questions and discussion.
7. _Be clear_: When you submit your changes, clearly describe the changes you have made, why you have made them, and how they have been implemented. This makes it as easier for someone looking at your work and deciding whether to incorporate it into the main project to do so. In the likely case the main project is hosted on GitHub, you should put this in the pull request (see the chapter {ref}`rr-vcs` for more details).

(r-open-source-look te-contribuking)=
### Looking for Projects to Contribute to and How to Contribute to Them

ولست بحاجة إلى المبالغة في التفكير في ما ستكون عليه مساهمتك الأولى بالضبط، أو كيف ستبدو هذه المساهمة. بدلاً من ذلك، ابدأ بالتفكير في المشاريع التي تستخدمها بالفعل أو تريد استخدامها. المشاريع التي ستساهم بها بنشاط هي المشاريع التي تجد نفسك ستعود إليها. في إطار تلك المشاريع، كلما كنت تلتقط نفسك تفكيرا بأن شيئا ما يمكن أن يكون أفضل أو مختلفا، تتصرف على غريزتك. قد تقوم بفحص README وتعثر على رابط مكسور أو طابعي. بدلاً من ذلك، يمكنك أن تكون مستعملاً جديداً وأن تلاحظ أن شيئاً ما معطل، أو أن تجد مشكلة تعتقد أنه ينبغي أن تكون في الوثائق. بدلاً من تجاهله والمضي قدماً، أو مطالبة شخص آخر بإصلاحه، انظر ما إذا كان يمكنك المساعدة عن طريق الإمساك. وهذا هو كل ما يدور حوله المصدر المفتوح.

يمكنك أيضًا استخدام أحد المصادر التالية لمساعدتك على اكتشاف المشاريع الجديدة والمساهمة فيها:

- [Open Source Friday](https://opensourcefriday.com/)
- [First Timers Only](https://www.firsttimersonly.com/)
- [CodeTriage](https://www.codetriage.com/)

إذا لم تكن متأكداً من كيفية البدء، فهناك بعض الطرق الأخرى التي يمكنك أن تدور حولها، مثل العثور على مشكلة مفتوحة للمعالجة أو السؤال عما إذا كان بإمكانك المساعدة في كتابة ميزة جديدة.

من المفاهيم الخاطئة الشائعة عن المساهمة في المصدر المفتوح هو أنك بحاجة إلى المساهمة في التعليمات البرمجية. والواقع أن الأجزاء الأخرى من المشروع هي التي غالبا ما تكون أهملت أو أغفلت أكثر من غيرها. سوف تقوم بعمل المشروع لصالح كبير من خلال عرض التلاعب بهذه الأنواع من المساهمات. يمكنك:

- Review code on other people's submissions.
- Write and improve the project's documentation.
- Curate a folder of examples showing how the project is used.
- Answer questions about the project on, for example, Stack Overflow,
- Keep things organized, for example, on GitHub by:
    - Linking to duplicate issues.
    - Suggesting new issue labels.
    - Going through open issues and suggesting closing old ones.
    - Ask clarifying questions on recently opened issues to move the discussion forward.

(r-open-source-مغلقة)=
## Closed Software

ماذا لو كنت تعمل مع أشخاص لا يستخدمون نموذج المصدر المفتوح لبرامجهم؟ وقد يبدو ذلك في البداية إهانة لجميع المبادئ التي نوقشت حتى الآن. غير أنه توجد في العادة أسباب وجيهة جدا وراء كون الأشياء هي الطريقة التي تكون بها (مثل الأسباب القانونية أو التجارية أو الأمنية). وفي كثير من الأحيان، سيظل من الممكن الاستخدام والإسهام، ولكن تفاصيل كيف يمكن أن تكون مختلفة. وأنواع الممارسات المستخدمة في البرمجيات ”المغلقة“ هي نفسها عموما، والمفاهيم والأدوات التي يمكنك تعلمها في طريق تورينج لا تزال تطبق.

غير أنه قد لا تكون هناك في بعض الأحيان أسباب وجيهة لنهج المصدر المغلق. ولمختلف مجالات البحث ثقافات مختلفة تتعارض مع المبادئ المفتوحة وتشعر بالإحباط الشديد. والتصدي لهذا الحاجز يمكن أن يكون صعبا جدا لأن الثقافات قد تستغرق سنوات أو عقودا لكي تتغير.

العمل مع البرمجيات المغلقة يمكن أن يوفر فرصاً وتهديدات لبحثك. وفي جميع الحالات، يتيح فهم وجهات نظر الآخرين واحترامها أكبر فرص النجاح.
