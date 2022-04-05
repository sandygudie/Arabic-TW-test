(rr-make)=
# Reproducibility with Make

(rr-make-prerequisites)=
## Prerequisites

| Prerequisite                                                                                  | Importance | Notes                                                        |
| --------------------------------------------------------------------------------------------- | ---------- | ------------------------------------------------------------ |
| [Experience with the command line](https://programminghistorian.org/en/lessons/intro-to-bash) | Necessary  |                                                              |
| {ref}`Version Control<rr-vcs>`                                                          | Helpful    | Experience using git is useful to follow along with examples |

Recommended skill level: intermediate

(rr-make-summary)=
## Summary

يمكن النظر إلى مشروع علم البيانات أو البحث على أنه شجرة من التبعيات: يعتمد تقرير على الأرقام والجداول، وتتوقف هذه بدورها على البيانات والنصوص المستخدمة في التحليل لمعالجة هذه البيانات (الموضحة في الشكل أدناه).  اصنع أداة لإنشاء ملفات إخراج من تبعيهم من خلال قواعد محددة مسبقا.  من الممكن الجمع بين هاتين الفكرتين لإنشاء مشروع قابل للتكرار مع مايك.  في هذا الفصل نقدم مقدمة لصنع وتقديم دروس حول كيفية استخدام إعداد البيانات لخط أنابيب التحليل.  ونصف أيضًا مشروع بحث في العالم الحقيقي الذي يستخدم جعل للانتقال من بيانات الإدخال الخام إلى التجارب كلها في الطريق إلى ملف pdf للورقة!

```{figure} ../figures/make-research-dag.png
---
name: make-research-dag
alt: Schematic of a research project.
---
Schematic of a research project.
```

(rr-make-intro)=
## An Introduction to Make

Make is a build automation tool. يستخدم ملف تكوين يسمى Makefile الذي يحتوي على *قواعد* لما يجب بناؤه. اصنع *أهدافا* باستخدام *وصفات*.  Targets can optionally have *prerequisites*.  المتطلبات الأساسية يمكن أن تكون ملفات على جهاز الكمبيوتر الخاص بك أو أهداف أخرى. قم بتحديد ما تريد بناء بناء على شجرة التبعية للأهداف والمتطلبات الأساسية (تقنياً، هذا هو {ref}`rr-make-resources-tool`). يستخدم *وقت التعديل* لـ المتطلبات المسبقة لتحديث الأهداف فقط عند الحاجة.

(rr-make-why)=
### Why use Make for Reproducibility?

There are several reasons why Make is a good tool to use for reproducibility:

1. Make is easy to learn
1. Make is available on many platforms
1. Make is flexible
1. Many people are already familiar with Make
1. Makefiles يقلل من الحمل المعرفي لأنه طالما أن الأهداف المشتركة لجعل `كلها` و `نظيفة` موجودة (الموضحة أدناه)، يمكنك أن تكون في الأعلى و تعمل دون الحاجة إلى قراءة تعليمات طويلة. هذا بشكل خاص مفيد عندما تعمل على مشروع شخص آخر أو على مشروع لم تستخدمه منذ وقت طويل.
1. Makefiles are human-readable and machine-readable text files. لذا بدلاً من كتابة تعليمات إلى إنسان لكيفية بناء تقرير أو إخراج، يمكنك توفير Makefile مع تعليمات يمكن قراءتها بواسطة شخص *و* ينفذها جهاز كمبيوتر.
1. Because Makefiles are text files they are easy to share and keep in version control.
1. Using Make doesn't exclude using other tools such as Travis and Docker.

مع Makefile، يمكنك مشاركة تحليل كامل (الكود والبيانات و سير العمل الحاسوبي) و السماح للمتعاونين أو قراء ورقتك بإعادة حساب النتائج الخاصة بك. باستخدام أدوات مثل LaTeX، يمكنك حتى إنشاء مخطوطة كاملة تحتوي على أرقام ونتائج محسوبة حديثاً! هذا يمكن أن يزيد الثقة في ناتج البحث الذي تولده، يمكنه أن يجعل بحثك أكثر سهولة ، ويمكنه أن يجعل التعاون أسهل. This chapter can show you how to get started.
