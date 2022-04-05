(rr-overview-definitions)=
# Definitions

The most common definition of reproducibility (and replication) was first noted by Claerbout and Karrenbach in 1992 {cite:ps}`ClaerboutKarrenbach1992Reproducibility` and has been used in computational science literature since then. تم إدخال تعريف شعبي آخر في عام 2013 من قبل رابطة الآلات الحاسوبية {cite:ps}`Ivie2018SciComp`، الذي قام بتبديل معنى مصطلحي 'قابل للتكرار`و 'قابل للتكرار` بالمقارنة مع كلاربوت وكارينباخ.

The following table contrasts both definitions {cite:ps}`Heroux2018Reproducibility`.

| Term         | Claerbout & Karrenbach                                                                                                                                    | ACM                                                                                                                                                                                                                                                                                                                                                                          |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reproducible | Authors provide all the necessary data and the computer codes to run the analysis again, re-creating the results.                                         | (Different team, different experimental setup.) (فريق مختلف، إعداد تجريبي مختلف) ويمكن الحصول على القياس بدقة محددة بواسطة فريق مختلف، ونظام قياس مختلف، في موقع مختلف في تجارب متعددة. For computational experiments, this means that an independent group can obtain the same result using artifacts which they develop completely independently.                          |
| Replicable   | A study that arrives at the same scientific findings as another study, collecting new data (possibly with different methods) and completing new analyses. | (Different team, same experimental setup.) (فريق مختلف، نفس الإعداد التجريبي) ويمكن أن يحصل فريق مختلف على القياس بدقة محددة باستخدام نفس إجراء القياس، نفس نظام القياس، في نفس ظروف التشغيل، في نفس الموقع أو في مكان مختلف في محاكمات متعددة. For computational experiments, this means that an independent group can obtain the same result using the author's artifacts. |

Barba (2018) {cite:ps}`Barba2018Reproducibility` conducted a detailed literature review on the usage of reproducible/replicable covering several disciplines. Most papers and disciplines use the terminology as defined by Claerbout and Karrenbach, whereas microbiology, immunology and computer science tend to follow the ACM use of reproducibility and replication. In political science and economics literature, both terms are used interchangeably.

In addition to these high level definitions of reproducibility, some authors provide more detailed distinctions. Victoria Stodden {cite:ps}`Victoria2014Reproducibility`, a prominent scholar on this topic, has for example identified the following further distinctions:

- _Computational reproducibility_: When detailed information is provided about code, software, hardware and implementation details.

- _Empirical reproducibility_: When detailed information is provided about non-computational empirical scientific experiments and observations. In practice, this is enabled by making the data and details of how it was collected freely available.

- _Statistical reproducibility_: When detailed information is provided, for example, about the choice of statistical tests, model parameters, and threshold values. This mostly relates to pre-registration of study design to prevent p-value hacking and other manipulations.

(rr-overview-definitions-reproducibility)=
## Table of Definitions for Reproducibility

At _The Turing Way_, we define **reproducible research** as work that can be independently recreated from the same data and the same code that the original team used. Reproducible is distinct from replicable, robust and generalisable as described in the figure below.


```{figure} ../../figures/reproducible-matrix.jpg
---
name: reproducible-matrix
alt: Kirstie's definition of reproducible research.
---
How the Turing Way defines reproducible research
```

The different dimensions of reproducible research described in the matrix above have the following definitions:

- **Reproducible:** A result is reproducible when the _same_ analysis steps performed on the _same_ dataset consistently produces the _same_ answer.
- **قابل للتكرار:** النتيجة قابلة للتكرار عندما ينتج _نفس_ تحليل __ مجموعة بيانات مختلفة إجابات متشابهة نوعيا.
- **روبست:** النتيجة قوية عندما يتم إخضاع _نفس_ مجموعة البيانات __ مختلفة من أعمال التحليل للإجابة على نفس سؤال البحث (على سبيل المثال خط أنابيب مكتوب في R وآخر مكتوب في بايتون) ويتم إنتاج إجابة مماثلة أو متماثلة نوعيا. Robust results show that the work is not dependent on the specificities of the programming language chosen to perform the analysis.
- **Generalisable:** Combining replicable and robust findings allow us to form generalisable results. Note that running an analysis on a different software implementation and with a different dataset does not provide _generalised_ results. There will be many more steps to know how well the work applies to all the different aspects of the research question. Generalisation is an important step towards understanding that the result is not dependent on a particular dataset nor a particular version of the analysis pipeline.

More information on these definitions can be found in "Reproducibility vs. Replicability: A Brief History of a Confused Terminology" by Hans E. Plesser {cite:ps}`Plesser2018Reproducibility`.

```{figure} ../../figures/reproducible-definition-grid.jpg
---
name: reproducible-definition-grid.jpg
alt: Grid with the characteristics of reproducible, replicable, robust and generalisable research
---
_The Turing Way_ project illustration by Scriberia. Used under a CC-BY 4.0 licence. DOI: [10.5281/zenodo.3332807](https://doi.org/10.5281/zenodo.3332807).
```

(rr-overview-reproducible)=
## Reproducible But Not Open

_The Turing Way_ recognises that some research will use sensitive data that cannot be shared and this handbook will provide guides on how your research can be reproducible without all parts necessarily being open.
