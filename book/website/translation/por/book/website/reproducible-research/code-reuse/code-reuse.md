(rr-code-reuse)=
# Código reutilizável
Seu projeto de software pode variar de um pequeno script que você usa para processamento de dados até um caderno usado para a análise de dados, ou uma biblioteca de software implementando seus algoritmos. Independentemente do quão grande ou pequeno seja seu projeto de software, é importante tornar seu código reutilizável.

Diferentes tipos de software têm diferentes requisitos para ser reutilizável: para um pequeno script, ter documentação suficiente pode ser suficiente, enquanto para uma biblioteca de software crítico de missão, pode ser necessário um teste completo. No nível mais básico, tudo o que você precisa fazer é colocar seu código online em algum lugar que provavelmente durará muito tempo. Uma abordagem mais elaborada para tornar seu software de pesquisa mais reutilizável é seguindo os Princípios FAIR para o Software de Pesquisa (FAIR4RS Princípios) {cite:ps}`ChueHong2021FAIR4RS`.

Quando falamos em tornar o código reutilizável, é útil esclarecer o que é que queremos dizer. Na tabela de definições de {ref}`<rr-overview-definitions-reproducibility>` definimos a pesquisa reprodutível como usando os mesmos dados e o mesmo código. No entanto, quando falamos sobre reutilização de código, isso pode assumir muitas formas: podemos querer executar exatamente o mesmo código (para linguagens de programação compiladas), isto pode até mesmo significar o mesmo arquivo binário), ou podemos querer modificar o código-fonte e estendê-lo de alguma forma específica para atender às nossas necessidades. Freire e Chirigati {cite:ps}`Freire2018Reproducibility` fornecem uma estrutura de diferentes níveis de reprodução, dependendo do que pode ser modificado. Definem os seguintes níveis de reprodução: repetível, reexecutável, portátil, expansível e modificável.

Podemos mapear as definições de reprodutível no quadro de Freire da seguinte forma:

| Freire framework | Definições de reprodução                                                 |
| ---------------- | ------------------------------------------------------------------------ |
| Repetível        | Reprodutível (mesmo dados, mesma análise)                                |
| Reexecutável     | Robusto & Replicável (mesmo código, diferentes dados/análise/parâmetros) |
| Portátil         | *Não considerado* (mesmo código/dados, ambiente diferente)               |
| Extensível       | (parte) Generalizável                                                    |
| Modificável      | (parte) Generalizável                                                    |

Portabilidade não era considerada anteriormente, mas para software um ambiente diferente (como hardware diferente, sistema operacional ou mesmo uma nova instalação em hardware comparável) pode afetar a capacidade de o software funcionar (por exemplo, isso pode afetar dependências).

Além disso, o Generalisable encapsula dois conceitos: Extensível (a habilidade de se integrar com outros softwares) e modificável (a habilidade de alterar parte da implementação para estender sua funcionalidade).

No restante deste capítulo, fornecemos a lista de recomendações que você pode seguir para garantir que seu código seja reutilizável.

(rr-code-reuse-recomendação-checklist)=
## Como tornar seu código mais reutilizável
Esta seção contém uma lista de verificações de recomendações para tornar seu software mais reutilizável. The {ref}`rr-code-reuse-recommendation-details` section contains a more in-depth explanation of each of these recommendations. Você pode seguir as recomendações que são mais adequadas para o seu tipo de software e ignorar as que não são relevantes no seu caso.

### Recomendações repetidas
1. Certifique-se de que você pode encontrá-lo (no espaço)
1. Certifique-se de que você possa encontrá-lo (em tempo)
1. Certifique-se de que você pode executar a mesma sequência de operações
1. Certifique-se de que seu ambiente e sequência de operações são robustos e nenhum humano é necessário para replicar o que foi feito
1. Licença do seu código
    - com uma licença que permite reutilização;
    - com uma licença compatível com as licenças das dependências
1. Certifique-se de que está acessível
1. Incluir os dados necessários
1. Escrever documentação útil*

### Recomendações reexecutáveis
1. Remova bits codificados e faça o código modular
1. Teste se os módulos que você criou podem ter diferentes tipos de dados ou parâmetros de entrada
1. Transformar os módulos em um pacote/caixa de ferramentas
1. Escrever documentação útil*

### Recomendações portáteis
1. Certifique-se de que você pode recriar o ambiente onde ele viveu.
1. Escrever documentação útil*

### Recomendações extensíveis
1. Escrever documentação útil*

### Recomendações modificáveis
1. Certifique-se de que seu código é legível por humanos
1. Certifique-se de que os comentários estão presentes
1. Escrever documentação útil*

O leitor observante pode notar que `Escrever documentação útil` é mencionada para cada nível de reutilização. Isto deve-se ao facto de serem necessários diferentes níveis de documentação para diferentes níveis de reutilização.

### Diferentes requisitos de documentação para diferentes níveis de reutilização
Escrever documentação útil é um requisito importante para todos os níveis de reutilização. No entanto, para os diferentes níveis de reutilização, existem diferentes requisitos de documentação:

A documentação:
- explica o uso, especificação:
  - o que o software faz; (necessário para repetição)
  - como pode ser usado; (necessário para repetição)
  - que opções/parâmetros estão disponíveis. (necessário para repetição)
- contém exemplos de como executá-lo. (necessário para repetição)
- tem instruções de instalação, incluindo boas descrições de:
  - o hardware do qual depende (por exemplo GPUs); (necessário para portátil)
  - o sistema operacional no qual o software foi testado; (necessário para portátil)
  - requisitos de software (como bibliotecas e configurações de shello). (necessário para portátil)

(rr-code-reuse-recomendação-detalhes)=
## Recomendações para código reutilizável
Certifique-se de que você (ou outra pessoa) pode reutilizar o seu código para fazer a mesma coisa exatamente. A seção {ref}`rr-code-reuse-recommendation-checklist` contém uma lista de verificações de recomendações para tornar seu software mais reutilizável. Nesta secção há uma explicação mais aprofundada de cada uma destas recomendações, com indicações para outras partes relevantes deste guia.

### Recomendações repetidas
Neste estágio, talvez você não precise sequer abrir o código e lê-lo, você só quer ter certeza de que pode voltar a executar todas as etapas necessárias e obter os mesmos resultados que você tiu.

#### 1. Certifique-se de que você pode encontrá-lo (no espaço)
Seu código deve ser armazenado publicamente e compartilhado com os colaboradores. Tem um identificador único e persistente, para que todos possam encontrá-lo e acessá-lo.

**Veja também**: {ref}`rr-vcs`

#### 2. Certifique-se de que você possa encontrá-lo (em tempo)
Idealmente, a evolução temporal do código está documentada com controle de versão. Isso permite que você recupere uma versão específica do passado.

**Veja também**: {ref}`rr-vcs`

#### 3. Certifique-se de que você pode executar a mesma sequência de operações
Muitas vezes, o ser humano que criou o ambiente é também aquele que escreveu o código e aquele que conhece a ordem exacta dos passos necessários para poder reexecutar o código e reproduzir os resultados. Isto poderia certamente ser cuidadosamente documentado para que outro humano o refaça.

**Veja também**: [Lição do CodeRefinery sobre Pesquisa Reprodutiva](https://coderefinery.github.io/reproducible-research/)

#### 4. Certifique-se de que seu ambiente e sequência de operações são robustos e nenhum humano é necessário para replicar o que foi feito
Não querem depender do ser humano. Tendem a cometer erros, mesmo que não tenham más intenções. Então você quer que seu ambiente seja escrito e seja re-criado quando necessário, e deseja que sua sequência de operações seja executada por um script de pipeline que cola todas as sequências de passos.

**Veja também**: {ref}`rr-renv-options`

#### 5. Licença do seu código
Certifique-se de anexar uma licença ao seu código e especifique como você deseja ser citado quando as pessoas a reutilizarem. Considere usar uma licença permissiva que permita a reutilização. Além disso, você deve escolher uma licença que seja compatível com as licenças das bibliotecas ou pacotes que o seu software depende.

**Veja também**: {ref}`rr-licensing-software`, {ref}`rr-licensing-software-permissive`, {ref}`rr-licensing-compatibilidade`

#### 6. Certifique-se de que está acessível
Certifique-se de especificar como você deseja ser citado quando as pessoas o reutilizarem.

**Veja também**: {ref}`cm-citable-cite-software`

#### 7. Incluir os dados necessários
Se o software depende de qualquer tipo de dados, os dados devem estar disponíveis

**Veja também**: {ref}`rr-rdm-data`

### Recomendações reexecutáveis
Certifique-se de que você (ou outros) pode reutilizá-lo para fazer a coisa que você fez, mas com diferentes dados/parâmetros diferentes

#### 1. Remova bits codificados e faça o código modular
Você não quer ter detalhes específicos de seus dados ou parâmetros de análise codificados no código. Se algo pode se tornar uma função reutilizável, separe-a dos parâmetros codificados e transforme-a em algo (re)usável por conta própria. Torne os módulos puros: dado o mesmo input, uma função pura sempre retorna o mesmo valor.

**Veja também**: [lição de desenvolvimento do CodeRefinery Modular Code](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/modular-code-development/master/talk.md/#1)

#### 2. Teste se os módulos que você criou podem ter diferentes tipos de dados ou parâmetros de entrada
Você talvez não saiba ainda como seu código será reutilizado no futuro. mas você pode evitar como não deve ser usado se você puder testar quais parâmetros são permitidos.

**Veja também**: [Aula com CodeRefinery sobre testes automatizados](https://coderefinery.github.io/testing/motivation/)

#### 3. Transformar os módulos em um pacote/caixa de ferramentas
Separe ainda mais as especificações do seu projeto com os bits que podem ser reutilizados em outros de seus projetos ou por outras pessoas.

**Veja também**: {ref}`rr-renv package`, [Packaging software](https://scicomp.aalto.fi/scicomp/packaging-software/), [Pacotes de software em Python](https://aaltoscicomp.github.io/python-for-scicomp/packaging/)

### Recomendações portáteis
A portabilidade refere-se à capacidade de transferir software para um novo ambiente. Isso pode se referir a uma máquina idêntica (mas não a mesma), mas também pode se referir a uma nova arquitectura de hardware, sistema operacional e coisas assim. Ambos são importantes para a reutilização de software.

#### 1. Certifique-se de que você pode recriar o ambiente onde ele viveu.
O ambiente é um instantâneo frágil no tempo que acompanha silenciosamente o código. Pode incluir o humano que operou o software, os passos que o humano fez para preparar os dados, o hardware, SO, bibliotecas, pacotes/caixas/dependências externas. Tudo isto pode ser cuidadosamente documentado para que outro ser humano refaça os mesmos passos.

**Veja também**: {ref}`rr-renv`

### Recomendações extensíveis e modificáveis
Certifique-se de que outros podem usar o seu código para estendê-lo e melhorá-lo.

#### 1. Certifique-se de que seu código é legível por humanos
Geralmente, paga mais escrever códigos para outros seres humanos para que eles possam lê-lo (incluindo o seu próprio futuro). Um isolante crítico com nomes de variáveis obscuros não é mais rápido ou mais eficiente do que dividir um linho em várias etapas com nomes de variáveis legíveis que fazem sentido. Além disso, o recurso a convenções de codificação ajudará outros leitores.

**Veja também**: {ref}`rr-code-style-and-formatting`, {ref}`rr-code-quality-advantages`

#### 1. Certifique-se de que os comentários estão presentes
Escreva comentários antes de escrever o código real. Imagine que alguém poderia ler os comentários e pular todos os bits de código entre comentários e ter uma imagem completa do que está acontecendo como se lesse o código inteiro.
