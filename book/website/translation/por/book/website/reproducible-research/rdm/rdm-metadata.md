(rr-rdm-metadados)=
# Documentação e Metadados

Ter dados disponíveis de nada serve se não for possível compreendê-los. Por exemplo, uma tabela de números é inútil se não houver nenhum título que descreva o que as colunas/linhas contêm. Portanto, você deve garantir que conjuntos de dados abertos incluam documentação.

## Documentação

A documentação fornece um contexto para o seu trabalho. Ele permite aos vossos colaboradores, colegas e futuros entenderem o que foi feito e porquê. A documentação dos dados pode ser feita em diferentes níveis. Todos os dados que acompanham a documentação devem ser escritos em linguagem clara e clara. A documentação permite que os usuários tenham informações suficientes para entender a fonte, pontos fortes, fragilidades e limitações analíticas dos dados para que possam tomar decisões informadas ao usá-los.

## Metadados

Metadados são informações sobre os dados, descritores que facilitam a catalogação de dados e a descoberta de dados. Muitas vezes, os metadados são destinados à leitura de máquina. Quando os dados são enviados para um repositório de dados confiável, os metadados legíveis por máquina são gerados pelo repositório. Se os dados não estiverem em um repositório, um arquivo de texto com metadados legíveis por máquina pode ser adicionado como parte da documentação.

- O tipo de investigação e a natureza dos dados também influenciam o tipo de documentação que é necessário.
- O nível de documentação e metadados [{term}`def<Metadata>`] variará de acordo com o projeto, e a gama de pessoas tem de ser compreendida.
- Exemplos de documentação podem incluir itens como [dicionários de dados](https://help.osf.io/hc/en-us/articles/360019739054-How-to-Make-a-Data-Dictionary) ou codebookks, protocolos, livros de registro ou periódicos de laboratório, arquivos README, logs de pesquisa, sintaxe de análise, algoritmos e comentários de código.
- Variáveis devem ser definidas e explicadas usando dicionários ou livros de código.
- Os dados devem ser armazenados em estruturas de pastas lógicas e hierárquicas, com um arquivo README usado para descrever a estrutura. O arquivo README é útil para outras pessoas e também ajudará você a encontrar seus dados no futuro {cite:ps}`Fuchs2018Document`. Veja o modelo LEIAME [da Cornell](https://cornell.app.box.com/v/ReadmeTemplate) para um exemplo.
- É uma boa prática utilizar padrões de metadados comunitários reconhecidos para facilitar a combinação de conjuntos de dados.

(rr-rdm-metadados-padrões)=
### Padrões Comunitários - Metadados

O uso de padrões definidos pela comunidade para metadados é vital para a pesquisa reprodutível e permite a comparação de dados heterogéneos de múltiplas fontes. domínios e disciplinas. As normas dos metadados são específicas da disciplina. Por exemplo, para dados cerebrais, a [Estrutura de dados brain Imaging](https://doi.org/10.25504/FAIRsharing.rd1j6t) é o padrão a ser usado. No entanto, nem toda disciplina pode usar padrões de metadados. Você pode ver se a sua disciplina usa padrões de metadados através do [FAIRsharing](https://fairsharing.org/), um recurso para identificar e citar os metadados ou esquemas de identificação, bancos de dados ou repositórios que existem para seus dados e disciplina. Existem também situações em que os investigadores utilizam padrões de metadados mais gerais. por exemplo, quando usam um arquivo genérico para armazenar os seus dados têm de aderir aos padrões de metadados do arquivo. Neste caso, um arquivo de texto com metadados disciplinares específicos pode ser adicionado como parte da documentação.
