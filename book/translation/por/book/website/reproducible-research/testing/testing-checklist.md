# Checklist para teste de código

Esta lista de verificação contém um monte de itens. As {ref}`mentioned before<rr-testing-write-tests>`, it is far better to do some of the items than none of them. Não desanime se esta lista de tarefas parecer intransponível.

<a name="Writing_tests"></a>

## Testes de escrita

- Escrevam algumas provas de fumo.
- Escreva testes de unidade para todas as unidades do seu código.
- Escreva testes de integração para verificar a integração entre unidades.
- Escreva alguns testes do sistema. Priorize caminhos comuns e importantes através do programa.
- Escreva testes de regressão. Podem existir testes de regressão em qualquer nível de teste.
- Se apropriado para testes de aceitação de seu projeto.
- Adicione testes de tempo de execução ao seu projeto.

<a name="Good_practice_checks"></a>

## Boas verificações práticas

- [ ] Document the tests and how to run them.
  - [ ] Write scripts to set up and configure any resources that are needed to run the tests.
- [ ] Pick and make use of a testing framework.
- [ ] Run the tests regularly.
  - [ ] Automate the process of running tests. Consider making use of continuous integration (see continuous integration chapter) to do this.
- [ ] Check the code coverage of your tests and try to improve it.
- [ ] Engage in code review with a partner.
