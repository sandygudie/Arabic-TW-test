(binder)=
# Vestimenta

Neste capítulo, discutiremos a Binder do Projeto e mybinder.org como um meio de compartilhar pesquisas de forma transparente e interativa.

(binder-compartilhamento)=
## Por que você deveria compartilhar o seu trabalho?

A motivação para compartilhar os resultados de pesquisa é mais profundamente explorada no capítulo {ref}`rr-open`.

Em resumo, compartilhar seu código de pesquisa pode ajudar a fornecer contexto para os resultados que você apresenta, ilustrando o processo pelo qual você passou para alcançá-los. Ao compartilhar o código, Também evitamos reinventar a roda a fim de fazer avançar um tema de investigação, uma vez que os instrumentos anteriores estão disponíveis para serem complementados.

No entanto, a maior barreira de compartilhamento de código é muitas vezes instalar pacotes e configurar o ambiente computacional, como veremos na próxima seção. Ao compartilhar seu trabalho através de plataformas como mybinder.org:

- Instalar pacotes de software não é mais um desafio
- Pessoas usando sistemas operacionais diferentes têm experiências semelhantes já que o cálculo está acontecendo na plataforma, não sua máquina local
- Seu trabalho pode ser distribuído para um público mais amplo uma vez que a barreira técnica baixou

(binder-what)=
## O que é Projeto Binder?

Discutimos por que é importante compartilhar seu trabalho e chegámos a um ponto em que decidimos publicar alguns Notebooks do Jupyter com o código de análise de uma plataforma de colaboração, tais como o GitHub.

O GitHub é uma ótima plataforma para compartilhar código _estaticamente_. Se o repositório for público, qualquer pessoa poderá navegar até o seu Notebook e ler o conteúdo. No entanto, _executar o código_ é muito mais complicado do que apenas exibi-lo como o GitHub. Muitas peças interdependentes são necessárias para executar o código, tais como:

- uma cópia do próprio código;
- o software apropriado para executá-lo;
- quaisquer pacotes extras que o código depende que não sejam enviados como parte do software principal;
- quaisquer dados de entrada que a análise exige;
- e você também precisa de algum hardware (um computador!) para executá-lo também.

Além de adquirir todas essas partes, você também precisa instalá-los corretamente e de tal forma que eles não sejam influenciados ou entrem em conflito com outros softwares que possam estar sendo executados em sua máquina. É muito trabalho!

Quão mais fácil seria se pudéssemos **executar código no navegador**, semelhante à forma como ele é exibido? É isso que o projeto Binder pretende alcançar.

A Binder fornece a seguinte infraestrutura a um usuário:

- algum hardware para executar código, geralmente um servidor hospedado na nuvem, mas também pode estar no local;
- um ambiente computacional que contém:
  - o software de approriate,
  - quaisquer dependências extras de pacotes,
  - todos os dados de entrada necessários,
  - e uma cópia do próprio código (Notebooks ou scripts);
- uma URL para onde o ambiente está rodando para que o código possa ser interagido por você ou seus colaboradores.

A Binder do projeto empacotou todas as partes em movimento que o tornam desafiador compartilhar o trabalho computacional em uma interface simples de uso. Há uma versão **gratuita e pública** desta interface executando em [**mybinder.org**](https://mybinder.org).

O desenho animado abaixo, por Juliette Taka, demonstra um fluxo de trabalho que o cientista usando o Binder pode adotar.

```{figure} ../figures/binder-comic.png
---
nome: binder_comic
alt: Uma ilustração dos passos que uma pessoa pode dar para criar um projeto binderizado.
---
Crédito digital: [Juliette Taka, Logilab e o projeto OpenDreamkit](https://opendreamkit.org/2017/11/02/use-case-publishing-reproducible-notebooks/)
```

Você pode saber mais sobre Project Binder e mybinder.org na sua página [Sobre mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

(binder-disam)=
### Desambiguação

Nesta secção, há alguns termos relacionados, que serão delineados aqui para clareza:

- **Binder Projeto**: Uma comunidade aberta que torna possível criar ambientes compartilháveis, interativos e reprodutíveis. A saída tecnológica deste projeto é um {ref}`rr-binderhub`.
- **BinderHub**: Uma infraestrutura baseada em nuvem para gerar Binders. O mais usado é o [mybinder.org](https://mybinder.org), que é mantido pela equipe do Projeto Binder. É construído sobre uma série de ferramentas de código aberto, incluindo [JupyterHub](https://z2jh.jupyter.org), para fornecer recursos de computação em nuvem aos usuários através de um navegador; e [`repo2docker`](https://repo2docker.readthedocs.io/), para construir imagens docker de projetos. Como se trata de um projeto aberto, é possível criar outros BinderHubs que podem suportar configurações mais especializadas. Uma dessas configurações poderia incluir autenticação para permitir que repositórios privados sejam compartilhados entre colaboradores fechados.
- **Um Binder**: Uma versão compartilhável de um projeto que pode ser visualizado e interagido dentro de um ambiente computacional reproduzível rodando na nuvem através de um navegador da web. Ao automatizar a instalação do ambiente de computação (conforme discutido no capítulo {ref}`rr-renv` ), A Binder do Projeto transforma a sobrecarga de compartilhar um ambiente desse tipo no ato de compartilhar uma URL.
- **[mybinder.org](https://mybinder.org)**: Um BinderHub, público e gratuito. Porque ele é público, você não deve usá-lo se o seu projeto exigir quaisquer informações pessoais ou confidenciais (como senhas).
- **Binderize**: O processo de criação de um Binder a partir de um projeto.

(binder-apropriado)=
## Quando é apropriado usar mybinder.org?

Manter um serviço gratuito e anônimo na nuvem é muito trabalho voluntário e custa muito dinheiro. Para reduzir um pouco os custos de corrida, mybinder.org coloca restrições computacionais em cada instância Binder corrente. Essas restrições são:

- 1 CPU, e
- 1 GB de RAM.

Portanto, mybinder.org **não é** um lugar apropriado para realizar replicações de ponta a ponta dos fluxos de trabalho de Aprendizagem de Máquina, por exemplo!

E esta é a principal razão pela qual este capítulo na Binder foi colocado no "Guia para Comunicação". Com essas restrições computacionais, mybinder.org se presta muito bem a hospedar demonstrações interativas e recursos de aprendizado para pacotes de software ou análises de pesquisa. Neste cenário, as pessoas que estão clicando no link Binder provavelmente querem aprender alguma coisa, e sentar-se em um processo demorado de formação de modelos provavelmente não os ajudará a conseguir isso. Em vez disso, você pode fornecer modelos pré-treinados ou instruções sobre como treinar os modelos em seu próprio hardware e _voltar_ para o Binder para o restante do tutorial interativo.

Então, quando é apropriado usar mybinder.org?

- Quando você quer _comunicar_ algo de forma interativa, como análises curtas, tutoriais ou até blogs! Confira [blog da Achintya Rao, alimentado por mybinder.org](https://blog.achintyarao.in/about/)!
- Quando o código e os dados associados (se relevantes) estão disponíveis publicamente
- Quando o código que você deseja executar interativamente não requer muito recurso ou recursos especializados (por exemplo, GPUs)

(binder-faqs)=
## FAQs

Muitas perguntas comuns são respondidas na [página Sobre mybinder.org](https://mybinder.readthedocs.io/en/latest/about/about.html).

### Como faço para salvar as minhas alterações no meu repositório?

Infelizmente, você não pode. Pelo menos, não na linha de comando em uma instância da Binder em execução.

Escrevendo de volta em um repositório hospedado, seja no GitHub ou em qualquer outra plataforma, exigirá uma credencial de algum tipo para autorizar você a escrever nesse repositório. E como já foi referido, mybinder. rg é um serviço completamente público e você não deve fornecer nenhuma informação sensível a uma instância de Binder em nenhuma circunstância.

No entanto, mybinder. rg executa um complemento chamado [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) que fornece um botão de download para salvar seus notebooks localmente, _mesmo que seu navegador tenha perdido a sua conexão com a infraestrutura da nuvem que está fornecendo o computador!_ Isto significa que você pode salvar seu progresso localmente, atualize seu repositório com seus cadernos salvos e reabra o seu Binder com os cadernos atualizados.

```{figure} ../figures/binder_notebook_banner.jpg
---
nome: binder_notebook_banner
alt: uma captura de tela do painel de controle de um Notebook Jupyter com um botão de download destacado por um retângulo roxo.
---
Usando este botão "Download" em um Jupyter Notebook em execução no mybinder. rg permitirá que você salve seus notebooks localmente, mesmo depois de a instância Binder ter sido desconectada de recursos computacionais.
```

### Como posso colaborar com meus pares em mybinder.org?

Não é impossível, mas definitivamente há espaço para desenvolver esse recurso em comparação com outros serviços de "computador gratuito na nuvem" disponíveis.

Aqueles que estão interessados nisso, pode saber mais em [este post do Discourse](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) e no [`jupyterlab-link-share` repositório](https://github.com/jtpio/jupyterlab-link-share).

### Como mybinder.org é diferente do Google Colab?

O Google Colab fornece um ambiente computacional "kked" com muitos dos pacotes de software de ciência de dados mais populares pré-instalados. Em contraste, mybinder.org builds imagens bespoke para cada repositório iniciado, especificamente instalando os pacotes listados em seus arquivos de configuração.

### Posso me conectar ao `INSERIR FORMAÇÃO DE DADOS AQUI`?

As conexões de rede no mybinder.org são bastante limitadas para fins de segurança e prevenção de abusos. Sendo assim, você deve ser capaz de se conectar a um provedor de dados externo, contanto que satisfaça os seguintes dois critérios:

- Ele pode ser acessado através de uma conexão HTTP/HTTPS
- Você não precisa de credenciais para acessar os dados

Lembre-se, mybinder.org é um serviço inteiramente público, e em nenhuma circunstância você deve fornecer informações confidenciais, como credenciais, a uma instância da Binder.

(binder-segue)=
## Como criar um projeto pronto para Binder

O próximo capítulo contém um [tutorial Zero-to-Binder](z2b) que irá guiá-lo pela criação de seu primeiro projeto pronto para Binder no GitHub.
