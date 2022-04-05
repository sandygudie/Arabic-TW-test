(rr-testing-runtime)=
# Runtime testing

Runtime tests are tests that run as part of the program itself. They may take the form of checks within the code, as shown below:
```
population = population + people_born - people_died

// test that the population is positive
if (population < 0):
error( 'The number of people can never be negative' )
```

Another example of a use of runtime tests is internal checks within functions that verify that their inputs and outputs are valid, as shown below:
```
function add_arrays( array1, array2 ):

// prueba que los arrays tienen el mismo tamaño
if (array1. ize() != array2.size()):
  error ( '¡Los arrays tienen diferentes tamaños!' )

salida = array1 + array2

if (output.size() != array1.size()):
  error ( '¡El array de salida tiene un tamaño incorrecto!'' )

devuelve salida )

return output
```

Advantages of runtime testing:
- Run within the program, so can catch problems caused by logic errors or edge cases.
- Makes it easier to find the cause of the bug by catching problems early.
- Catching problems early also helps prevent them escalating into catastrophic failures. It minimises the blast radius.

Disadvantages of runtime testing:

- Tests can slow down the program.
- What is the right thing to do if an error is detected? How should this error be reported? Exceptions are a recommended route to go with this.
