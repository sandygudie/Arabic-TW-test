(rr-open-data)=
# Open Data

يشهد العالم تحولاً عالمياً كبيراً تيسره التكنولوجيا ووسائط الإعلام الرقمية، وتغذيه البيانات والمعلومات، وينطوي هذا التحول على إمكانات هائلة لتشجيع إجراء بحوث أكثر شفافية، ومساءلة، وكفاءة، واستجابة، وفعالية، ولا تُنشر سوى نسبة ضئيلة جداً من البيانات الأصلية في المجلات التقليدية، وعلى الرغم من السياسات القائمة بشأن أرشفة البيانات، فإن بيانات الممارسة اليوم تُخزن في المقام الأول في ملفات خاصة، وليس في مستودعات مؤسسية آمنة، لا يتمكن احد من الوصول لها أو الاطلاع عليها (وفي كثير من الأحيان حتى الباحث الذي أصدر البيانات)،

This lack of data sharing is an obstacle to international research (be it academic, governmental, or commercial) for two main reasons:

1. It is generally difficult or impossible to reproduce a study without the original data.
2. و لا يمكن للباحثين الآخرين إعادة استخدام البيانات أو إدماجها في أعمال جديدة إذا لم يتمكنوا من الوصول إليها،

وبناءاً على ذلك، هناك ثورة عالمية جارية في مجال البيانات تسعى إلى تعزيز التعاون وإنشاء وتوسيع برامج بحوث فعالة تَتَّسم بالكفاءة. Open data [{term}`def<Open data>`] is crucial to meeting these objectives. وهي متاحة مجاناً على الإنترنت. ويُسمح لأي مستخدم بتنزيلها أو نسخها أو تحليلها أو معالجتها أو إعادة استخدامها لأي غرض آخر مع حواجز مالية، وقانونية، وتقنية أقل.

وهذا يمثل تحولاً حقيقياً في كيفية عمل البحوث. Funders are starting to require researchers to make their data available and submit data management plans {ref}`Data Management Plans<rr-rdm-dmp>` as part of project proposals. وفي الوقت الراهن، كثيراً ما يتعيَّن على أي شخص يرغب في استخدام بيانات من أحد الباحثين أن يتصل بذلك الباحث وأن يقدم طلباً، وإذا كان الوصول إلى البيانات مقيداً، لأسباب أمنية على سبيل المثال، فينبغي توضيح مبررات ذلك، وإذا كان الوصول إلى البيانات مقيداً، لأسباب أمنية على سبيل المثال، فينبغي توضيح مبررات ذلك، ثم إن وحرية الوصول إلى البيانات واستخدامها فيما بعد، يُعد ذا قيمة كبيرة للمجتمع والاقتصاد، ولذلك ينبغي أن تكون تلك البيانات مفتوحة بشكل تلقائي وألا تكون مغلقة إلا عند الضرورة،

يمكنك العثور على المزيد حول الخطوات العملية لجعل بياناتك متاحة في القسم الذي يصف {ref}`خطوات مشاركة البيانات <rr-rdm-sharing-steps>` في الفصل الفرعي: {ref}`مشاركة وأرشفة البيانات<rr-rdm-sharing>`.

(rr-open-data-barriers)=
## عوائق (Data Sharing) مشاركة البيانات
ويجد العديد من الأكاديميين أن مشاركة البيانات أمر صعب. وأوضحت الدراسات الاستقصائيّة الأخيرة {cite:ps}`Stuart2018sharing` التي أُجريت بين الباحثين تسرد الأسباب التالية:

- تنظيم البيانات بطريقة قابلة للعرض ومفيدة يُعدّ أمراً صعباً (كما ذكر 46 في المائة من الأشخاص)
- الباحثون غير متيقِّنين من حقوق النشر والتأليف والترخيص (كما ذكر 37 في المائة من الأشخاص)،
- كما انه لا يعرف الباحثون أي مستودع يمكن استخدامه لأنواع مختلفة من البيانات (كما ذكر 33 في المائة)

وهذه تحديات ثقافية يمكن التصدي لها في الممارسة المتغيرة التي تمضي قدماً. بَيد أن هناك أيضاً أسباباً قانونية أو أخلاقية أو تعاقدية تحول أحياناً دون إتاحة البيانات للجمهور بكاملها أو حتى أجزاء منها، بَيد أن هناك أيضاً أسباباً قانونية أو أخلاقية أو تعاقدية تحول أحياناً دون إتاحة البيانات للجمهور بكاملها أو حتى أجزاء منها،

```{figure} ../../figures/data-privacy.jpg
---
height: 500px
name: data-privacy
alt: An image detailing why private data should be used. A person stands next to a well with 'private data' written on it and a padlock around it. It is black and white and blue. The text lists that 'people deserve - dignity, agency, privacy, rights, confirmed consent.'
---
_The Turing Way_ project illustration by Scriberia. Original version on Zenodo. [http://doi.org/10.5281/zenodo.3695300](http://doi.org/10.5281/zenodo.3695300)
```

(rr-open-data-barriers-privacy)=
### Privacy And Data Protection

تنطوي العديد من مجالات البحث على العمل بالبيانات الشخصية الحساسة، علماً بأن البحوث الطبية هي أوضح مثال على ذلك. ويجب حماية الأفراد من إعادة تحديد هُوِيَّتهم عن طريق بياناتهم المستخدمة في البحوث، وقد يكون إخفاء هُوِيَّة البيانات كافياً في بعض الحالات، ولكن ضمان عدم إمكانية إعادة تحديد الهُوِيَّة يُصبح صعباً بصورة متزايدة وذلك بسبب التقدم التقني، ونُموّ الطاقة الحاسوبية، - ومن المفارقات العجيبة - نُموّ البيانات المفتوحة، فعلى سبيل المثال، قد يكون من الممكن تحديد الهُوِيَّة عن طريق التنقيب في البيانات التي يمكن الوصول إليها وما يسمى بأشباه المُعرفات، وهي مجموعة من الخصائص (المشتركة) المحددة ــ في تركيبها ــ بحيث يمكن استخدامها للتعرف على الأفراد،

وقد يظَل الحفاظ على الخصوصية ممكناً إذا تم توفير مجموعات بيانات جزئية أو عامة. على سبيل المثال، من الممكن أن تُقَدِّم نطاقات عُمرية بدلاً من تاريخ الميلاد أو أول رقمين فقط من الرموز البريدية، وقد يكون من الممكن أيضاً توفير البيانات في شكل يُتيح للباحثين الاستفسار عنها مع إبقاء البيانات نفسها مغلقة، على سبيل المثال، قد يكون المستخدم قادراً على إرسال استفسار لاسترداد متوسط مجموعة البيانات، ولكن لا يمكنه الوصول إلى أي من نِقَاط البيانات الفردية،

وتنطوي العديد من مجالات التخصصات العلمية على العمل بالبيانات الشخصية الحساسة، وتُنظَّم إدارتها تنظيماً جيّداً في تشريعات حماية البيانات (في أوروبا من خلال التنفيذ الوطني للقواعد العامة لحماية البيانات) والإجراءات الأخلاقية كما هي راسخة في معظم مؤسسات البحث {cite:ps}`EU2016protection`.

(rr-open-data-barriers-consent)=
### Consent

ولكي تُتاح بيانات البحث المجهولة لإعادة الاستخدام في المستقبل، يجب أن تشمل استمارات الموافقة مشاركة هذه البيانات مع باحثين آخرين، تُشير البحوث حتى الآن إلى أن المشاركين في الدراسة عادة ما يكونون أقل اهتماماً بالبيانات التي يتم أرشفتها ومشاركتها مما يعتقد الباحثون {cite:ps}`Kuula2010archiving`. وينبغي أن تتضمن أوراق المعلومات المقدّمة من المشاركين واستمارات الموافقة كيفية تخزين البيانات البحثية، وحفظها واستخدامها في الأمد الطويل، وكيفية حماية السرية عند الحاجة.

(rr-open-data-barriers-anonymisation)=
### Anonymisation

Individuals must be protected from (re)identification through their data Anonymisation of the data may be sufficient in some cases, but ensuring that re-identification is not possible is becoming increasingly difficult. It might even be impossible due to technical progress, growing computational power and – ironically – more open data.

For example, re-identification may be possible via data-mining of accessible data and so-called quasi-identifiers, a set of (common) properties that are – in their combination – so specific that they can be used to identify an individual. Preserving privacy may still be possible if partial or generalised datasets are provided, like age groups instead of birth date, or only the first two digits of postal codes. It may also be possible to provide the data in such a format that researchers can query whilst keeping the data itself closed. على سبيل المثال، قد يكون المستخدم قادراً على إرسال استفسار لاسترداد متوسط مجموعة البيانات، ولكن لا يمكنه الوصول إلى أي من نِقَاط البيانات الفردية، Another way to provide anonymised data is to provide [synthetic data](https://en.wikipedia.org/wiki/Synthetic_data), data generated to reflect the conditions and properties of the raw data, without including any personal information.

(rr-open-data-barriers-national)=
### National and Commercially Sensitive Data

In many cases, companies are understandably unwilling to publish much of their data. The reasoning goes that if commercially sensitive information of a company is disclosed, it will damage the company’s commercial interests and undermine competitiveness. This is based on the thinking that in competitive markets, innovation will only occur with some protection of information. If a company spends time and money developing something new, the details of which are then made public, then its competitors can easily copy it without having to invest the same resources. The result is that no one would innovate in the first place. Similarly, for public safety concerns, governments are often unwilling to publish data that relates to issues such as national security. In such cases, it may not be possible to make data open, or it may only be possible to share partial/obscured datasets.

***Chapter Tags**: This chapter is curated for the `Turing Data Study Group` (`turing-dsg`).*
