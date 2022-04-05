(rr-code-reuse-recomendações)=
# Visão geral da reutilização do código

This section contains a checklist of recommendations for making your software more reusable. A seção de detalhes`rr-code-reuse-` do {ref}contém uma explicação mais aprofundada de cada uma dessas recomendações. You can follow the recommendations that are more suitable for your type of software and skip the ones which are not relevant in your case.

## Recomendações Repetidas

1. Certifique-se de que você pode encontrá-lo (no espaço; significado: ser capaz de localizar o repositório/projeto)
1. Certifique-se de que você pode encontrá-lo (no tempo; significado: ser capaz de localizar uma determinada versão)
1. Make sure you can execute the same sequence of operations
1. Make sure your environment and sequence of operations is robust and no human is needed to replicate what was done
1. License your code
    - with a license that allows for reuse;
    - with a license compatible with the dependencies’ licenses
1. Make sure it is citable
1. Include necessary data
1. Write useful documentation*

## Recomendações reexecutáveis

1. Remova bits codificados (como caminhos que só existiam no disco rígido onde o pipeline era executado) e faça o código modular
1. Test that the modules you made can take different types of input data or parameters
1. Turn the modules into a package/toolbox
1. Write useful documentation*

## Recomendações Portáteis
1. Make sure you can recreate the environment where it lived
1. Write useful documentation*

## Recomendações Extensíveis
1. Write useful documentation*

## Recomendações modificáveis
1. Make sure your code is readable by humans
1. Make sure comments are present
1. Write useful documentation*

The observant reader might will notice that `Write useful documentation` is mentioned for every level of reuse. This is because different levels of documentation are required for different levels of reuse.

## Documentação

*Different documentation requirements for different levels of reuse*

Writing useful documentation is an important requirement for all levels of reuse. However, for the different levels of reuse, there are different documentation requirements:

The documentation:
- explains usage, specifying:
  - what the software does; (required for repeatable)
  - how it can be used; (required for repeatable)
  - what options/parameters are available. (required for repeatable)
- contains examples of how to run it. (required for repeatable)
- has installation instructions, including good descriptions of:
  - the hardware it depends on (for example GPUs); (required for portable)
  - the operating system the software has been tested on; (required for portable)
  - software requirements (such as libraries and shell settings). (required for portable)
