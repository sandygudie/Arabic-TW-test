(rr-vcs)=
# التحكم في الإصدار

(rr-vcs-prerequisites)=
## الشروط المسبقة

| الشروط المسبقة                                                                     | الأهمية | الحواشي |
| ---------------------------------------------------------------------------------- | ------- | ------- |
| [الخبرة في سطر الأوامر](https://programminghistorian.org/en/lessons/intro-to-bash) | مساعدة  |         |

**مستوى المهارة الموصى به**: _مبتدئ - متوسط_

(rr-vcs-summary)=
## Summary

وبغض النظر عن كيفية تنظيم مجموعتك، يتعين إدارة عمل العديد من المساهمين في مجموعة واحدة من وثائق العمل المشتركة. التحكم في الإصدار هو نهج لتسجيل التغييرات التي أجريت في ملف أو مجموعة من الملفات مع مرور الوقت حتى تتمكن أنت والمتعاونين معك من تتبع تاريخ هذه التغييرات، مراجعة أي تغييرات، والعودة أو العودة إلى الإصدارات السابقة. تسمى إدارة التغييرات أو التنقيحات على أي نوع من المعلومات التي تجرى في ملف أو مشروع ما بنسخة.

وفي هذا الفصل، نناقش أفضل الممارسات ذات الصلة بغض النظر عن الأدوات. ممارسات الإصدار تأتي أساسا من إدارة التغييرات في مستودعات الرموز. ومع ذلك، في الواقع، يمكنك استخدام التحكم في الإصدار لأي نوع من الملفات تقريبا على الكمبيوتر. على سبيل المثال، عند كتابة ورقة مع متعاونين متعددين، يمكن للتحكم في الإصدار أن يساعد في تتبع ما تغير، ومن قام بتغييرها، وما هي التحديثات التي تم القيام بها.

يمكن استخدام نظم تحكم إصدار مختلفة من خلال برنامج مع واجهة مستخدم رسمية، أو تطبيقات قائمة على متصفح الويب، أو أدوات سطر الأوامر. لقد رأينا جميعا نهج إصدار بسيط للملفات حيث يتم تخزين إصدارات مختلفة من الملف باسم مختلف. أدوات مثل Google Drive و Dropbox توفر منصات لتحديث الملفات ومشاركتها مع الآخرين في الوقت الحقيقي. يوجد نظام تحكم أكثر تطورا في الإصدار داخل أدوات مثل [مستندات جوجل](https://docs.google.com/) أو [HackMD](http://hackmd.io/). هذه تسمح للمتعاونين بتحديث الملفات أثناء تخزين كل إصدار في سجل الإصدارات الخاص بهم (سوف نناقش هذا بالتفصيل). توفر أنظمة تحكم النسخة المتقدمة (VCS) مثل [Git](https://en.wikipedia.org/wiki/Git)و [Mercurial](https://www.mercurial-scm.org/)و [SVN](https://subversion.apache.org/) أدوات أكثر قوة.

ويهدف هذا الفصل إلى تغطية المبادئ العامة التي تقوم عليها جميع نظم مراقبة النسخ المتقدمة وأفضل الممارسات التي تنطبق على جميع هذه النظم. نحن نناقش العديد من الأدوات والمميزات؛ ولكننا نشجع القراء على استخدام الميزات المفيدة لعملهم والأدوات المريحة لهم. وستوجه معظم التعليمات الواردة في هذا الفصل أيضاً نحو Git، وهو ما يشيع استخدامه من جانب الباحثين، و خدمة استضافة مستودع Git على الويب، [GitHub](https://github.com/)، التي تيسر التعاون عبر الإنترنت.

لاحقا في هذا الفصل، نناقش أيضا التحكم في الإصدار للبيانات، وهو يطبق لتتبع تنقيحات الكميات الكبيرة من البيانات، ولا سيما عند العمل بصورة تعاونية. من المفيد أن نعرف أن البيانات يمكن أن تكون متقلبة وأن تصديرها يمكن أن يحسن قابلية تحليلاتكم العلمية للتكرار.

```{figure}  ../figures/project-history.jpg
---
الاسم: تاريخ المشروع
البديل : التباين في إدارة سجل المشروع. على اليسار - الاختيار بين الملفات المسمّاة بشكل غامض. على اليمين - الاختيار بين الإصدارات المتتالية (من V1 إلى V6).
---
_طريق التوحيد_ التوضيحي لمشروع سكريبيريا. يستخدم بموجب ترخيص CC-BY 4.0. DOI: [10.5281/zenodo.3332807] (https://doi.org/10.5281/zenodo.3332807).
```

(rr-vcs-useful)=
## الدافع والخلفية

التحكم في الإصدار يساعدنا على فهم التغييرات التي قمنا بها في الماضي أو لماذا قمنا بتحليل محدد في الطريقة التي قمنا بها، حتى بعد أسابيع أو شهور. بمساعدة التعليقات والرسائل الملتزمة، يمكن لكل نسخة أن تشرح التغييرات التي تحتوي عليها مقارنة بالنسخ السابقة. هذا مفيد عندما نشارك تحليلنا (ليس فقط البيانات)، وجعله قابلا للتدقيق أو **قابل للتكرار** - وهو ممارسة علمية جيدة.

نظام التحكم في الإصدار يخزن بدقة تاريخ التغييرات ومن قام بإجرائها، لذلك بينما لا يزال من السهل الوصول إليها، دليل العمل الخاص بك ليس مستغلا بسبب حطام الإصدارات السابقة التي هي ضرورية للإبقاء على حالة محددة. وبالمثل، مع مراقبة النسخ، ليس هناك حاجة إلى ترك أجزاء من التعليمات البرمجية التي تم تعليقها إذا كنت بحاجة إلى العودة إلى الإصدار القديم مرة أخرى.


وأخيرا، فإن مراقبة الإصدار قيمة لا تقدر بثمن للمشاريع التعاونية حيث يعمل مختلف الناس على نفس المدونة في وقت واحد ويؤسسون على عمل بعضهم البعض. فهو يتيح تتبع التغييرات التي يجريها مختلف الناس ويمكن أن يجمع تلقائيا بين عمل الناس مع توفير قدر كبير من الجهود المضنية للقيام بذلك يدويا. استخدام التحكم في الإصدار لمشروعك البحثي يعني أن عملك شفاف تماما، ولأن جميع إجراءاتك مسجلة، فإنها تمكن الآخرين من إعادة إنتاج دراستك. وعلاوة على ذلك، توفر خدمات التحكم في الإصدار مثل {ref}`GitHub<cl-github-novice-motivation>` طريقة للاتصال والتعاون بطريقة أكثر تنظيما مثل في طلبات الجذب، ومراجعات الرموز، والمشكلات.