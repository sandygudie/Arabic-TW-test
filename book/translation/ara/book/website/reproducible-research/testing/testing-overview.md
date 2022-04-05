(rr-testing-overview)=
# Overview of Testing Types

There are a number of different kinds of tests, which will be discussed here.

Firstly there are positive tests and negative tests. Positive tests check that something works, for example testing that a function that multiplies some numbers together outputs the correct answer. Negative tests check that something generates an error when it should. For example nothing can go quicker than the speed of light, so a plasma physics simulation code may contain a test that an error is outputted if there are any particles faster than this, as it indicates there is a deeper problem in the code.

In addition to these two kinds of tests, there are also different levels of tests which test different aspects of a project. These levels are outlined below and both positive and negative tests can be present at any of these levels. A thorough test suite will contain tests at all of these levels (though some levels will need very few).

(r-test-Types) =
## Types of Testing

[اختبار الدخان](#Smoke_testing): فحوصات أولية موجزة جدا تضمن المتطلبات الأساسية المطلوبة لتشغيل المشروع قيد التشغيل. If these fail there is no point proceeding to additional levels of testing until they are fixed.

[اختبار الوحدة](#Unit_tests): مستوى عملية اختبار البرمجيات حيث يتم اختبار وحدات فردية من البرمجيات. The purpose is to validate that each unit of the software performs as designed.

[اختبار التكامل](#Integration_testing): مستوى اختبار البرامج حيث يتم دمج الوحدات الفردية واختبارها كمجموعة. The purpose of this level of testing is to expose faults in the interaction between integrated units.

[اختبار النظام](#System_tests): مستوى عملية اختبار البرمجيات حيث يتم اختبار نظام كامل ومتكامل. The purpose of this test is to evaluate whether the system as a whole gives the correct outputs for given inputs.

[اختبار القبول](#Acceptance_testing): مستوى عملية اختبار البرمجيات حيث يتم اختبار نظام للتحقق من مقبوليته. The purpose of this test is to evaluate the system's compliance with the project requirements and assess whether it is acceptable for the purpose.

هنا تشبيه: خلال عملية تصنيع قلم نقطة الكرة، الحد الأقصى، الجسم، يتم إنتاج الذيل وخرطوشة الحبر ونقطة الكرة بشكل منفصل ويتم اختبار الوحدة بشكل منفصل. عندما تكون وحدتان أو أكثر جاهزتين، يتم تجميعها وإجراء اختبار التكامل، على سبيل المثال، اختبار للتحقق من السقف المناسب على الجسم. عند تكامل القلم الكامل، يتم إجراء اختبار النظام للتحقق من أنه يمكن استخدامه لكتابة مثل أي قلم. اختبار القبول يمكن أن يكون شيئاً للتأكد من أن القلم هو اللون الذي يأمره العميل.

وهناك أيضا نوع آخر من الاختبارات يسمى اختبار التراجع. واختبار الانحراف هو نوع من الاختبارات التي يمكن إجراؤها على أي من المستويات الأربعة الرئيسية ويقارن نتائج الاختبارات قبل وبعد إجراء تغيير في الشفرة، ويعطي خطأ إذا كانت هذه مختلفة.

وتناقش هذه الأنواع المختلفة من الاختبارات بمزيد من التفصيل في الفصول الفرعية التالية.
