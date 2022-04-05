(rr-make-results)=
# Including numerical results and tables

في هذه المرحلة ربما تفكرون "هذا رائع جداً لدرجة أنني أستطيع الآن إدراج الأرقام في مخطوطاتي! But how exactly does this work for numerical results?"

الورق القابل للتكاثر المرتبط أعلاه يظهر طريقة واحدة للقيام بذلك: بعد حساب النتائج، يتم كتابتها في شكل جدول لاتيكس . Here is how one of these tables looks like right after it was computed:

```latex
\begin{tabular}{lrrr|rrrr}
Property & HypoParsr & Sniffer & Suitability & Pattern & Type & No Tie & Full\\
\hline
Delimiter & 87.48 & 86.82 & 65.41 & 92.61 & 88.33 & 91.38 & \textbf{94.92}\\
Quotechar & 82.90 & 92.36 & 44.60 & 95.23 & 90.10 & 93.80 & \textbf{97.36}\\
Escapechar & 87.96 & 94.37 & 74.85 & 97.95 & 96.26 & 95.44 & \textbf{99.25}\\
Overall & 80.60 & 85.45 & 38.19 & 90.99 & 83.61 & 90.61 & \textbf{93.75}\\
\hline
\end{tabular}
```

لتضمين هذا الجدول في مخطوطك، يمكنك استخدام دالة LaTeX's `\input{}` . إذا كان الملف مع الجدول يسمى `mytable.tex`، يمكن لهذا الأمر إدراجه في المخطوطة الخاصة بك:

```latex
\begin{table}
\input{mytable}
\end{table}
```

An alternative is to make use of variables. بدلاً من إنشاء جدول في ملف منفصل، يمكنك كتابة هيكل جدول الهيكل الأساسي وتمكينه من خلال المتغيرات. وترتبط النتائج التي تحسبها مع المتغيرات، وبمجرد تجميع المخطوطة الخاصة بك، يتم تبادل المتغيرات للحصول على نتائج رقمية حقيقية. Here is how such a table looks like in your manuscript:

```latex
\begin{table}
    \begin{tabular*}{ccc}
        \textbf{Variable} & \textbf{Mean}   & \textbf{Std. deviation} \
        \hline
        Variable 1        & \var1mean       & \var1std                \
        Variable 2        & \var2mean       & \var2std                \
    \end{tabular*}
\end{table}
```

ou أن `\var1medi` ليس الأمر القياسي لاتيكس: إنه متغير يمكنك تعريف نفسك! How is this done? ضع نصك البرمجي طباعة النتائج التي قمت بحسابها ضمن تعريف `\newcommand{}}` في ملف، على سبيل المثال مثل هذا (مثال بايثون المبسط):

```python
# this loops to data vectors of two variables (data1, data2), compute the
# mean and standard deviation, and print the results together with the
# variable name ('var1', 'var2')
for name, data in (['var1', data1], ['var2', data2]):
    mean = np.mean(data)
    std = np.mean(data)
    print('\\newcommand{\\%s }{ %f }' % (name + 'mean', mean))
    print('\\newcommand{\\%s }{ %f }' % (name + 'std', std))
```

دعونا نقول أن متوسط مجموعة البيانات الأولى هو 9.2، سيبدو التعريف مثل هذا: `\newcommand{\var1mean}{9.2}`. لاحظ أن هذا المثال يستخدم Python، ولكن يمكنك استخدام أي لغة أو طريقة تتعرف عليها لطباعة تعاريف مثل هذه. مع هذا التعريف، تبادل LaTeX خلية الجدول مع `\var1وسط` مع النتيجة الرقمية من الحساب. يمكنك التقاط التعاريف وكتابتها إلى ملف باستخدام إعادة التوجيه مع `>`. In this example, we write it to a file called `results_def.tex`

```makefile
results_def.tex: code/make_summary_stats.py
    python code/make_summary_stats.py > results_def.tex
```

كبديل ل `>`، يمكنك أيضًا إعادة توجيه النتائج باستخدام يونكس [أنابيب](https://en.wikipedia.org/wiki/Pipeline_(Unix)) و [tee](https://en.wikipedia.org/wiki/Tee_(command)) الأمر (`python code/make_summary_stats. y <unk> tee results_def.tex`). هذا لن يقوم فقط بإعادة توجيه إخراج البرنامج النصي إلى ملف، ولكن أيضا بطباعته في المحطة الطرفية الخاصة بك. هذه الخدعة المفيدة يمكن أن تساعدك على ملاحظة ما إذا كان كل شيء يعمل كما هو متوقع أثناء تنفيذ البرنامج النصي الخاص بك.

أخيرا، استخدم الأمر `input{}` لتضمين المتغيرات الجديدة في مخطوطك والمتغيرات في الجداول:

```latex
\begin{document}
\input{results_def.tex}
```

الأمثلة المعروضة هنا مبسطة، ولكن بقدر من التفكير، يمكنك التأكد من تضمين النتائج في مخطوطك كما يتم حسابها. هذا يساعدك (لا توجد أخطاء في نسخ النتائج إلى الجداول، ياي!) ويجعل البحث الخاص بك أيسر منالا وأكثر قابلية للتكرار.
