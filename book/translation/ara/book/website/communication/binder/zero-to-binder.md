(z2b)=
# صفر إلى بيندر

في هذا الفصل، سنقوم بإنشاء مشروع بيندر من الصفر: سنقوم أولاً بإنشاء مستودع على GitHub ثم نطلق على mybinder.org. الأقسام التي يتوقع أن تكمل فيها مهمة هي مشار إليها بثلاثة أضواء مرور 🚦 emojis. بعض الخطوات تعطيك خيار Python أو Julia أو R - انقر على علامة التبويب للغة المفضلة لديك.

```{admonition} Attributions
هذا البرنامج التعليمي مبني على ورشات تيم هيد التي يمكن العثور عليها هنا: <http://bit.ly/zero-to-binder> و <http://bit.ly/zero-to-binder-rise>

شكرا لآنا كريستالي و أوليفر ستريكسون على مساعدتهما في تطوير محتوى آر وجوليا، على التوالي.
```

```{attention}
قد يستغرق التحميل وقتا طويلا، ولكن هذا لا يعني بالضرورة أن Binder الخاص بك سوف يفشل في الإطلاق.
يمكنك دائماً تحديث النافذة إذا رأيت رسالة "... تستغرق وقتاً أطول للتحميل، علق بصراعة!".
```

```{admonition} If you are using R...
إذا كنت تتبع مسار R، فقد قمنا بإدراج بعض الخطوات البديلة باستخدام حزمة 'holepunch' (https://github. om/karthik/holepunch) الذي سيبني بيئتك باستخدام [صورة قاعدة الصخور](https://github.com/rocker-org/rocker) وينبغي أن يكون في نهاية المطاف أسرع لبناء وإطلاق.
```

(z2b-reqs)=
## المتطلبات

ستحتاج إلى:

- **بعض التعليمات البرمجية وبعض البيانات.** الكود يجب أن يستغرق أقل من **10 دقائق لتشغيل**، وينبغي أن تكون البيانات أقل من **10 ميغابايت**. قد يعني هذا أنك تختار فقط سكريبت واحد من مشروع أكبر، أو تجلب مجموعة فرعية من بياناتك. لاحظ أنه من المهم حقاً أن تكون التعليمات البرمجية والبيانات **عامة** لأننا سوف نستخدم مثيلة الزناد العام.
- **حساب GitHub** الرجاء التسجيل لواحد إذا لم يكن لديك بالفعل حساب واحد: <https://github.com/join>

(z2b-step-1)=
## 1. إنشاء مستودع للقرون

🚦🚦🚦

````{tabbed} Python
1) إنشاء مستودع جديد على GitHub يسمى "my-First binder"
   - تأكد من أن المستودع **عام**, _not private_!
   - لا تنسى تهيئة المستودع باستخدام README!
2) إنشاء ملف يسمى `hello.py` عبر واجهة الويب مع `print("مرحباً من Binder!")" في السطر الأول والالتزام بفرع `main`
````

````{tabbed} Julia
1) إنشاء مستودع جديد على GitHub يسمى "my-First binder"
   - تأكد من أن المستودع **عام**, _not private_!
   - لا تنسى تهيئة المستودع باستخدام README!
2) إنشاء ملف يسمى `مرحباً. l` عبر واجهة الويب مع `println("مرحباً من بيندر! )` في السطر الأول والالتزام بالفرع 'main'
3) إنشاء ملف يسمى 'Project. oml` (تحذير: الرسملة مهمة!) مع المحتوى التالي و إلتزامها بـ 'main`.
   هذا سيضع جوليا في بيئة بيندر.

   ```julia
   [compat]
   julia = "1.3"
```
````

````{tabbed} R
1) إنشاء مستودع جديد على GitHub يسمى "my-First binder"
   - تأكد من أن المستودع **عام**, _not private_!
   - لا تنسى تهيئة المستودع باستخدام README!
2) إنشاء ملف يسمى `مرحباً. ` عبر واجهة الويب مع `print("مرحبًا من Binder! )` على السطر الأول والالتزام بفرع 'main'
3) إنشاء ملف يسمى 'تشغيل'. xt` مع 'r-2022-01-01' في السطر الأول.
   يمثل هذا التاريخ لقطة من [CRAN](https://cran.r-project.org/) المستضافة على [RStudio Package Manager](https://packagemanager.rstudio.com) سنستخدم.
   قم بتوصيل هذا الملف إلى فرع "main".

   ```{note}
   في R يمكنك استخدام `holepunch::write_runtime()` لإنشاء `runtime.txt` في دليل `.binder/`؛ سيتم تكوينه مع تاريخ اليوم.
   ```
````
(z2b-public repo)=
### لماذا يجب أن يكون المستودع عامًا؟
mybinder.org لا يمكن الوصول إلى المستودعات الخاصة لأن هذا يتطلب رمزا سريا. ويختار فريق بيندر عدم تحمل مسؤولية التعامل مع الرموز السرية حيث أن mybinder.org خدمة عامة ودليل على المفهوم التكنولوجي. إذا كان الوصول إلى المستودعات الخاصة ميزة تحتاج إليها/فريقك، فإننا ننصح بأن تنظر في بناء [الخاص بك BinderHub](https://binderhub.readthedocs.io).
(z2b-step-2)=
## 2. ابدأ مستودعك الأول!
🚦🚦🚦
1) انتقل إلى **<https://mybinder.org>** 2) اكتب عنوان URL الخاص بك في مربع "GitHub repo أو URL". يجب أن تبدو هكذا:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) كما تكتب، صفحة الويب تنشئ رابط في "نسخ عنوان URL أدناه. .." علبة يجب أن تبدو هكذا: **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** 4) نسخه، قم بفتح علامة تبويب جديدة للمتصفح وقم بزيارة عنوان URL - سترى "سبينر" عندما يقوم بايندر بتشغيل المستودع
إذا كان كل شيء يسير بسلاسة، سترى واجهة JupyterLab
(z2b-Background-1)=
### ماذا يحدث في الخلفية؟ الجزء الأول
أثناء الانتظار، BinderHub (الخلفية للبندر) هو:
- جلب المستودع الخاص بك من GitHub
- تحليل المحتويات
- بناء صورة Docker استنادًا إلى المستودع الخاص بك
- إطلاق صورة Docker في السحابة
- توصيلك بها عبر المتصفح الخاص بك
(z2b-step-3)=
## 3. تشغيل البرنامج النصي
🚦🚦🚦

````{tabbed} Python
1. من لوحة الإطلاق، حدد "الطرف"
2. في النافذة الطرفية الجديدة، اكتب 'python hello.py' واضغط على العودة
````

````{tabbed} Julia
1. من لوحة الإطلاق، حدد "الطرف"
2. في النافذة الطرفية الجديدة، اكتب 'julia hello.jl' واضغط على العودة
````

````{tabbed} R
1. من لوحة الإطلاق، حدد "الطرف"
2. في النافذة الطرفية الجديدة، اكتب `Rscript -e 'source("hello.R")` ثم اضغط على العودة
````

`مرحبا من بيندر!` يجب طباعته إلى المحطة الطرفية.

(z2b-step-4)=
## 4. تثبيت التبعيات

كان من السهل البدء، لكن بيئتنا هي حبيسة - دعونا نضيف **التبعية**!

🚦🚦🚦

````{tabbed} Python
1) في مستودع الخاص بك، قم بإنشاء ملف يسمى `requirements.txt`
2) إضافة سطر يقول: `numpy==1.14.5`
3) التحقق من typos! ثم قم بالتزود بالفرع `main'
4) قم بزيارة **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** مرة أخرى في علامة تبويب جديدة
````

````{tabbed} Julia
1) في مستودعك، قم بتحرير `المشروع'. ملف oml`
2) أضف كتلة جديدة تقول:

   ```julia
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) تحقق من typos! ثم التزم بـ 'الرئيسي`.
4) قم بزيارة **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** مرة أخرى في علامة تبويب جديدة
````

````{tabbed} R
1) في مستودعك، قم بإنشاء ملف يسمى `install.R`
2) إضافة سطر يقول: `install.packages("readr")`
3) التحقق من typos! ثم قم بالالتزام بفرع `main`
4) قم بزيارة **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** مرة أخرى في علامة تبويب جديدة

```{note}
إذا استخدم `holepunch`، يمكنك إنشاء `تثبيت. '' ملف وإضافة التعليمات البرمجية تلقائياً لتثبيت جميع الإعتمادات في مشروعك باستخدام `holepunch::write_install()`.
```
````
هذه المرة، انقر فوق "بناء الجذور" في الشريط الكبير، الأفقي، الرمادي. وهذا سيتيح لك مشاهدة التقدم المحرز في البناء الخاص بك. من المفيد عندما يفشل البناء الخاص بك أو عندما يكون هناك شيء تعتقد أنه يجب _تثبيته_ مفقود.

```{note}
في بعض الأحيان يقوم بناء سجلات بيندر بطباعة الأشياء بالخط الأحمر، مثل التحذيرات بأن "الأنابيب" غير محدثة (غالباً ما يكون "الأنابيب" قديماً لأنه يتم تحديثه بانتظام! أو رسائل التثبيت، خاصة إذا كنت تستخدم R.
هذه الرسائل الحمراء لا تعني بالضرورة أن هناك مشكلة في بناءك وسوف تفشل - إنه مجرد خيار للون الخط المؤسف!
```

(z2b-Background-2)=
### ماذا يحدث في الخلفية؟ الجزء الثاني

هذه المرة، سيقوم BinderHub بقراءة ملف التكوين الذي أضفته وتثبيت الإصدار المحدد من الحزمة التي طلبتها.

(z2b-dependencies)=
### المزيد عن تثبيت التبعيات

````{tabbed} Python
في المثال أعلاه استخدمنا علامتين متساويتين (`==`) لتثبيت نسخة `numpy`.
هذا يخبر بايندر بتثبيت هذا الإصدار.

طريقة أخرى لتثبيت رقم الإصدار هي استخدام أكبر من أو يساوي للتوقيع (`>=`) للسماح بتثبيت أي إصدار أعلى من إصدار معين.
هذا مفيد عندما يكون لديك الكثير من التبعيات التي قد يكون لها تبعية على بعضها البعض ويسمح Binder بإيجاد تكوين من التبعيات الخاصة بك التي لا تتعارض مع بعضها البعض مع تجنب أي إصدارات سابقة قد تقطع أو تغير الكود الخاص بك.

أخيرا لا يمكنك توفير رقم الإصدار على الإطلاق (فقط اسم المكتبة/الحزمة) وسيقوم بايندر بتثبيت أحدث إصدار من هذه الحزمة.
````

````{tabbed} Julia
في المثال أعلاه قمنا بنسخ تجزئة إلى ملف `Project.toml` الخاص بنا والذي يتعلق بإصدار الحزمة التي نود تثبيتها.
ومن أجل رسم بياني للاعتماد الكامل، سنحتاج أيضا إلى إدراج ملف 'Manifest.toml` يوثق تبعيات التبعية.
بين هذين الملفين، يمكننا أن نشهد تكراراً دقيقاً لبيئة جوليا.

وبطبيعة الحال، يمكننا أن نتصور أنه، مع نمو البيئة وتزايد التعقيدات المترابطة، سوف تصبح كتابة هذه الملفات يدوياً مدهشة جداً!
الحقيقة هي أنك لن تفعل ذلك يدوياً، مدير الحزمة المدمج 'Pkg' يمكنه [إنشاؤه تلقائياً](https://julialang.github.io/Pkg.jl/v1/environments/).
````

````{tabbed} R
في المثال الوارد أعلاه، حددنا أننا نريد استخدام R في مشروعنا بإدراج تاريخ في `runtime.txt`.
يخبر التاريخ بايندر أي لقطة CRAN للمصدر R والطرود منها.
هذه اللقطات مستمدة من [RStudio Package Manager](https://packagemanager.rstudio.com) (RSPM).
وفي المثال المذكور أعلاه، تستخدم لقطة RSPM المؤرخة `r-2022-01-01' وتتوافر نسخة R و`readr` في ذلك التاريخ وتركيبها.
على سبيل المثال سير العمل للعمل بشكل صحيح، يرجى التأكد من عدم تقديم تاريخ قبل تاريخ المثال هذا.

يوفر هذا بعض إصدارات حزمة بدائية للمستخدمين R، ولكنه ليس قوي مثل إصدارات التثبيت في `requirements.txt` في Python.
للحصول على نسخة أكثر قوة وتحديدا في R، ألقي نظرة على حزمة [`renv`](https://rstudio.github.io/renv/).
````

(z2b-step-5)=
## 5. التحقق من البيئة

🚦🚦🚦

````{tabbed} Python
(1) من لوحة الإطلاق، حدد "Python 3" من قسم الملاحظات لفتح دفتر ملاحظات جديد
2) اكتب التالي في خلية جديدة:

   ```python
   import numpy
   print(numpy.__version__
   numpy.random. و()
   ```

   ```{attention}
   لاحظ الشرطين السفليين لكل من جانبي 'الإصدار`!
   ```

3) تشغيل الخلية لرؤية رقم الإصدار ورقم عشوائي مطبوعة

   - اضغط إما على SHIFT+RETURN أو زر "تشغيل" في شريط القوائم
````

````{tabbed} Julia
(1) من لوحة الإطلاق، حدد "جوليا" من قسم الملاحظات لفتح دفتر ملاحظات جوليا الجديد
2) اكتب التالي في خلية جديدة:

   ```julia
   باستخدام Pkg
   Pkg. طاطم()
   ```

3) تشغيل الخلية لمشاهدة رقم الإصدار المطبوع

   - اضغط إما على SHIFT+RETURN أو زر "تشغيل" في شريط القوائم
````

````{tabbed} R
(1) من لوحة الإطلاق، حدد "R" من قسم الملاحظات لفتح دفتر ملاحظات R جديد
2) اكتب التالي في خلية جديدة:

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(system). ile("extdata/mtcars. sv", pack= "readr"))
   ```

3) تشغيل الخلية

    - اضغط إما على SHIFT+RETURN أو على زر "تشغيل" في شريط القوائم
    يجب أن ترى المخرج التالي:
      - رقم الإصدار من النسخة المثبتة من `readr`
      - نسيج محتويات `mtcars. sv` وهو ملف csv مضمن في الحزمة `readr`
````

```{attention}
إذا قمت بحفظ دفتر الملاحظات، فسيتم حفظ **لا** في مستودع GitHub .
إعادة التغييرات إلى مستودع GitHub من خلال الحاوية غير ممكن مع Binder.
**أي تغييرات قمت بها على الملفات الموجودة داخل Binder سوف تفقد بمجرد إغلاق نافذة المتصفح.**
```

(z2b-step-6)=
## 6. مشاركة عملك

بايندر هو كل شيء حول مشاركة عملك بسهولة وهناك طريقتان للقيام بذلك:

- شارك رابط **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** مباشرة
- قم بزيارة **[https://mybinder. rg](https://mybinder.org)**، اكتب عنوان URL الخاص بالمرد الخاص بك وانسخ كتلة نصية "Markdown" أو "ReStrucated Tpe" في `README. (د)` ملف. هذه الكتلة ستجعل شارة يمكن للناس النقر عليها، والتي تبدو هكذا: ![عشق](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) إضافة **Markdown** snippet من **<https://mybinder.org>** إلى `README.md` ملف في repo
   - الشريط الرمادي الذي يعرض شارة الشارة سيظهر للكشف عن كتل الكود. انقر على أيقونة الحافظة بجوار المربع المميز بـ "م" لنسخ الكتلة الدماغية تلقائيا. 2) انقر فوق الشارة للتأكد من أنها تعمل!

(z2b-step-7)=
## 7. الوصول إلى البيانات في Binder الخاص بك

نوع آخر من التبعية للمشاريع هو **البيانات**. هناك طرق مختلفة لجعل البيانات متاحة في Binder الخاص بك اعتماداً على حجم البيانات الخاصة بك والتفضيلات الخاصة بك لمشاركتها.

(z2b-small files)=
### ملفات عامة صغيرة

أبسط نهج لملفات البيانات العامة الصغيرة هو إضافتها مباشرة إلى مستودع GitHub الخاص بك. ثم يتم تغطيتها مباشرة في البيئة ويتم إصدارها مع التعليمات البرمجية الخاصة بك.

هذا مثالي للملفات حتى **10 ميغابايت**.

(z2b-متوسطة الملفات)=
### الملفات العامة المتوسطة

للوصول إلى الملفات المتوسطة **من 10 دقائق ميغابايت حتى بضع مئات ميغابايت**، يمكنك إضافة ملف يسمى `بريد` إلى المستودع الخاص بك. ملف `postBubuild` هو سكريبت قميص يتم تنفيذه كجزء من بناء الصورة ويتم تنفيذه مرة واحدة فقط عند بناء صورة جديدة، ليس في كل مرة يطلق فيها البندر.

راجع [Binder `postBuild` على سبيل المثال](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) لمزيد من استخدامات `النسخة البريدية`.

```{note}
يتم بناء صور جديدة فقط عندما يرى بيندر التزاما جديدا، ليس في كل مرة تضغط فيها على رابط بيندر.
لذلك، يتم تنزيل البيانات مرة واحدة فقط عند بناء صورة Docker، وليس في كل مرة يتم فيها تشغيل Binder.
```

(z2b-Bi-files)=
### ملفات عامة كبيرة

ليس من العملي وضع ملفات كبيرة في مستودع GitHub الخاص بك أو إدراجها مباشرة في الصورة التي يبنيها Binder . الخيار الأفضل للملفات الكبيرة هو استخدام مكتبة خاصة بتنسيق البيانات لبث البيانات كما تستخدمها أو تنزيلها عند الطلب كجزء من الكود الخاص بك.

لأسباب أمنية، تقتصر حركة المرور الصادرة لـ Binder الخاصة بك على اتصالات HTTP/S أو GitHub فقط. لن تتمكن من استخدام مواقع FTP لجلب البيانات على mybinder.org.

(z2b-private-files)=
### الملفات الخاصة

وليس هناك سبيل للوصول إلى الملفات التي ليست عامة من mybinder.org. يجب أن تنظر إلى جميع المعلومات في بايندر كمعلومات عامة، بمعنى أن:

- لا يجب أن يكون هناك كلمات مرور، رموز، مفاتيح وما إلى ذلك في مستودع GitHub الخاص بك؛
- لا يجب عليك كتابة كلمات المرور في Binder قيد التشغيل على mybinder.org؛
- لا يجب عليك تحميل مفتاح SSH الخاص بك أو رمز API الخاص بك إلى Binder.

من أجل دعم الوصول إلى الملفات الخاصة، ستحتاج إلى إنشاء نشر محلي لـ [BinderHub](https://binderhub.readthedocs.io) حيث يمكنك تحديد المقايضات الأمنية بأنفسنا.

```{note}
وبناء BinderHub ليس بالمهمة البسيطة التي تضطلع بها عادة مجموعات تكنولوجيا المعلومات/RE لأسباب تتعلق بإدارة الصيانة والأمن والإدارة.
ومع ذلك، فإن ذلك لا يعني أنهم يشكلون - فقط - مجموعات من الناس الذين يجب عليهم/يمكن أن يبنوا BinderHub.
```

(z2b-step-8)=
## 8. الحصول على البيانات مع `بناء البريد`

🚦🚦🚦

````{tabbed} Python
1) انتقل إلى مستودع GitHub الخاص بك وقم بإنشاء ملف يسمى `postBuild`
2) في `postBuild`، أضف سطراً واحداً يقرأ: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` هو برنامج يسترجع المحتوى من خوادم الويب.
     هذا الخط يستخرج المحتوى من عنوان URL المرير و يحفظه إلى اسم الملف المشار إليه بعلم `O` (عاصمة "O", لا صفر)، في هذه الحالة `فجوة في الدين. Sv`.
     العلم `q` يخبر `wget` أن يفعل ذلك بهدوء، مما يعني أنه لن يطبع أي شيء لوحدة التحكم.
(3) تحديث `متطلباتك'. ملف xt` بإضافة سطر جديد مع 'pandas' عليه وسطر جديد آخر مع 'matplotlib' عليه
   - هذه الحزم ليست ضرورية لتحميل البيانات ولكن سوف نستخدمها لقراءة ملف CSV وإنشاء مخطط
4) انقر فوق شارة Binder في README لبدء Binder الخاص بك

بمجرد بدء تشغيل Binder ، يجب أن ترى ملف جديد ظهر لم يكن جزءا من المستودع الخاص بك عند النقر على الشارة.

الآن تصور البيانات عن طريق إنشاء دفتر ملاحظات جديد (اختيار "Python 3" من قسم الندوة) وتشغيل الكود التالي في الخلية.

```python
%matplotlib inlin

استيراد pandas

بيانات = pandas.read_csv("gapminder.csv", index_col="country")

سنوات = البيانات. olumns.str.strip("gdpPercap_") # استخراج السنة من آخر 4 أحرف من كل عمود
data.columns = سنوات. stype(int) # تحويل قيم السنة إلى عدد صحيح، حفظ النتائج مرة أخرى إلى بيانات البيانات

() [أستراليا]. lot()
```

```{note}
راجع هذا [درس برنامج النجار](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) لمزيد من المعلومات.
```
````

````{tabbed} Julia
1) انتقل إلى مستودع GitHub الخاص بك وقم بإنشاء ملف يسمى `postBuild`
2) في `postBuild`، أضف سطراً واحداً يقرأ: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` هو برنامج يسترجع المحتوى من خوادم الويب.
     هذا الخط يستخرج المحتوى من عنوان URL المرير و يحفظه إلى اسم الملف المشار إليه بعلم `O` (عاصمة "O", لا صفر)، في هذه الحالة `فجوة في الدين. Sv`.
     العلم `q` يخبر `wget` أن يفعل ذلك بهدوء، مما يعني أنه لن يطبع أي شيء لوحدة التحكم.
3) Update your `Project.toml` file by adding new dependencies to `[deps]` with the following lines:

   ```julia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plots = "91a5bcdd-55d7-5caf-9e0b-520d859cae80"
   ```

   - These packages aren't necessary to download the data but we will use them to read the CSV file and make a plot
4) Click the binder badge in your README to launch your Binder

Once the Binder has launched, you should see a new file has appeared that was not part of your repo when you clicked the badge.

الآن تصور البيانات عن طريق إنشاء دفتر ملاحظات جديد (اختيار "جوليا" من قسم كتاب الملاحظات) وتشغيل الكود التالي في خلية.

```julia
باستخدام DataFrames
باستخدام CSV
باستخدام Plots

بيانات = CSV.read("gapminder). sv", DataFrame)

# استخراج الصف المقابل لأستراليا
aus_gdp = data[:, :country]. = "أستراليا"، :]
aus_gdp = Matrix(aus_gdp[:، :end])[:] # كناقل

# استخرج السنوات كمعلومات من أسماء الأعمدة
سنوات = [x[end 3:end] لـ x in names(data)[2:end]]
سنوات = parse. تعرف, سنوات)

# الأرض
plot(سنوات, aus_gdp)
```
````

````{tabbed} R
1) انتقل إلى مستودع GitHub الخاص بك وقم بإنشاء ملف يسمى `postBuild`
2) في `postBuild`، أضف سطراً واحداً يقرأ: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` هو برنامج يسترجع المحتوى من خوادم الويب.
     هذا الخط يستخرج المحتوى من عنوان URL المرير و يحفظه إلى اسم الملف المشار إليه بعلم `O` (عاصمة "O", لا صفر)، في هذه الحالة `فجوة في الدين. Sv`.
     العلم `q` يخبر `wget` أن يفعل ذلك بهدوء، مما يعني أنه لن يطبع أي شيء لوحدة التحكم.
3) قم بتحديث ملف `install.R` لتثبيت تبعيتين إضافيتين، `"tidyr"` و`ggplot2"`. للقيام بذلك، قم بتزويد ناقل حرف الحزم المطلوبة إلى 'install.packages()' بدلا من سلسلة حرف واحدة. يجب أن يبدو أمر التثبيت مثل هذا:

   ```r
   تثبيت. (”قراء“، ”tidyr“، "ggplot2"))
   ```

    - هذه الحزم ليست ضرورية لتحميل البيانات ولكن سوف نستخدمها لقراءة ملف CSV، قم بمعالجته وقم بصنع حزمة سكنية
انقر فوق شارة الزورق في README الخاص بك لتشغيل الزورق الخاص بك

بمجرد بدء تشغيل الزورق ، يجب أن ترى ملف جديد ظهر لم يكن جزءا من المستودع الخاص بك عند النقر على الشارة.

الآن تصور البيانات عن طريق إنشاء دفتر ملاحظات جديد (اختيار "R" من قسم كتاب الملاحظات) وتشغيل الكود التالي في خلية.

```r
library(readr)
library(tidyr)
library(ggplot2)

بيانات <- read_csv("gapminder. sv") %>%
    pivot_aus(-country)،
                 names_to = "year",
                 القيم - إلى = "gdpPercap"،
                 names_prefix = "gdpPercap_",
                 names_transform = list(سنة = as). nteger))

البيانات [البيانات$country == ”أستراليا“، ] ٪>٪
    ggplot(aes(x = سنة، y = gdpPercap)) +
    geom_line()
```
````
(z2b-beyond-notebooks)=
## تغيير الواجهة
خلال هذا البرنامج التعليمي، كنا نستخدم واجهة JupyterLab هذه هي الواجهة الافتراضية لأنواع بيندر المنشأة حديثا. غير أن هذه ليست الواجهة البينية الوحيدة المتاحة على mybinder.org، كما أن نظرة دفتر الملاحظات الكلاسيكية والرديو متاحان أيضاً. (يحتاج الأمر إلى تركيب بيئة RT لتوفر RStudio).
يمكنك الوصول إلى واجهات مختلفة بطرق مختلفة. أسهل طريقة هي استخدام الأزرار في JupyterLab Launcher، ولكن يمكنك توفير معلمات URL لفتح واجهة محددة مباشرة (أو ملف! عندما يطلق نموذج بيندر. سنقوم الآن بتغطية ثلاث طرق يمكنك التلاعب بعنوان Binder الخاص بك للتنقل بين الواجهة.
### من داخل بايندر قيد التشغيل
إليك بنية عنوان URL داخل نموذج تشغيل Binder تشغيل JupyterLab:
> **https://<some-prefix>.mybinder.org/user/<a composite of your username, repo name and a hash>/lab**
You can change the interface from JupyterLab to either the Classic Notebook or RStudio by changing the `/lab` part of the URL to:
- **Classic Notebook:** `/tree`
- **RStudio:** `/rstudio`
### by changing the mybinder.org launch link
Here is the launch link you have been using throughout this tutorial:
> **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD**
You can access each interface by appending once of the following to the end of you URL:
- **Jupyter Notebook:** `?urlpath=tree`
- **JupyterLab:** `?urlpath=lab`
- **RStudio:** `?urlpath=rstudio`
### by using the mybinder.org form
You can also set the interface when constructing your launch link on the mybinder.org website (instead of editing the URL directly) as demonstrated in the below gif.

```{figure} https://user-images.githubusercontent.com/1448859/53651127-4dabe900-3c46-11e9-8684-2cfde840d4ce.gif
---
name: changing_interfaces
alt: A gif demonstrating how to change the interface of a Binder on the mybinder.org website
---
Use the "URL to open" option on the mybinder.org site to select your interface
```

(z2b-over-to-you)=
## Now over to you!

Now you've binderized (bound?) this demo repo, it's time to binderize the example script and data you brought along!

**Some useful links:**

- Choosing languages:
  - **<https://mybinder.readthedocs.io/en/latest/howto/languages.html>**
- Configuration files:
  - **<https://mybinder.readthedocs.io/en/latest/using/config_files.html>**
- Example Binder repos:
  - **<https://mybinder.readthedocs.io/en/latest/sample_repos.html>**
- Getting data:
  - With `wget`: **<https://github.com/binder-examples/getting-data>**
  - With `quilt`: **<https://github.com/binder-examples/data-quilt>**
  - From remote storage: **<https://github.com/binder-examples/remote_storage>**

**Advanced usage patterns:**

- Separating content from envorinment with `nbgitpuller` to reduced rebuilds:
  - **<https://discourse.jupyter.org/t/tip-speed-up-binder-launches-by-pulling-github-content-in-a-binder-link-with-nbgitpuller/922>**
- Tips for reducing the start-up time of your repository:
  - **<https://discourse.jupyter.org/t/how-to-reduce-mybinder-org-repository-startup-time/4956>**