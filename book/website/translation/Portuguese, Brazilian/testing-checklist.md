# Checklist para teste de código

Esta lista de verificação contém um monte de itens. Como {ref}`mencionado antes de<rr-testing-write-tests>`, é muito melhor fazer alguns dos itens do que nenhum deles. Não desanime se esta lista de tarefas parecer intransponível.

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

- [ ] Documento os testes e como executá-los.
  - [ ] Escrever scripts para configurar e configurar todos os recursos necessários para executar os testes.
- [ ] Escolha e faça uso de um framework de teste.
- [ ] Execute os testes regularmente.
  - [ ] Automatize o processo de testes em execução. Considere utilizar a integração contínua (ver capítulo de integração contínua) para fazer isso.
- [ ] Verifique a cobertura do código de seus testes e tente melhorá-lo.
- [ ] Participe da revisão de código com um parceiro.
