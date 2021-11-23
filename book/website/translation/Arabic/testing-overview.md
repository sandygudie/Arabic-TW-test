(r-test-Overview)=
# لمحة عامة عن أنواع الاختبار

وهناك عدد من أنواع الاختبارات المختلفة التي ستناقش هنا.

أولاً، هناك اختبارات إيجابية واختبارات سلبية. الاختبارات الإيجابية تتحقق من أن شيئاً ما يعمل، على سبيل المثال اختبار أن الدالة التي تضرب بعض الأرقام معاً تأتي بالإجابة الصحيحة. الاختبارات السلبية تتحقق من أن شيئاً ما يولد خطأ عندما ينبغي أن يفعل ذلك. فعلى سبيل المثال، لا شيء يمكن أن يذهب أسرع من سرعة الضوء، لذلك قد يحتوي رمز محاكاة فيزياء البلازما على اختبار بأن هناك خطأ في الإخراج إذا كانت هناك أي جسيمات أسرع من ذلك، كما يشير إلى أن هناك مشكلة أعمق في الشفرة.

وبالإضافة إلى هذين النوعين من الاختبارات، هناك أيضا مستويات مختلفة من الاختبارات التي تختبر جوانب مختلفة من المشروع. ويرد أدناه موجز لهذه المستويات ويمكن إجراء اختبارات إيجابية وسلبية على أي من هذه المستويات. وستتضمن مجموعة اختبار شاملة اختبارات على جميع هذه المستويات (وإن كانت بعض المستويات لا تحتاج إلا إلى القليل جداً).

(rr-testing-types-of-testing)=
## أنواع الاختبار

[Smoke testing](#Smoke_testing): Very brief initial checks that ensures the basic requirements required to run the project hold. If these fail there is no point proceeding to additional levels of testing until they are fixed.

[Unit testing](#Unit_tests):    A level of the software testing process where individual units of a software are tested. The purpose is to validate that each unit of the software performs as designed.

[Integration testing](#Integration_testing): A level of software testing where individual units are combined and tested as a group. The purpose of this level of testing is to expose faults in the interaction between integrated units.

[System testing](#System_tests):    A level of the software testing process where a complete, integrated system is tested. The purpose of this test is to evaluate whether the system as a whole gives the correct outputs for given inputs.

[Acceptance testing](#Acceptance_testing):  A level of the software testing process where a system is tested for acceptability. The purpose of this test is to evaluate the system's compliance with the project requirements and assess whether it is acceptable for the purpose.

Here's an analogy: during the process of manufacturing a ballpoint pen, the cap, the body, the tail, the ink cartridge and the ballpoint are produced separately and unit tested separately. When two or more units are ready, they are assembled and integration testing is performed, for example a test to check the cap fits on the body. When the complete pen is integrated, system testing is performed to check it can be used to write like any pen should. Acceptance testing could be a check to ensure the pen is the colour the customer ordered.

There is also another kind of testing called regression testing. Regression testing is a type of testing that can be performed at any of the four main levels and compares the results of tests before and after a change is made to the code, and gives an error if these are different.

These different types of tests are discussed in more detail in the next subchapters.
