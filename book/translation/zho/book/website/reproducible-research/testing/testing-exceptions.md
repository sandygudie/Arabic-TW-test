(rr-testing-challenges)=
# Challenges and exceptional cases in testing

(rr-testing-challenges-stochastic-code)=
## Testing stochastic code

Sometimes code contains an element of randomness, a common example being code that makes use of [Monte Carlo methods](https://en.wikipedia.org/wiki/Monte_Carlo_method). Testing this kind of code can be very difficult because if it is run multiple times it will generate different answers, all of which may be "right", even is it contains no bugs. There are two main ways to tackle testing stochastic code:

### Use random number seeds

随机数种子有点难以解释，这就是一个例子。 这里有一个能打印三个随机数字的 Python 脚本。

```python
导入随机

# 打印三个随机数字
打印(random.random())
打印(random.random())
打印(random.random.random())
```

这个脚本没有漏洞，但如果你一再运行它，你每次都会得到不同的答案。 现在让我们随机设置一个随机的种子。

```python
导入随机

# 设置随机的种子
随机种子
 随机种子

# 打印三个随机数
打印机(随机随机数)
打印机(随机数.随机数)
打印机(随机数.随机数) 
 打印(随机数)
```

现在，如果您运行此脚本，它将输出

```python
0.134364244112
0.8474333736937
0.763774618977
```

每次运行此脚本时，您都会得到 *相同的* 输出。 它将打印相同的 ** 三个随机数。 如果随机数种子被更改，你将会获得不同的三个随机数字：

```python
0.956034271889
0.947827487059
0.0565513677268
```
but again you will get those same numbers every time the script is run in the future.

随机数种子是使事情变得可靠随机的一种方式。 然而，依靠随机数种子进行测试的风险是很小的。 说你有一个像这样的函数：

```python
def my_function():
  a = calculation_that_uses_two_random_numbers()
  b = calculation_that_uses_fiv_random_numbers()
  c = a + b
```

If you set the random number seed you will always get the same value of `c`, so it can be tested. But, say the model is changed and the function that calculates `a` uses a different number of random numbers that it did previously. Now not only will `a` be different but `b` will be too, because as shown above the random numbers outputted given a random number seed are in a fixed order. As a result the random numbers produced to calculate `b` will have changed. This can lead to tests failing when there is in fact no bug.

#### Measure the distribution of results

Another way to test code with a random output is to run it many times and test the distribution of the results. Perhaps the result may fluctuate a little, but is always expected around 10 within some tolerance. That can be tested. The more times the code is run the more reliable the average and so the result. However the more times you run a piece of code the longer it will take your tests to run, which may make tests prohibitively time-consuming to conduct if a reliable result is to be obtained. Furthermore, there will always be an element of uncertainty and if the random numbers happen to fall in a certain way you may get result outside of the expected tolerance even if the code is correct.

Both of these approaches to testing stochastic code can still be very useful, but it is important to also be aware of their potential pitfalls.

(rr-testing-challenges-difficult-quatify)=
## Tests that are difficult to quantify

Sometimes (particularly in research) the outputs of code are tested according to whether they "look" right. For example say we have a code modelling the water levels in a reservoir over time.

The result may look like this:

```{figure} ../../figures/eyeball-test1.jpg
---
名称：eyeball测试1
备选案文：
-
```

On a day with rain it might look like this:

```{figure} ../../figures/eyeball-test2.jpg
---
name: eyeball-test2
alt:
---
```

and on a dry day it might look like this:

```{figure} ../../figures/eyeball-test3.jpg
---
名称：eyeball测试3
备选案文：
---
```

All of these outputs look very different but are valid. However, if a researcher sees a result like this:

```{figure} ../../figures/eyeball-test-error.jpg
----
名称: eyeball-test-errer
alt:
---
```

they could easily conclude there is a bug as a lake is unlikely to triple its volume and then lose it again in the space of a few hours. 像这样的“Eyeballing”测试是耗费时间的，因为它们必须由人来完成。 然而，通过创建基本的“健康检查”，这一过程可以部分或完全自动化。 例如，一次性水位应该是在水位范围内，例如，在前一阶段应该是10%的水量。 Another check could be that there are no negative values, as a lake can't be -30% full. These sort of tests can't cover every way something can be visibly wrong, but they are much easier to automate and will suffice for most cases.

(rr-testing-challenges-non-integer)=
## Testing if non-integer numbers are equal

### When 0.1 + 0.2 does not equal 0.3

There is a complication with testing if the answer a piece of code outputs is equal to the expected answer when the numbers are not integers. Let's look at this Python example, but note that this problem is not unique to Python.

如果我们将0.1分配给 `a` a 和 0.2分配给 `b` 并打印它们的金额，我们将按预期得到0.3。

```python
>>> a = 0.1
>>> b = 0.2
>>> print(a+b)
0.3
```

但是，如果我们比较 `a` plus `b` 到 0.3 的结果，我们就会得到False。

```python
>>> 打印(a+b == 0.3)
错误
```

如果我们直接显示 `a` plus `b` 的值, 我们可以看到一个微小的差错。

```python
>>> a + b
0.3000000000004
```

这是因为浮点数是实际数字的近似值。 浮点数计算的结果可能取决于编译器或解释器、处理器或系统结构以及正在使用的 CPU 或进程的数量。 这可能是写入测试的主要障碍。

### Equality in a floating point world

在比较浮点数的均等性时，我们必须在给定的宽度内进行比较，也可以称之为阈值或三角洲。 For example, we might consider the calculated and expected values of some number to be equal if the absolute value of their difference is within the absolute value of our tolerance.

许多测试框架提供了将浮点数与特定容忍度范围内的均等值进行比较的功能。 例如，对于框架pest：

```python
导入pytest

a = 0.1
b = 0.2
c = a + b
sectc == pytest.approx(0.3)
```

this passes, but if the 0.3 was changed to 0.4 it would fail.

Unit test frameworks for other languages also often provide similar functions:

- Cunit for C: CU_ASSERT_DOUBLE_EQUAL(actual, expected, granularity)
- CPPUnit for C++: CPPUNIT_ASSERT_DOUBLES_EQUAL(expected, actual, delta)
- googletest for C++: ASSERT_NEAR(val1, val2, abs_error)
- FRUIT for Fortran: subroutine assert_eq_double_in_range_(var1, var2, delta, message)
- JUnit for Java: org.junit.Assert.assertEquals(double expected, double actual, double delta)
- testthat for R:
  - expect_equal(actual, expected, tolerance=DELTA) - absolute error within DELTA
  - 期望等价(实际，预期，尺寸=预期，容忍度=DELTA) - DELTA中的相对错误
- 朱利亚：
  - `val1 ≈ val2`
  - `isapprox(val1, val2, atol=abs_delta, rtol=rel_delta)`
  - `Test.jl` with `origin.`: `@test val1 assistance val2 atol=abs_delta rtol=rel_delta`
