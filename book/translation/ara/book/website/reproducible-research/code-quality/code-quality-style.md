(نمط r-code) =
# Code Style and Formatting

نمط البرمجة هو مجموعة من الاتفاقيات حول كيفية تنسيق البرمجة. على سبيل المثال، ما الذي تسميه المتغيرات الخاصة بك؟ هل تستخدم المسافات أو علامات التبويب للإضافة؟ أين تضع تعليقات؟ استخدام نفس النمط بشكل متسق في كل الكود يجعل قراءتك أسهل. الكود الذي يسهل قراءته هو أسهل فهمه من جانبك ومن جانب المتعاونين المحتملين. ولذلك، فإن الانضمام إلى أسلوب الترميز يقلل من خطر الأخطاء وييسر العمل معا على البرمجيات. [لماذا البرمجة على نمط الأمور](http://coding.smashingmagazine.com/2012/10/25/why-coding-style-matters/) هي مقالة لطيفة عن سبب أهمية أنماط البرمجة وكيف أنها تزيد من جودة البرنامج.

على سبيل المثال [PEP8](https://www.python.org/dev/peps/pep-0008/) هو أكثر أنماط برمجة بايثون استخداما و [ECMAScript 6](http://es6-features.org/) على سبيل المثال [ES6](http://es6-features.org/) هو مواصفات لغة الكتابة الموحدة بواسطة ECMA International للبرمجة في جافاسكريبت.

للحصول على أدلة النمط الشائع الاستخدام لمختلف لغات البرمجة راجع [أدلة اللغة](https://guide.esciencecenter.nl/best_practices/language_guides/languages_overview.html). لدى جوجل أيضا دليل نمط [](https://code.google.com/p/google-styleguide/) للعديد من اللغات المستخدمة في مشاريع مفتوحة المصدر منشأ من جوجل.

(r-code-style-and format-formatting)=
## Automatic formatting

يوجد العديد من الأدوات لتنسيق التعليمات البرمجية تلقائياً بحيث تتبع أسلوباً معيناً. يتيح التنسيق التلقائي جودة أكبر، خاصة عندما تتعاون مع فريق والناس الآخرين بحاجة إلى النظر إلى التعليمات البرمجية التي كتبتها. العديد من المطورين والمنظمات يحافظون على معايير تنسيق التعليمات البرمجية مثل **2 مسافة** أو **4 مسافة داخلية**. استخدام هذه يوصى به بشدة لأن احتمال العثور على الأخطاء (إن وجدت) يزيد عدة أضعاف.

[EditorConfig](https://editorconfig.org) هي أداة مستقلة لغة تساعد على الحفاظ على أنماط المساحة البيضاء المتسقة لأشخاص متعددين يعملون على نفس المشروع عبر محررين مختلفين. يدعم معظم المحررين تحرير الإعدادات إما محلياً أو من خلال إضافة. تقريبا جميع محرري الـ IDEs والنصوص المستخدمين على نطاق واسع يدعم التنسيق التلقائي عند الكتابة. على سبيل المثال: [مجموعة JetBrains IDE](https://www.jetbrains.com/products.html#)، [VSCode](https://code.visualstudio.com/) و [Atom](https://atom.io/).

بالإضافة إلى ذلك، هناك العديد من الأدوات الخاصة بلغة معينة لتنسيق التعليمات البرمجية تلقائياً وفقاً لنمط معين. لاحظ أن المحررين كثيرا ما يؤيدون استخدام هذه الأدوات مباشرة من بيئة التحرير.

| Language   | Formatter Tool                                                                                              |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| C/C++      | [GNUIndent](http://www.gnu.org/software/indent/), [GreatCode](http://sourceforge.net/projects/gcgreatcode/) |
| Python     | [Black](https://black.readthedocs.io), [yapf](https://pypi.org/project/yapf/)                               |
| Javascript | [beautifier.io](https://beautifier.io/)                                                                     |
| Java       | [Google Java format](https://github.com/google/google-java-format), [JIndent](http://www.jindent.com/)      |
| PHP        | [phpStylist](http://sourceforge.net/projects/phpstylist/)                                                   |
| Perl       | [PerlTidy](http://perltidy.sourceforge.net/)                                                                |
| Shell/Bash | [ShellIndent](http://www.bolthole.com/AWK.html)                                                             |
| CSS        | [CSSTidy](http://csstidy.sourceforge.net/)                                                                  |
| HTML       | [Tidy](http://tidy.sourceforge.net/)                                                                        |

**نصيحة سريعة**: إذا كنت تستخدم رمز VS كمحرر نصي رئيسي ، يمكنك تمكين تنسيق التعليمات البرمجية التلقائية إلى المتصفح الخاص بك. فتح صفحة التفضيلات الخاصة بك في وضع JSON وإضافة السطر التالي:

```
"editor.formatOnSave": true,
```

(r-code-style-service)=
## Online services providing software quality checks

هناك العديد من خدمات الويب التي تقوم بتحليل التعليمات البرمجية وجعل جودة التعليمات البرمجية مرئية. عادة ما تقوم هذه الخدمات بتشغيل أداة أو أكثر من أدوات تحليل التعليمات البرمجية الثابتة التي يمكن استخدامها أيضًا من سطر الأوامر أو مدمجة في محررك على جهاز الكمبيوتر الخاص بك. يوصى بشدة باستخدام خدمة جودة التعليمات البرمجية التي تتكامل مع مستودع GitHub/GitLab ، حيث يمكنها الكشف عن مشاكل الجودة في طلبات السحب والإبلاغ عنها.

خدمات تحليل جودة البرمجة هي مواقع الويب التي غالباً ما توفر الميزات التالية:

- Automatically analyse your code after pushing it to GitHub/GitLab
- Usually free for open source projects
- Support multiple programming languages, but not every language will have the same level of features
- Grade or score for the quality of all of the code in the repository
- List of issues with the code, grouped by severity
- Drill down to location of issue
- Default list of checks which the service provider finds the best practice
- Can be configured to make the list of checks more strict or relaxed
- Can be configured to ignore files or extensions
- Can read a configuration file from repository
- Track issues over time and send alerts when quality deteriorates
- Optionally reports on code coverage generated by a CI build
- Automatically deploy the repository and generates a preview build for review before final release.

للحصول على قائمة من الخيارات أنظر [Shields.io](https://shields.io/category/analysis) أو [قائمة الخدمات المجانية للمشاريع مفتوحة المصدر](https://github.com/ripienaar/free-for-dev#code-quality).
