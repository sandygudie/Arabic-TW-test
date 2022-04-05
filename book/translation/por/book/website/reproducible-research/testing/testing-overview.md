(rr-testing-overview)=
# Visão geral dos Tipos de Teste

Há vários tipos de testes, que serão aqui discutidos.

Em primeiro lugar, há testes positivos e testes negativos. Testes positivos verificam se algo funciona, por exemplo, testando que uma função que multiplica alguns números juntos produz a resposta correta. Testes negativos verificam que algo gera um erro quando deveria. Por exemplo, nada pode ser mais rápido do que a velocidade da luz. então um código de simulação da física de plasma pode conter um teste de que um erro é gerado se houver alguma partícula mais rápido que isso, conforme indica que existe um problema mais profundo no código.

Para além destes dois tipos de testes, existem também diferentes níveis de testes que testam diferentes aspectos de um projecto. Estes níveis estão descritos abaixo e tanto os testes positivos como os negativos podem estar presentes em qualquer um destes níveis. Um conjunto de testes completo conterá testes a todos estes níveis (embora alguns níveis precisem de poucos).

(rr-testing-types-of-testing)=
## Tipos de Teste

[Smoke testing](#Smoke_testing): Very brief initial checks that ensures the basic requirements required to run the project hold. If these fail there is no point proceeding to additional levels of testing until they are fixed.

[Unit testing](#Unit_tests):    A level of the software testing process where individual units of a software are tested. O objetivo é validar que cada unidade do software funciona conforme projetado.

[Integration testing](#Integration_testing): A level of software testing where individual units are combined and tested as a group. O objectivo deste nível de testes é expor as falhas na interacção entre unidades integradas.

[System testing](#System_tests):    A level of the software testing process where a complete, integrated system is tested. The purpose of this test is to evaluate whether the system as a whole gives the correct outputs for given inputs.

[Acceptance testing](#Acceptance_testing):  A level of the software testing process where a system is tested for acceptability. O objectivo deste teste é avaliar a conformidade do sistema com os requisitos do projecto e avaliar se é aceitável para o fim.

Here's an analogy: during the process of manufacturing a ballpoint pen, the cap, the body, the tail, the ink cartridge and the ballpoint are produced separately and unit tested separately. When two or more units are ready, they are assembled and integration testing is performed, for example a test to check the cap fits on the body. When the complete pen is integrated, system testing is performed to check it can be used to write like any pen should. Acceptance testing could be a check to ensure the pen is the colour the customer ordered.

There is also another kind of testing called regression testing. Regression testing is a type of testing that can be performed at any of the four main levels and compares the results of tests before and after a change is made to the code, and gives an error if these are different.

These different types of tests are discussed in more detail in the next subchapters.
