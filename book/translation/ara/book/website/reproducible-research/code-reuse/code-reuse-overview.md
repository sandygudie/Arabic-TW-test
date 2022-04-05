(r-code-reuse-recommendations)=
# نظرة عامة على إعادة استخدام الكود

This section contains a checklist of recommendations for making your software more reusable. يحتوي قسم {ref}`rr-code reuse-detail` على شرح أكثر تعمقا لكل توصية من هذه التوصيات. You can follow the recommendations that are more suitable for your type of software and skip the ones which are not relevant in your case.

## التوصيات المتكررة

1. تأكد من أنك تستطيع العثور عليه (في الفضاء؛ معني: أن تكون قادراً على تحديد موقع المستودع/المشروع)
1. تأكد من أنك تستطيع العثور عليها (في الوقت؛ المعنى: أن تكون قادراً على تحديد موقع إصدار معين)
1. Make sure you can execute the same sequence of operations
1. Make sure your environment and sequence of operations is robust and no human is needed to replicate what was done
1. License your code
    - with a license that allows for reuse;
    - with a license compatible with the dependencies’ licenses
1. Make sure it is citable
1. Include necessary data
1. Write useful documentation*

## توصيات قابلة لإعادة التشغيل

1. إزالة الأجزاء المقوى (مثل المسارات التي كانت موجودة فقط على القرص الصلب حيث تم تشغيل خط الأنابيب) وجعل الوحدة النمطية
1. Test that the modules you made can take different types of input data or parameters
1. Turn the modules into a package/toolbox
1. Write useful documentation*

## التوصيات المحمولة
1. Make sure you can recreate the environment where it lived
1. Write useful documentation*

## التوصيات الموسعة
1. Write useful documentation*

## توصيات قابلة للتعديل
1. Make sure your code is readable by humans
1. Make sure comments are present
1. Write useful documentation*

The observant reader might will notice that `Write useful documentation` is mentioned for every level of reuse. This is because different levels of documentation are required for different levels of reuse.

## Documentation

*Different documentation requirements for different levels of reuse*

Writing useful documentation is an important requirement for all levels of reuse. However, for the different levels of reuse, there are different documentation requirements:

The documentation:
- explains usage, specifying:
  - what the software does; (required for repeatable)
  - how it can be used; (required for repeatable)
  - what options/parameters are available. (required for repeatable)
- contains examples of how to run it. (required for repeatable)
- has installation instructions, including good descriptions of:
  - the hardware it depends on (for example GPUs); (required for portable)
  - the operating system the software has been tested on; (required for portable)
  - software requirements (such as libraries and shell settings). (required for portable)
