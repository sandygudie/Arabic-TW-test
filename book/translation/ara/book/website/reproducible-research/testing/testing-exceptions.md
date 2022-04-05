(rr-testing-challenges)=
# Challenges and exceptional cases in testing

(rr-testing-challenges-stochastic-code)=
## Testing stochastic code

Sometimes code contains an element of randomness, a common example being code that makes use of [Monte Carlo methods](https://en.wikipedia.org/wiki/Monte_Carlo_method). Testing this kind of code can be very difficult because if it is run multiple times it will generate different answers, all of which may be "right", even is it contains no bugs. There are two main ways to tackle testing stochastic code:

### Use random number seeds

أعداد عشوائية من البذور يصعب تفسيرها قليلاً لذلك هنا مثال. إليك نص بايثون صغير يطبع ثلاثة أرقام عشوائية.

```python
استيراد عشوائي

# طباعة ثلاثة أرقام عشوائية
print(random.random())
print(random.random())
print(random.random())
```

هذا البرنامج النصي لا يحتوي على أي أخطاء ولكن إذا قمت بتشغيله بشكل متكرر، فستحصل على إجابات مختلفة في كل مرة. الآن دعونا نعيّن رقم عشوائي.

```python
استيراد عشوائي

# تعيين رقم عشوائي
عشوائي.seed(1)

# طباعة ثلاثة أرقام عشوائية
طبعة (random.random())
print(random.random())
print(random.random())
```

الآن إذا قمت بتشغيل هذا البرنامج النصي فإنه يخرجه

```python
0.134364244112 
 0.847433736937
0.763774618977
```

وفي كل مرة تقوم بتشغيل هذا البرنامج النصي ستحصل على *نفس* الإخراج، سيطبع *نفس* ثلاثة أرقام عشوائية. إذا تم تغيير رقم البذور العشوائي ستحصل على ثلاثة أرقام عشوائية مختلفة:

```python
0.956034271889
0.947827487059
0.0565513677268
```
but again you will get those same numbers every time the script is run in the future.

البذور العشوائية هي طريقة لجعل الأشياء عشوائية بشكل موثوق. غير أن خطر الاختبارات التي تعتمد على أعداد عشوائية هو أنها يمكن أن تكون حبيسة. قل أن لديك دالة منظمة مثل هذا:

```python
def my_function():
  a = calculation_that_uses_two_random_numbers()
  b = calculation_that_uses_five_random_numbers()
  c = a + b
```

If you set the random number seed you will always get the same value of `c`, so it can be tested. But, say the model is changed and the function that calculates `a` uses a different number of random numbers that it did previously. الآن لن يكون `` مختلفا فقط ولكن `ب` سيكون أيضا لأنه كما هو موضح أعلاه الأعداد العشوائية التي يتم إخراجها بسبب رقم عشوائي هي بترتيب ثابت. As a result the random numbers produced to calculate `b` will have changed. This can lead to tests failing when there is in fact no bug.

#### Measure the distribution of results

Another way to test code with a random output is to run it many times and test the distribution of the results. Perhaps the result may fluctuate a little, but is always expected around 10 within some tolerance. That can be tested. The more times the code is run the more reliable the average and so the result. However the more times you run a piece of code the longer it will take your tests to run, which may make tests prohibitively time-consuming to conduct if a reliable result is to be obtained. Furthermore, there will always be an element of uncertainty and if the random numbers happen to fall in a certain way you may get result outside of the expected tolerance even if the code is correct.

Both of these approaches to testing stochastic code can still be very useful, but it is important to also be aware of their potential pitfalls.

(rr-testing-challenges-difficult-quatify)=
## Tests that are difficult to quantify

Sometimes (particularly in research) the outputs of code are tested according to whether they "look" right. For example say we have a code modelling the water levels in a reservoir over time.

The result may look like this:

```{figure} ../../figures/eyeball-test1.jpg
---
name: eyeball test1
alt:
---
```

On a day with rain it might look like this:

```{figure} ../../figures/eyeball-test2.jpg
---
name: eyeball test2
alt:
---
```

and on a dry day it might look like this:

```{figure} ../../figures/eyeball-test3.jpg
---
الاسم: اختبار eyeball 3
البديل
---
```

All of these outputs look very different but are valid. However, if a researcher sees a result like this:

```{figure} ../../figures/eyeball-test-error.jpg
---
name: eyeball test-error
alt:
---
```

they could easily conclude there is a bug as a lake is unlikely to triple its volume and then lose it again in the space of a few hours. اختبارات "العين" مثل هذه تستغرق وقتاً طويلاً كما يجب أن يقوم بها الإنسان. غير أن هذه العملية يمكن أن تكون آلية جزئيا أو كليا عن طريق إنشاء "فحوص عافية" أساسية. فعلى سبيل المثال، ينبغي أن يكون مستوى المياه في وقت ما في حدود 10 في المائة من مستوى المياه في الخطوة السابقة على سبيل المثال. Another check could be that there are no negative values, as a lake can't be -30% full. These sort of tests can't cover every way something can be visibly wrong, but they are much easier to automate and will suffice for most cases.

(rr-testing-challenges-non-integer)=
## Testing if non-integer numbers are equal

### When 0.1 + 0.2 does not equal 0.3

There is a complication with testing if the answer a piece of code outputs is equal to the expected answer when the numbers are not integers. Let's look at this Python example, but note that this problem is not unique to Python.

إذا قمنا بتعيين 0.1 إلى `A` و 0.2 إلى `b` وطباعة المبلغ الخاص بهم، نحصل على 0.3، كما هو متوقع.

```python
>>> a = 0.1
>>> b = 0.2
>>> print(+ b)
0.3
```

ولكن إذا قمنا بمقارنة نتيجة `` + `b` إلى 0.3 فإننا نحصل على خطأ ما.

```python
>>> print(+ b == 0.3)
False
```

إذا نظرنا إلى قيمة `` + `b` مباشرة، يمكننا أن نرى أن هناك هامش خطأ دقيق.

```python
>>> a + b
0.300000000000004
```

ويرجع ذلك إلى أن أرقام النقاط العائمة هي أرقام تقريبية للأرقام الحقيقية. ويمكن أن تعتمد نتيجة الحسابات بالنقاط العائمة على المترجم أو المترجم الشفوي أو المعالج أو بنية النظام وعدد وحدات المعالجة المركزية أو العمليات المستخدمة. ويمكن أن يشكل ذلك عقبة رئيسية أمام اختبارات الكتابة.

### Equality in a floating point world

وعند مقارنة أرقام النقاط العائمة للمساواة، علينا أن نقارنها في إطار تسامح معين، ويطلق عليها بدلا من ذلك عتبة أو دلتا وعند مقارنة أرقام النقاط العائمة للمساواة، علينا أن نقارنها في إطار تسامح معين، ويطلق عليها بدلا من ذلك عتبة أو دلتا على سبيل المثال وقد نعتبر أن القيم المحسوبة والمتوقعة لبعض الأعداد متساوية إذا كانت القيمة المطلقة لاختلافها في حدود القيمة المطلقة لتسامحنا.

ويوفر العديد من أطر الاختبار وظائف لمقارنة المساواة بين الأعداد ذات النقاط العائمة في إطار تسامح معين. وعلى سبيل المثال بالنسبة لاختبار الإطار:

```python
استيراد بيتيست

أ = 0.1
ب = 0.2
ج = أ + ب
تأكيد c == pytest.approx (0.3)
```

this passes, but if the 0.3 was changed to 0.4 it would fail.

Unit test frameworks for other languages also often provide similar functions:

- Cunit for C: CU_ASSERT_DOUBLE_EQUAL(actual, expected, granularity)
- CPPUnit for C++: CPPUNIT_ASSERT_DOUBLES_EQUAL(expected, actual, delta)
- googletest for C++: ASSERT_NEAR(val1, val2, abs_error)
- FRUIT for Fortran: subroutine assert_eq_double_in_range_(var1, var2, delta, message)
- الوحدة المشتركة من أجل جافا: org.junit. Assert.assertEquals(كان متوقعا، فعلي مزدوج، دلتا مزدوجة)
- testthat for R:
  - expect_equal(actual, expected, tolerance=DELTA) - absolute error within DELTA
  - expect_equal(فعلي, متوقع, scale=المتوقع, tolerance=DELTA) - خطأ نسبي داخل DELTA
- جوليا:
  - `val1 ≈ val2`
  - `isapprox(val1, val2, atol=abs_delta, rtol=rel_delta)`
  - `Test.jl` مع `±`: `@testval1 ± val2 atol=abs_delta rtol=rel_delta`
