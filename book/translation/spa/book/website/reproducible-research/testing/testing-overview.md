(rr-testing-overview)=
# Overview of Testing Types

There are a number of different kinds of tests, which will be discussed here.

Firstly there are positive tests and negative tests. Positive tests check that something works, for example testing that a function that multiplies some numbers together outputs the correct answer. Negative tests check that something generates an error when it should. For example nothing can go quicker than the speed of light, so a plasma physics simulation code may contain a test that an error is outputted if there are any particles faster than this, as it indicates there is a deeper problem in the code.

In addition to these two kinds of tests, there are also different levels of tests which test different aspects of a project. These levels are outlined below and both positive and negative tests can be present at any of these levels. A thorough test suite will contain tests at all of these levels (though some levels will need very few).

(rr-testing-types-of-testing)=
## Types of Testing

[Pruebas de humo](#Smoke_testing): Comprobaciones iniciales muy breves que garantizan los requisitos básicos necesarios para ejecutar el proyecto. If these fail there is no point proceeding to additional levels of testing until they are fixed.

[Prueba unitaria](#Unit_tests): Un nivel del proceso de prueba de software donde se prueban las unidades individuales de un software. The purpose is to validate that each unit of the software performs as designed.

[Prueba de integración](#Integration_testing): Un nivel de prueba de software donde las unidades individuales se combinan y prueban como un grupo. The purpose of this level of testing is to expose faults in the interaction between integrated units.

[Prueba del sistema](#System_tests): Un nivel del proceso de prueba de software donde se prueba un sistema completo e integrado. The purpose of this test is to evaluate whether the system as a whole gives the correct outputs for given inputs.

[Pruebas de aceptación](#Acceptance_testing): Un nivel del proceso de prueba de software donde un sistema es probado para ser aceptado. The purpose of this test is to evaluate the system's compliance with the project requirements and assess whether it is acceptable for the purpose.

Aquí hay una analogía: durante el proceso de fabricación de un bolígrafo, la tapa, el cuerpo, la cola, el cartucho de tinta y el punto de pelota se producen por separado y la unidad de prueba por separado. Cuando dos o más unidades están listas, se ensamblan y se realizan pruebas de integración, por ejemplo una prueba para comprobar que la tapa encaja en el cuerpo. Cuando la pluma completa está integrada, las pruebas del sistema se realizan para comprobar que se pueden utilizar para escribir como cualquier bolígrafo. Las pruebas de aceptación podrían ser una comprobación para asegurar que el bolígrafo es el color que el cliente ha pedido.

También hay otro tipo de pruebas llamadas pruebas de regresión. Las pruebas de Regresión son un tipo de prueba que se puede realizar en cualquiera de los cuatro niveles principales y compara los resultados de las pruebas antes y después de que se haga un cambio en el código, y da un error si son diferentes.

Estos diferentes tipos de pruebas se discuten con más detalle en los subcapítulos siguientes.
