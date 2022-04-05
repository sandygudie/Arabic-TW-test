(rr-testing-challenges)=
# Challenges and exceptional cases in testing

(rr-testing-challenges-stochastic-code)=
## Testing stochastic code

Sometimes code contains an element of randomness, a common example being code that makes use of [Monte Carlo methods](https://en.wikipedia.org/wiki/Monte_Carlo_method). Testing this kind of code can be very difficult because if it is run multiple times it will generate different answers, all of which may be "right", even is it contains no bugs. There are two main ways to tackle testing stochastic code:

### Use random number seeds

El número aleatorio de semillas son un poco difíciles de explicar, así que aquí hay un ejemplo. Aquí hay un pequeño script Python que imprime tres números aleatorios.

```python
importar al azar

# Imprime tres números aleatorios
print(random.random())
print(random.random())
print(random.random())
```

Este script no tiene fallos, pero si lo ejecuta repetidamente recibirá respuestas diferentes cada vez. Ahora vamos a establecer una semilla de número aleatorio.

```python
importar al azar

# Establecer una semilla de números aleatoria
random.seed(1)

# Imprimir tres números aleatorios
print(random.random())
print(random.random())
print(random.random())
```

Ahora si ejecuta este script saldrá

```python
0.134364244112
0.847433736937
0.763774618977
```

y cada vez que ejecutes este script obtendrás la *misma* salida, imprimirá *los mismos* tres números aleatorios. Si se cambia la semilla de números aleatorios obtendrás tres números aleatorios diferentes:

```python
0.956034271889
0.947827487059
0.0565513677268
```
but again you will get those same numbers every time the script is run in the future.

Las semillas de números aleatorios son una forma de hacer las cosas de manera fiable al azar. Sin embargo, un riesgo con pruebas que dependen de las semillas de números aleatorios puede ser alto. Digamos que tienes una función estructurada algo como esto:

```python
def my_function():
  a = cálculo_that_uses_two_random_numbers()
  b = cálculo_that_uses_five_random_numbers()
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
nombre: eyeball-test1
alt:
---
```

On a day with rain it might look like this:

```{figure} ../../figures/eyeball-test2.jpg
---
nombre: eyeball-test2
alt:
---
```

and on a dry day it might look like this:

```{figure} ../../figures/eyeball-test3.jpg
---
nombre: eyeball-test3
alt:
---
```

All of these outputs look very different but are valid. However, if a researcher sees a result like this:

```{figure} ../../figures/eyeball-test-error.jpg
---
nombre: eyeball-test-error
alt:
---
```

they could easily conclude there is a bug as a lake is unlikely to triple its volume and then lose it again in the space of a few hours. Las pruebas "Eyeballing" como estas requieren mucho tiempo, ya que deben ser realizadas por un ser humano. Sin embargo, el proceso puede automatizarse parcial o completamente mediante la creación de "comprobaciones de sanidad" básicas. Por ejemplo, el nivel de agua en un momento debería estar dentro de, digamos, el 10% del nivel de agua en el paso anterior del tiempo. Another check could be that there are no negative values, as a lake can't be -30% full. These sort of tests can't cover every way something can be visibly wrong, but they are much easier to automate and will suffice for most cases.

(rr-testing-challenges-non-integer)=
## Testing if non-integer numbers are equal

### When 0.1 + 0.2 does not equal 0.3

There is a complication with testing if the answer a piece of code outputs is equal to the expected answer when the numbers are not integers. Let's look at this Python example, but note that this problem is not unique to Python.

Si asignamos 0.1 a `a` y 0.2 a `b` e imprimimos su suma, obtenemos 0.3, como se esperaba.

```python
>>> a = 0.1
>>> b = 0.2
>>> print(a + b)
0.3
```

Sin embargo, si comparamos el resultado de `a` más `b` a 0.3 obtenemos False.

```python
>>> print(a + b == 0.3)
False
```

Si mostramos el valor de `a` más `b` directamente, podemos ver que hay un margen sutil de error.

```python
>>> a + b
0.3000000000000000004
```

Esto se debe a que los números de punto flotante son aproximaciones de números reales. El resultado de cálculos de coma flotante puede depender del compilador o intérprete, de la arquitectura del procesador o del sistema y del número de CPUs o procesos que se estén utilizando. Esto puede presentar un obstáculo importante para la escritura de pruebas.

### Equality in a floating point world

Al comparar los números de coma flotante por igualdad, tenemos que compararlos dentro de una tolerancia determinada, llamando alternativamente umbral o delta. For example, we might consider the calculated and expected values of some number to be equal if the absolute value of their difference is within the absolute value of our tolerance.

Muchos marcos de pruebas proporcionan funciones para comparar la igualdad de números de coma flotante con una tolerancia determinada. Por ejemplo, para el pytest del marco:

```python
import pytest

a = 0.1
b = 0.2
c = a + b
assert c == pytest.approx(0.3)
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
  - expect_equal(real, esperado, escala=esperado, tolerancia=DELTA) - error relativo dentro de DELTA
- Mañana:
  - `val1 ≈ val2`
  - `isapprox(val1, val2, atol=✫ _delta, rtol=rel_delta)`
  - `Test.jl` with `mañana`: `@test val1 ► val2 atol=is_delta rtol=rel_delta`
