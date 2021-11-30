(r-test-systemtest)=
# اختبار النظام

وبمجرد إجراء اختبارات التكامل، يمكن أن يبدأ مستوى آخر من الاختبارات يسمى اختبار النظام. واختبار النظام هو مستوى من اختبار البرمجيات حيث يتم اختبار برمجيات كاملة ومتكاملة. يزود المختبر البرنامج بالمدخلات ويتحقق مما إذا كان ناتج البرنامج صحيحا. وإذا لم تكن هناك مشكلة في مكان ما في النظام. لاحظ أنه ليس من الضروري القيام بذلك يدوياً، بل يمكن أن يتم تلقائياً. والغرض من هذه الاختبارات هو تقييم مدى امتثال النظام للمتطلبات المحددة. ومن نواح عديدة، يشكل اختبار النظام امتداداً لاختبار الإدماج. وينصب تركيز اختبارات النظام على التأكد من أن مجموعات المكونات تعمل بشكل صحيح ككل متماسك.

غير أنه بدلا من التركيز على الوصلات البينية بين المكونات، تقيّم اختبارات النظام عادة قدرة برنامج حاسوبي كامل على العمل في الخارج. وتتجاهل هذه المجموعة من الاختبارات الأجزاء المكونة لها من أجل قياس البرمجيات المكونة ككيان موحد. وبسبب هذا التمييز، عادة ما تركز اختبارات النظام على النواتج المتاحة للمستخدم أو الخارجية.

كما يمكن لاختبار النظام أن يختبر ميزات النظام خلاف الصلاحية. ومن الأمثلة على ذلك:

- اختبار الأداء: هل يفي أداء البرنامج بالحد الأدنى من المتطلبات؟ وقد يقيس اختبار الأداء المدة التي يستغرقها تشغيل النظام في حالة معينة.
- اختبار الهجرة: هل ينجح البرنامج عند نقله إلى بيئة حسابية أخرى؟
- الإجهاد/اختبار الحجم/التحميل: اختبار كيفية تصرف البرنامج عندما يكون تحت الضغط، على سبيل المثال، عندما يكون مطلوبا لمعالجة كميات كبيرة جدا من البيانات.
- اختبار الاستخدام: مدى سهولة استخدام البرنامج (أكثر شيوعاً في البرمجيات التجارية، والاختبارات التي يجريها عادة البشر بدلاً من الاختبارات الآلية).
- اختبار الاسترداد: ما إذا كان البرنامج يمكن أن يستمر إذا وقعت أخطاء (ومرة أخرى، أكثر شيوعاً في البرمجيات التجارية).

## نصائح اختبار النظام

كما أن اختبارات النظام، التي تسمى أيضا الاختبارات من النهاية إلى النهاية، تقوم بتشغيل البرنامج، جيدا، من النهاية إلى النهاية. وعلى هذا النحو، فإن هذه الاختبارات هي أكثر الاختبارات استهلاكاً للوقت. لذلك يجب عليك تشغيل هذه الاختبارات فقط إذا كانت جميع الاختبارات ذات المستوى الأدنى (الدخان، الوحدة، التكامل) قد اجتازت بالفعل. إذا لم تكن لديهم، قم بإصلاح المشكلات التي اكتشفوها أولاً قبل إضاعة الوقت في تشغيل اختبارات النظام.

ونظراً لطابعها الذي يستغرق وقتاً طويلاً فإنه غالباً ما يكون من غير العملي أيضاً إجراء اختبارات نظام كافية لتتبع كل طريق ممكن من خلال برنامج، ولا سيما إذا كان هناك عدد كبير من البيانات المشروطة. لذلك يجب أن تنظر في حالات اختبار النظام التي تقوم بتشغيلها بعناية وأولوية:

- أكثر الطرق شيوعا من خلال البرنامج.
- أهم الطرق لبرنامج ما. فعلى سبيل المثال، يهدف جهاز الكشف عن الموجات الجاذبية إلى العثور على أحداث نادرة للغاية. إذا كان هناك خلل في ذلك المسار من خلال البرنامج الذي يراقب الكاشف فستكون مشكلة *كبيرة*
- الحالات التي تكون عرضة للكسر بسبب مشاكل هيكلية داخل البرنامج. على الرغم من أنه من الأفضل فقط حل تلك المشاكل، لكن الحالات موجودة حيث قد لا يكون هذا ممكنا.

وبما أن اختبارات النظام قد تستغرق وقتا طويلا، فقد يكون من غير العملي إجراء هذه الاختبارات بصورة منتظمة جدا (مثل عدة مرات في اليوم بعد تغييرات صغيرة في الشفرة). ولذلك يمكن أن تكون فكرة جيدة هي تشغيلها كل ليلة (والتشغيل الآلي لهذه العملية) بحيث يمكن الاطلاع عليها بسرعة نسبية إذا ما أُدخلت أخطاء مفادها أن اختبار النظام وحده هو الذي يمكن أن يكتشف المبرمج.