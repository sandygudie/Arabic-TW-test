# Checklist for Code Testing

This checklist contains a lot of items. كما ذكر {ref}`قبل<rr-testing-write-tests>`، من الأفضل بكثير القيام ببعض العناصر من لا شيء منها. Do not be discouraged if this list of tasks seems insurmountable.

<a name="Writing_tests"></a>

## Writing tests

- Write a few smoke tests.
- Write unit tests for all your code units.
- Write integration tests to check the integration between units.
- Write a few system tests. Prioritise common and important paths through the program.
- Write regression tests. Regression tests can exist at any level of testing.
- If appropriate for your project write acceptance tests.
- Add runtime tests into your project.

<a name="Good_practice_checks"></a>

## Good practice checks

- [ ] توثيق الاختبارات وكيفية إجرائها.
  - [ ] كتابة النصوص البرمجية لإعداد وتكوين أي موارد مطلوبة لتشغيل الاختبارات.
- [ ] اختيار إطار الاختبار والاستفادة منه.
- [ ] إجراء الاختبارات بانتظام.
  - [ ] أتمتة عملية إجراء الاختبارات. النظر في الاستفادة من التكامل المستمر (انظر الفصل الخاص بالتكامل المستمر) للقيام بذلك.
- [ ] تحقق من التغطية البرمجية للاختبارات الخاصة بك وحاول تحسينها.
- [ ] المشاركة في استعراض الرموز مع شريك.
