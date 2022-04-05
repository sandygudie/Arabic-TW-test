(rr-make-resources)=
# Resources for "Make"

(rr-make-resources-manual)=
## Manual

- [دليل المرجع الرسمي ](https://www.gnu.org/software/make/manual/make.html).

(rr-make-resources-discussions)=
## Discussions

- [مناقشة حول صنع HackerNews](https://news.ycombinator.com/item?id=15041986).

- [جعل متكرر نظر في ضار](http://aegis.sourceforge.net/auug97.pdf). هذه ورقة معلومة حول لماذا لا يجب عليك استخدام المداخلات. للإيجاز: إذا فعلت هذا لا يستطيع رؤية DAG بأكمله وهذا يؤدي إلى مشاكل.

- [جعل غير متكرر نظر في ضار](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/03/hadrian.pdf): هذه ورقة بحث تصف إخفاقات صنع للبنايات الكبيرة و المعقدة.

(rr-make-resources-blogs)=
## Blogs

Of course we are not the first to suggest the use of Make for reproducibility! تم العثور على مشاركات المدونة المذكورة أدناه بعد كتابة البرنامج التعليمي أعلاه، ولكن يمكن إضافة المزيد من المعلومات والأمثلة.

- [قابلية التكرار صعبة](https://kbroman.wordpress.com/tag/reproducible-research/). مناقشة إنشاء مشروع بحث قابل للاستنساخ باستخدام Make.

- [GNU Make for Reproducible Data Analysis](http://zmjones.com/make/). لإستخدام اصنع لتحليل قابل للتكاثر في نفس النسق كما نفعل أعلاه.

- [أنابيب المعلومات الحيوية القابلة للتكرار باستخدام صنع](http://byronjsmith.com/make-bml/). دروس موسعة جدا حول استخدام اصنع لتحليل البيانات.

- [التحليل التلقائي للبيانات خطوط الأنابيب](http://stat545.com/automation04_make-activity.html). برنامج تعليمي مماثل يستخدم R للتحليل.

- [Writing a reproducible Paper](http://handbook.datalad.org/en/latest/usecases/reproducible-paper.html#automation-with-existing-tools). دروس مشابهة مع بايثون باستخدام المتغيرات لتجميع الجداول في المخطوطة .

(rr-make-resources-tools)=
## Tools

- رسم DAG لـ Makefile باستخدام [makefile2graph](https://github.com/lindenb/makefile2graph).

(rr-make-resources-alternatives)=
## Alternatives to Make

هناك [العديد من البدائل صنع](https://en.wikipedia.org/wiki/List_of_build_automation_software). في الأسفل هناك بعض الذين ألقوا القبض على عينينا، وقد يكون ذلك يستحق النظرة.

- [SnakeMake](https://snakemake.readthedocs.io/en/stable/). القائم على Python3 بديل لمايك. يدعم Snakemake العديد من البطاقات البرية في أسماء الملفات، يدعم رمز Python في القواعد. ويمكن تشغيل سير العمل على محطات العمل، مجموعات، الشبكة، وفي السحابة دون تعديل.

- [Tup](http://gittup.org/tup/index.html). نظام بناء سريع يجهز المتطلبات الأساسية من أسفل إلى أعلى بدلاً من "ماكي" من أعلى إلى أسفل. تبدو السرعة مثيرة للإعجاب والورقة التي تصفها مثيرة للاهتمام، ولكن للمشاريع الصغيرة لن تكون سرعة ماكي اختناق. بناء صيغة ملف Tupfile ليس متوافقاً مع صيغة Makefiles.

- [Bazel](https://www.bazel.build). نسخة مفتوحة المصدر من نظام بناء Blaze الخاص بجوجل.

- [Buck](https://buckbuild.com/). Facebook's build system.


