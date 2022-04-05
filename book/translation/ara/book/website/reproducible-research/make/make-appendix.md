(rr-make-appendix)=
# Appendix

(rr-make-appendix-dag)=
## Directed Acyclic Graph

A Directed Acyclic Graph (DAG) is a *graph* of nodes and edges that is:

1. *الموجه*: الحواف لها اتجاه ويمكنك فقط المشي على الرسم البياني في ذلك الاتجاه
2. *acyclic*: does not contain cycles: A can't depend on B when B depends on A.

The latter property is of course quite handy for a build system. يمكن العثور على المزيد من المعلومات حول DAGs على [ويكيبيديا](https://en.wikipedia.org/wiki/Directed_acyclic_graph).

(rr-make-appendix-installing)=
## Installing Make

First, check if you have GNU Make installed already. In a terminal type:

```bash
$ make
```

If you get `make: command not found` (or similar), you don't have Make. إذا حصلت على `صنع: *** لا توجد أهداف محددة ولم يتم العثور على مكان مؤقت.  توقف.` أنت لديها صنع.

We'll be using **GNU Make** in this tutorial. تحقق من أن هذا ما لديك عن طريق الكتابة:

```bash
$ make --version
```

إذا لم يكن لديك غنو صنع ولكن لديك إصدار BSD ، قد لا تعمل بعض الأشياء كما هو متوقع ونوصي بتثبيت GNU Make.

To install GNU Make, please follow these instructions:

- **Linux**: Use your package manager to install Make. على سبيل المثال على Arch Linux:

  ```bash
  $ sudo pacman -S make
  ```

  Ubuntu:
  ```bash
  $ sudo apt-get install build-essential
  ```

- **MacOS**: If you have [Homebrew](https://brew.sh/) installed, it's simply:

  ```bash
  $ brew install make
  ```

  إذا كان لديك تنفيذ مدمج، فيرجى التأكد من أنها تصنع جنو عن طريق التحقق من `اجعل --الإصدار`.

(rr-make-appendix-advancedgr)=
## Advanced: Generating Rules using Call

*يواصل هذا القسم البرنامج التعليمي أعلاه ويعرض ميزة صنع للإنشاء التلقائي للقواعد.*

في خط أنابيب علوم البيانات، قد يكون من الشائع تطبيق برامج نصية متعددة على نفس البيانات (على سبيل المثال عندما تقارن الأساليب أو تختبر معلمات مختلفة). في هذه الحالة، قد يصبح من الممل كتابة قاعدة منفصلة لكل نص نصي عندما يتغير اسم البرنامج النصي فقط. لتبسيط هذه العملية ، يمكننا أن نجعل توسيع ما يسمى [*المعلبة* وصفة](https://www.gnu.org/software/make/manual/make.html#Canned-Recipes).

To follow along, switch to the `canned` branch:

```bash
$ make clean
$ git stash --all        # note the '--all' flag so we also stash the Makefile
$ git checkout canned
```

على هذا الفرع ستلاحظ أن هناك برنامج نصي جديد في **البرامج النصية** الدليل المسمى `generate_qplot.py`. يعمل هذا البرنامج النصي بشكل مماثل لـ `Generate_histogram. y` سكريبت (يحتوي على نفس بناء سطر الأوامر)، ولكن يولد [Q-plot](https://en.wikipedia.org/wiki/Q%E2%80%93Q_plot). ملف **report.tex** تم تحديثه أيضا لدمج هذه المخططات.

بعد التبديل إلى فرع `المعلب` سيكون هناك Makefile في مستودع الذي يحتوي على قاعدة منفصلة لإنشاء قطع QQ. هذا Makefile يبدو هكذا:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst data/%.csv,output/figure_%.png,$(DATA))
QQPLOTS = $(patsubst data/%.csv,output/qqplot_%.png,$(DATA))

.PHONY: all clean

all: output/report.pdf

$(HISTOGRAMS): output/histogram_%.png: data/%.csv scripts/generate_histogram.py
    python scripts/generate_histogram.py -i $< -o $@

$(QQPLOTS): output/qqplot_%.png: data/%.csv scripts/generate_qqplot.py
    python scripts/generate_qqplot.py -i $< -o $@

output/report.pdf: report/report.tex $(FIGURES)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

You'll notice that the rules for histograms and QQ-plots are very similar.

مع تزايد عدد البرامج النصية التي تريد تشغيلها على بياناتك، قد يؤدي هذا إلى عدد كبير من القواعد في ماكيفيلي التي تكاد تكون واحدة بالضبط. يمكننا تبسيط هذا عن طريق إنشاء [*وصفة معلبة *](https://www.gnu.org/software/make/manual/html_node/Canned-Recipes.html) تأخذ كلا من اسم البرنامج النصي واسم النوع كمدخلات:

```makefile
define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef
```

لاحظ أننا في هذه الوصفة نستخدم `$(1)` لأي من `الرسم البياني` أو `القطع` و `$(2)` للنوع الصحيح. تتطابق هذه مع حجج الدالة المتوقعة مع `وصفة البرنامج النصي على البيانات` المعلّبة. لاحظ أيضا أننا نستخدم $ `$<` و `$@` في الوصفة الفعلية، مع اثنين `$` رموز للهروب. لإنشاء جميع الأهداف، نحن بحاجة إلى سطر يستدعي هذه الوصفة المعلبة.  في حالتنا، نحن نستخدم حلقة التكرار المزدوجة حول الأنواع و البرامج النصية:

```makefile
$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre))) \
    ) \
)
```

In these lines the `\` character is used for continuing long lines.

The full Makefile then becomes:

```makefile
# Makefile for analysis report
#

ALL_CSV = $(wildcard data/*.csv)
DATA = $(filter-out $(wildcard data/input_file_*.csv),$(ALL_CSV))
HISTOGRAMS = $(patsubst %,output/histogram_%.png,$(GENRES))
QQPLOTS = $(patsubst %,output/qqplot_%.png,$(GENRES))

GENRES = $(patsubst data/%.csv,%,$(DATA))
SCRIPTS = histogram qqplot

.PHONY: all clean

all: output/report.pdf

define run-script-on-data
output/$(1)_$(2).png: data/$(2).csv scripts/generate_$(1).py
    python scripts/generate_$(1).py -i $$< -o $$@
endef

$(foreach genre,$(GENRES),\
    $(foreach script,$(SCRIPTS),\
        $(eval $(call run-script-on-data,$(script),$(genre)))\
    )\
)

output/report.pdf: report/report.tex $(HISTOGRAMS) $(QQPLOTS)
    cd report/ && pdflatex report.tex && mv report.pdf ../$@

clean:
    rm -f output/report.pdf
    rm -f $(HISTOGRAMS) $(QQPLOTS)
```

لاحظ أننا أضيفنا متغير `SCRIPTS` مع `هستوغرام` و `Qqplot` الأسماء. إذا كان علينا إضافة برنامج نصي آخر يتبع نفس النمط كهذين الأمرين، سوف نحتاج فقط إلى إضافته إلى متغير `SRIPTS` .

To build all of this, run

```bash
$ make -j 4
```
