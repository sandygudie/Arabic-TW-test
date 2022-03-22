(z2b)=
# Zero-para-Binder

Neste capítulo, vamos criar um projeto Binder do zero: primeiro vamos criar um repositório no GitHub e depois vamos iniciar no mybinder.org. Seções onde se espera que você complete uma tarefa são indicadas por três semáforos de luz 🚦 emojis. Algumas etapas lhe dão a opção do Python, Julia ou R - clique na aba do seu idioma preferido.

```{admonition} Attributions
Este tutorial se baseia em oficinas _Zero-to-Binder_ do Tim Head, que podem ser encontradas aqui: <http://bit.ly/zero-to-binder> e <http://bit.ly/zero-to-binder-rise>

Obrigado a Anna Krystalli e Oliver Strickson por sua ajuda no desenvolvimento do conteúdo de R e Júlia. respectivamente.
```

```{attention}
Binder pode levar muito tempo para carregar, mas isso não significa que seu Binder falhará ao iniciar.
Você sempre pode atualizar a janela se você ver a mensagem "... está demorando mais para carregar, pendurar firme!".
```

```{admonition} If you are using R...
Se você estiver seguindo o caminho R, incluímos algumas etapas alternativas usando o [pacote `holepunch`](https://github. om/karthik/holepunch) que criará seu ambiente usando uma [imagem base do rocker](https://github.com/rocker-org/rocker) e deverão, em última análise, ser mais rápido para construir e lançar.
```

(z2b-reqs)=
## Requisitos

Você vai precisar:

- **Algum código e alguns dados.** O código deve levar menos de **10 minutos para executar**, e os dados devem ser menores que **10 MB**. Isso pode significar que você só escolhe um script de um projeto maior, ou traz um subconjunto de seus dados. Note que é muito importante que o código e os dados possam ser tornados **públicos** , porque nós estaremos usando a instância pública de binder.
- **Uma conta GitHub.** Por favor, cadastre-se para uma se você ainda não tem uma: <https://github.com/join>

(z2b-step-1)=
## 1. Criando um repositório para Binderize

🚦🚦🚦

````{tabbed} Python
1) Crie um novo repositório no GitHub chamado "my-first-binder"
   - Certifique-se de que o repositório é **público**, _não_!
   - Não se esqueça de inicializar o repositório com um README!
2) Crie um arquivo chamado `hello.py` através da interface web com `print("Olá da Binder!")` na primeira linha e commit com a branch `main`
````

````{tabbed} Julia
1) Crie um novo repositório no GitHub chamado "my-first-binder"
   - Certifique-se de que o repositório é **público**, _não_!
   - Não se esqueça de inicializar o repositório com um README!
2) Crie um arquivo chamado `olá. l` através da interface web com `println("Olá de Binder! )` na primeira linha e commit com a branch `main`
3) Crie um arquivo chamado `Project. oml` (ATENÇÃO: a capitalização é importante!) com o seguinte conteúdo e compromete-o para `main`.
   Isto irá instalar o Julia no ambiente Binder.

   ```julia
   [compat]
   julia = "1.3"
```
````

````{tabbed} R
1) Crie um novo repositório no GitHub chamado "my-first-binder"
   - Certifique-se de que o repositório é **público**, _não_!
   - Não se esqueça de inicializar o repositório com um README!
2) Crie um arquivo chamado `olá. ` através da interface web com `print("Olá da Binder! )` na primeira linha e commit com a branch `main`
3) Crie um arquivo chamado `runtime. xt` com `r-2022-01-01` na primeira linha.
   Esta data representa o snapshot de [CRAN](https://cran.r-project.org/) hospedado no [RStudio Package Manager](https://packagemanager.rstudio.com) que vamos usar.
   Envie este arquivo para o branch `main`.

   ```{note}
   Em R você pode usar `holepunch::write_runtime()` para criar um `runtime.txt` no diretório `.binder/`; ele será configurado com a data de hoje.
   ```
````
(z2b-repositório-público)=
### Por que razão o repositório tem de ser público?
mybinder.org não pode acessar repositórios privados, pois isso exigiria um token secreto. A equipe binder optou por não assumir a responsabilidade de lidar com tokens secretos como mybinder.org é um serviço público e uma prova de conceito tecnológico. Se acessar repositórios privados é um recurso que você / sua equipe precisa, recomendamos que você analise para construir seu próprio [BinderHub](https://binderhub.readthedocs.io).
(z2b-step-2)=
## 2. Inicie o seu primeiro repositório!
🚦🚦🚦
1) Vá para **<https://mybinder.org>** 2) Digite a URL do seu repositório na caixa "GitHub repo ou URL". Deve ficar assim:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) À medida que você digita, a página da Web gera um link no "Copy the URL below. Caixa ." Deve ficar assim: **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** Copiá-lo, abrir uma nova aba do navegador e visitar essa URL - Você verá um "girar" quando o Binder abrir o repositório
Se tudo correu bem, você verá uma interface do JupyterLab.
(z2b-fundo-1)=
### O que está acontecendo no fundo? - Parte 1
Enquanto espera, o BinderHub (o backend do Binder) é:
- Buscando seu repositório no GitHub
- Analisando o conteúdo
- Construindo uma imagem Docker com base no seu repositório
- Largando a imagem Docker na nuvem
- Conectando você através do seu navegador
(z2b-step-3)=
## 3. Executar o script
🚦🚦🚦

````{tabbed} Python
1. No painel de lançamento, selecione "Terminal"
2. Na nova janela terminal, digite `python hello.py` e pressione return
````

````{tabbed} Julia
1. No painel de lançamento, selecione "Terminal"
2. Na nova janela do terminal, digite `julia hello.jl` e pressione return
````

````{tabbed} R
1. No painel de lançamento, selecione "Terminal"
2. Na nova janela do terminal, digite `Rscript -e 'source("olá.R")'` e então pressione return
````

`Olá de Binder!` será impresso no terminal.

(z2b-step-4)=
## 4. Fixando Dependências

Foi fácil de começar, mas nosso ambiente é desbones - vamos adicionar uma **dependência**!

🚦🚦🚦

````{tabbed} Python
1) Em seu repositório, crie um arquivo chamado `requirements.txt`
2) Adicione uma linha que diz: `numpy==1.14.5`
3) Verifique os tipos! Em seguida, commit com a branch `main`
4) Visite **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** novamente em uma nova aba
````

````{tabbed} Julia
1) Em seu repositório, edite o `Projeto. arquivo oml`
2) Adicione um novo bloco que diz:

   ```julia
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) Verificar por tipos! Em seguida, commit no 'main'.
4) Visite **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** novamente em uma nova aba
````

````{tabbed} R
1) Em seu repositório, crie um arquivo chamado `install.R`
2) Adicione uma linha que diz: `install.packages("readr")`
3) Confira os tipos! Em seguida, commit com a branch `main`
4) Visite **https://mybinder. rg/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** novamente em uma nova aba

```{note}
Se usando `holepunch`, você pode criar uma `instalar. ` arquivo e adicione automaticamente o código para instalar todas as dependências do seu projeto usando `holepunch::write_install()`.
```
````
Desta vez, clique em "Construir Logs" na barra grande, horizontal cinza. Isto permitirá que você acompanhe o progresso da sua construção. É útil quando sua compilação falha ou algo que você acha que _deveria estar_ instalado está faltando.

```{note}
Às vezes, os logs de compilação de Binder imprimem coisas em fonte vermelha, tais como avisos que `pip` não está atualizado (`pip` está frequentemente desatualizado porque é atualizado regularmente! ou instalar mensagens, especialmente se você estiver usando R.
Essas mensagens vermelhas não significam necessariamente que há um problema com sua compilação e vai falhar - é apenas uma infeliz escolha de cor da fonte!
```

(z2b-fundo-2)=
### O que está acontecendo no fundo? - Parte 2

Desta vez, o BinderHub lerá o arquivo de configuração que você adicionou e instalará a versão específica do pacote solicitado.

(z2b-dependencies)=
### Mais sobre fixação de dependências

````{tabbed} Python
No exemplo acima, nós usamos dois sinais iguais (`==`) para fixar a versão do `numpy`.
Isso diz à Binder para instalar a versão específica.

Outra maneira de fixar um número de versão é usar o sinal maior ou igual (`>=`) para permitir que qualquer versão acima de um determinado seja instalada.
Isso é útil quando você tem muitas dependências que podem ter dependências umas das outras e permite que a Binder encontre uma configuração de suas dependências que não entrem em conflito umas com as outras, evitando versões anteriores que possam quebrar ou alterar seu código.

Finalmente você não pode fornecer um número de versão (apenas o nome da biblioteca/pacote) e a Binder irá instalar a última versão desse pacote.
````

````{tabbed} Julia
No exemplo acima, copiamos um hash para o nosso arquivo `Project.toml` que está relacionado com a versão do pacote que gostaríamos de instalar.
Para um gráfico de dependência completo, nós também precisaríamos incluir um arquivo `Manifest.toml` que documentasse as dependências das dependências.
Entre esses dois arquivos, somos capazes de instanciar uma replicação exata de um ambiente Julia.

Claro que podemos imaginar que, à medida que o ambiente cresce e as interdependências se tornem mais complexas, seria muito tributável escrever esses arquivos manualmente!
A verdade é que você nunca faria isso manualmente, o gerenciador de pacotes `Pkg` embutido pode [gerá-los automaticamente](https://julialang.github.io/Pkg.jl/v1/environments/).
````

````{tabbed} R
No exemplo acima, especificamos que queremos usar R no nosso projeto incluindo uma data em `runtime.txt`.
A data indica à Binder qual CRAN snapshot para source R e pacotes.
Estes snapshots são originados do [RStudio Package Manager](https://packagemanager.rstudio.com) (RSPM).
No exemplo acima, o snapshot do RSPM datado de `r-2022-01-01` é usado e a versão de R e `readr` disponíveis nessa data e instalada.
Para o exemplo de fluxo de trabalho para funcionar corretamente, certifique-se de que você não informou uma data antes dessa data de exemplo.

Isto fornece alguns pacotes rudimentares de versão para usuários R, mas não é tão robusto quanto a versão fixada em um `requirements.txt` no Python.
Para uma versão mais robusta e específica fixando em R, dê uma olhada no [pacote `renv`](https://rstudio.github.io/renv/).
````

(z2b-step-5)=
## 5. Verifique o ambiente

🚦🚦🚦

````{tabbed} Python
1) Do painel de lançamento Selecione "Python 3" da seção de Observação para abrir um novo caderno de notas
2) Digite o seguinte em uma nova célula:

   ```python
   import numpy
   print(numpy.__version__)
   numpy.random. andn()
   ```

   ```{attention}
   Note os dois sublinhados de qualquer lado de `versão`!
   ```

3) Execute a célula para ver o número da versão e um número aleatório impresso

   - Pressione SHIFT+RETURN ou o botão "Executar" na barra de menu
````

````{tabbed} Julia
1) Do painel de lançamento selecione "Julia" da seção de Observações para abrir um novo caderno Julia
2) Digite o seguinte em uma nova célula:

   ```julia
   usando Pkg
   Pkg. tatus()
   ```

3) Execute a célula para ver o número de versão impresso

   - Pressione SHIFT+RETURN ou o botão "Executar" na barra de menu
````

````{tabbed} R
1) Do painel de lançamento selecione "R" da seção de Observações para abrir um novo Quadro de Notas de R
2) Insira o seguinte em uma nova célula:

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(sistema. ile("extdata/mtcars. sv", package = "readr"))
   ```

3) Execute a célula

    - Pressione SHIFT+RETURN ou o botão "Executar" na barra de menu
    Você deve ver o seguinte output:
      - o número de versão da versão instalada do `readr`
      - uma tibble do conteúdo dos `mtcars. sv` que é um arquivo csv incluído no pacote `readr`
````

```{attention}
Se você salvar este caderno, ele **não** será salvo no repositório do GitHub.
Empurrar as alterações de volta ao repositório do GitHub através do contêiner não é possível com o Binder.
**Qualquer alteração feita em arquivos dentro da Binder será perdida quando você fechar a janela do navegador.**
```

(z2b-step-6)=
## 6. Compartilhando seu trabalho

Binder é compartilhar seu trabalho com facilidade e há duas maneiras de fazê-lo:

- Compartilhe a URL **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** diretamente
- Visite **[https://mybinder. rg](https://mybinder.org)**, digite a URL do seu repositório e copie o trecho de texto Markdown ou ReStructured no seu `README. d` arquivo. Este trecho irá renderizar um emblema em que as pessoas podem clicar, que se parece com isto: ![Vestimenta](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) Adicione o **snippet** Markdown de **<https://mybinder.org>** ao arquivo `README.md` em seu repositório
   - A barra cinza que mostra um crachá no binder será exibida para revelar os trechos. Clique no ícone da área de transferência ao lado da caixa de marcada com "m" para copiar automaticamente o trecho de Markdown. 2) Clique no selo para ter certeza que funciona!

(z2b-step-7)=
## 7. Acessando dados no seu Binder

Outro tipo de dependência para projetos é **dados**. Existem diferentes maneiras de disponibilizar dados no seu Binder, dependendo do tamanho dos seus dados e das suas preferências para compartilhá-los.

(z2b-pequenos arquivos)=
### Arquivos públicos pequenos

A abordagem mais simples para arquivos de dados públicos pequenos é adicioná-los diretamente no seu repositório do GitHub. Eles são então diretamente encapsulados ao ambiente e versionados juntamente com seu código.

Isso é ideal para arquivos de até **10MB**.

(z2b-medios arquivos)=
### Arquivos públicos médios

Para acessar arquivos médios **de algumas 10s MB até algumas centenas de MB**, você pode adicionar um arquivo chamado `postBuild` ao seu repositório. Um arquivo `postBuild` é um script shell que é executado como parte da construção da imagem e só é executado quando uma nova imagem é construída, não toda vez que o Binder é lançado.

Veja [exemplo `postBuild` do Binder](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) para mais usos do `script postBuild`.

```{note}
Novas imagens são construídas somente quando a Binder vê um novo commit, não toda vez que você clica no link Binder.
Portanto, os dados só são baixados uma vez quando a imagem do Docker é construída, não toda vez que o Binder é iniciado.
```

(z2b-grandes)=
### Arquivos públicos grandes

Não é prático colocar arquivos grandes no seu repositório do GitHub ou incluí-los diretamente na imagem que a Binder compila. A melhor opção para arquivos grandes é usar uma biblioteca específica para o formato de dados para transmitir os dados enquanto você os usa ou baixá-los sob demanda como parte do seu código.

Por razões de segurança, o tráfego de saída do seu Binder é restrito apenas a conexões HTTP/S ou GitHub. Você não será capaz de usar sites FTP para obter dados em mybinder.org.

(z2b-arquivos privados)=
### Arquivos privados

Não há nenhuma maneira de acessar arquivos que não são públicos em mybinder.org. Você deve considerar todas as informações do seu Binder como públicas, ou seja, que:

- não deve haver senhas, tokens, chaves e assim por diante no seu repositório do GitHub;
- você não deve digitar senhas em um Binder executando em mybinder.org;
- você não deve carregar sua chave SSH privada ou token de API para um Binder.

Para apoiar o acesso a arquivos privados, Você precisa criar um deploy local do [BinderHub](https://binderhub.readthedocs.io) onde possa decidir o trading com segurança.

```{note}
Construir um BinderHub não é uma tarefa simples e geralmente é assumida por grupos de IT/RSE por razões em torno do gerenciamento de manutenção, segurança e governação.
No entanto, isso não significa que eles são os grupos _apenas_ de pessoas que deveriam/poderiam construir um BinderHub.
```

(z2b-step-8)=
## 8. Obtenha dados com `postBuild`

🚦🚦🚦

````{tabbed} Python
1) Vá para o seu repositório do GitHub e crie um arquivo chamado `postBuild`
2) Em `postBuild`, adicione uma única linha lendo: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` é um programa que recupera conteúdo de servidores web.
     Esta linha extrai o conteúdo do URL do bitly e o salva no nome do arquivo indicado pela bandeira '-O' (capital "O", não zero), neste caso `gapminder. sv`.
     A bandeira `-q` diz para `wget` fazer isso em silêncio, o que significa que não vai imprimir nada para o console.
3) Atualize seus requisitos `. xt` adicionando uma nova linha com `pandas` nele e outra linha com `matplotlib`
   - Esses pacotes não são necessários para baixar os dados, mas vamos usá-los para ler o arquivo CSV e fazer um gráfico
4) Clique no crachá binder no README para abrir o Binder

Uma vez que o Binder tenha iniciado, você deve ver um novo arquivo que não fazia parte do seu repositório quando você clicou na insígnia.

Agora visualize os dados criando um novo caderno (selecionando "Python 3" na seção Notebook) e execute o seguinte código em uma célula.

```python
%matplotlib inline

importar pandas

dados = pandas.read_csv("gapminder.csv", index_col="country")

anos = dados. olumns.str.strip("gdpPercap_") # Extrair ano dos últimos 4 caracteres de cada coluna
dada.colunas = anos. stype(int) # Converte valores do ano em inteiros, salvando resultados de volta para os dados do dataframe

. oc["Austrália"]. lot()
```

```{note}
Veja esta [lição de Software Carpentrada](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) para mais informações.
```
````

````{tabbed} Julia
1) Vá para o seu repositório do GitHub e crie um arquivo chamado `postBuild`
2) Em `postBuild`, adicione uma única linha lendo: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` é um programa que recupera conteúdo de servidores web.
     Esta linha extrai o conteúdo do URL do bitly e o salva no nome do arquivo indicado pela bandeira '-O' (capital "O", não zero), neste caso `gapminder. sv`.
     A bandeira `-q` diz para `wget` fazer isso em silêncio, o que significa que não vai imprimir nada para o console.
3) Atualize seu `Projeto. oml` adicionando novas dependências a `[deps]` com as seguintes linhas:

   ```julia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plots = "91a5bcdd-55d7-5caf-9e0b-520d859cae80"
   ``

   - Estes pacotes não são necessários para baixar, mas vamos usá-los para ler o arquivo CSV e fazer um encaixe
4) Clique no emblema binder no seu README para iniciar o Binder

Uma vez que o Binder tenha iniciado, você deve ver um novo arquivo que não fazia parte do seu repositório quando você clicou na insígnia.

Agora visualize os dados criando um novo caderno (selecionando "Julia" da seção Notebook) e execute o código a seguir em uma célula.

```julia
usando DataFrames
usando CSV
usando Plots

data = CSV.read("gapminder. sv", DataFrame)

# Extrair a linha correspondente à Austrália
aus_gdp = dados[dados[:, :country] . = "Austrália", :]
aus_gdp = Matrix(aus_gdp[:, :end])[:] # como vetor

# Extrair os anos como Ints dos nomes das colunas
anos = [x[end-3:end] para x em nomes(dados)[2:end]]
anos = análise. Int, anos)

# Plot
plot(anos, aus_gdp)
```
````

````{tabbed} R
1) Vá para o seu repositório do GitHub e crie um arquivo chamado `postBuild`
2) Em `postBuild`, adicione uma única linha lendo: `wget -q -O gapminder. sv http://bit.ly/2uh4s3g`
   - `wget` é um programa que recupera conteúdo de servidores web.
     Esta linha extrai o conteúdo do URL do bitly e o salva no nome do arquivo indicado pela bandeira '-O' (capital "O", não zero), neste caso `gapminder. sv`.
     A bandeira `-q` diz para `wget` fazer isso em silêncio, o que significa que não vai imprimir nada para o console.
3) Atualize seu arquivo `install.R` para instalar duas dependências adicionais, `"tidyr"` e `"ggplot2"`. Para fazer isso, forneça um vetor de personagem dos pacotes necessários para `install.packages()` em vez de uma única string de caractere. O comando de instalação agora deve ficar assim:

   ```r
   instale. ackages(c("readr", "tidyr", "ggplot2"))
   ```

    - Esses pacotes não são necessários para baixar os dados, mas vamos usá-los para ler o arquivo CSV, processe-o e faça um gráfico
4) Clique no ícone amargo em seu README para iniciar seu Binder

Uma vez que o Binder tiver iniciado, você deve ver um novo arquivo que não fazia parte do seu repositório quando você clicou na insígnia.

Agora visualize os dados criando um novo caderno (selecionando "R" da seção Observação) e executando o código a seguir em uma célula.

```r
library(readr)
library(tidyr)
library(ggplot2)

data <- read_csv("gapminder. sv") %>%
    pivo_mais tempo(-país,
                 nomes_to = "ano",
                 valores_para = "gdpPercap",
                 nomes_prefix = "gdpPercap_",
                 nomes_transformacao = list(ano = as. nteger))

dados[dados$country == "Austrália", ] %>%
    ggplot(a(x = ano, y = gdpPercap)) +
    geom_line()
```
````
(z2banotadores-além)=
## Mudando a interface
Ao longo deste tutorial, temos usado a interface do JupyterLab. Essa é a interface padrão para instâncias Binder recém-criadas. No entanto, esta não é a única interface disponível no mybinder.org, a visualização do Notebook clássico e o RStudio também estão disponíveis. (O ambiente R precisa ser instalado para que o RStudio esteja disponível.)
Você pode acessar as diferentes interfaces de maneiras diferentes. O jeito mais fácil é usar os botões no Lançador JupyterLab, mas você pode fornecer parâmetros de URL diretamente para abrir uma interface específica (ou arquivo! quando a instância Binder é iniciada. Agora vamos cobrir três maneiras que você pode manipular seu URL do Binder para navegar entre interfaces.
### de dentro a Binder Correndo
Aqui está a estrutura da URL dentro de uma instância da Binder em execução executando o JupyterLab:
> **https://<some-prefix>.mybinder.org/user/<a composite of your username, repo name and a hash>/lab**
You can change the interface from JupyterLab to either the Classic Notebook or RStudio by changing the `/lab` part of the URL to:
- **Classic Notebook:** `/tree`
- **RStudio:** `/rstudio`
### by changing the mybinder.org launch link
Here is the launch link you have been using throughout this tutorial:
> **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD**
You can access each interface by appending once of the following to the end of you URL:
- **Jupyter Notebook:** `?urlpath=tree`
- **JupyterLab:** `?urlpath=lab`
- **RStudio:** `?urlpath=rstudio`
### by using the mybinder.org form
You can also set the interface when constructing your launch link on the mybinder.org website (instead of editing the URL directly) as demonstrated in the below gif.

```{figure} https://user-images.githubusercontent.com/1448859/53651127-4dabe900-3c46-11e9-8684-2cfde840d4ce.gif
---
name: changing_interfaces
alt: A gif demonstrating how to change the interface of a Binder on the mybinder.org website
---
Use the "URL to open" option on the mybinder.org site to select your interface
```

(z2b-over-to-you)=
## Now over to you!

Now you've binderized (bound?) this demo repo, it's time to binderize the example script and data you brought along!

**Some useful links:**

- Choosing languages:
  - **<https://mybinder.readthedocs.io/en/latest/howto/languages.html>**
- Configuration files:
  - **<https://mybinder.readthedocs.io/en/latest/using/config_files.html>**
- Example Binder repos:
  - **<https://mybinder.readthedocs.io/en/latest/sample_repos.html>**
- Getting data:
  - With `wget`: **<https://github.com/binder-examples/getting-data>**
  - With `quilt`: **<https://github.com/binder-examples/data-quilt>**
  - From remote storage: **<https://github.com/binder-examples/remote_storage>**

**Advanced usage patterns:**

- Separating content from envorinment with `nbgitpuller` to reduced rebuilds:
  - **<https://discourse.jupyter.org/t/tip-speed-up-binder-launches-by-pulling-github-content-in-a-binder-link-with-nbgitpuller/922>**
- Tips for reducing the start-up time of your repository:
  - **<https://discourse.jupyter.org/t/how-to-reduce-mybinder-org-repository-startup-time/4956>**
