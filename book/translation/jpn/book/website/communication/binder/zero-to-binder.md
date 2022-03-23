(z2b)=
# Zero-to-Binder

この章では、最初からBinderプロジェクトを作成します。まずはGitHub上でリポジトリを作成し、mybinder.org上で起動します。 タスクを完了すると予想されるセクションには、3つの信号が表示されます🚦 絵文字。 いくつかのステップでは、Python、Julia、R のオプションが用意されています。お好みの言語のタブをクリックしてください。

```{admonition} Attributions
このチュートリアルは、Tim Headの_Zero-to-Binder_ワークショップに基づいています。ここで見つけることができます。 <http://bit.ly/zero-to-binder> and <http://bit.ly/zero-to-binder-rise>

アンナ・クリスタリとオリバー・ストリクソンに、RとJuliaのコンテンツを開発してくれてありがとうございます。 を選択します。
```

```{attention}
Binderはロードに時間がかかることがありますが、必ずしもBinderが起動しないことを意味するわけではありません。
「...ロードに時間がかかっている、しっかりと待ってください!」というメッセージが表示された場合、いつでもウィンドウを更新できます。
```

```{admonition} If you are using R...
R パスに従っている場合は、[`holepunch` パッケージ](https://github) を使用して別のステップを追加しました。 [rocker base image](https://github.com/rocker-org/rocker) を使用して環境を構築するom/karthik/holepunch) そして、最終的にはビルドと打ち上げがより速くなるはずです。
```

(z2b-reqs)=
## 要件

必要なもの:

- **Some code and some data.** The code should take less than **10 minutes to run**, and the data should be less than **10 MB**. これは、より大きなプロジェクトから1つのスクリプトを選択したり、データの一部を持参したりすることを意味します。 公開バインダーインスタンスを使用するので、コードとデータを公開することが **** できることは本当に重要です。
- **GitHubアカウントです。** まだお持ちでない場合はサインアップしてください: <https://github.com/join>

(z2b-step-1)=
## 1. Binderize にリポジトリを作成する

🚦🚦🚦

````{tabbed} Python
1) "my-first-binder" という新しいリポジトリを GitHub 上に作成します。
   - リポジトリが **public** であることを確認します。
   - README でリポジトリを初期化することを忘れないでください！
2) 最初の行に `print("Hello from Binder!")` を使い、ウェブインターフェースから `hello.py`という名前のファイルを作成し、`main`ブランチにコミットします。
````

````{tabbed} Julia
1) "my-first-binder" という新しいリポジトリを GitHub 上に作成します。
   - リポジトリが **public** であることを確認します。
   - README でリポジトリを初期化することを忘れないでください！
2) `hello という名前のファイルを作成します。 `println("Hello from Binder! ) 最初の行にある `main` ブランチにコミット
3) `Project というファイルを作成します。 oml` (WARNING: 大文字化は重要です!) には次の内容を含み、 `main` にコミットします。
   これは、Binder環境にJuliaをインストールします。

   ```jlia
   [compat]
   jlia = "1.3"
```
````

````{tabbed} R
1) "my-first-binder" という新しいリポジトリを GitHub 上に作成します。
   - リポジトリが **public** であることを確認します。
   - README でリポジトリを初期化することを忘れないでください！
2) `hello という名前のファイルを作成します。 `print("Hello from Binder! ) 最初の行にある `main` ブランチにコミット
3) `runtime という名前のファイルを作成します。 最初の行に`r-2022-01-01`を付けたxt`。
   この日付は [RStudio Package Manager](https://packagemanager.rstudio.com) でホストされている [CRAN](https://cran.r-project.org/) のスナップショットを表しています。
   このファイルを `main` ブランチにコミットします。

   ```{note}
   R では `holepunch::write_runtime()` を使用して `.binder/` ディレクトリに `runtime.txt` を作成することができます。
   ```
````
(z2b-public-repo)=
### なぜリポジトリは公開されなければならないのですか?
mybinder.orgは秘密のトークンを必要とするため、プライベートリポジトリにアクセスできません。 Binderチームは、mybinder.orgは公開サービスであり、技術的な概念の証明であるため、秘密のトークンを扱う責任を負わないことを選択します。 プライベートリポジトリにアクセスすることが必要な機能である場合は、独自の [BinderHub](https://binderhub.readthedocs.io) の構築を検討することをお勧めします。
(z2b-step-2)=
## 2. 最初のリポジトリを起動します！
🚦🚦🚦
1) **<https://mybinder.org>** 2) "GitHub リポジトリまたは URL" ボックスに、リポジトリの URL を入力します。 以下のようになります:
> **https://github.com/YOUR-USERNAME/my-first-binder** 3) As you type, the webpage generates a link in the "Copy the URL below..." box It should look like this: **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** 4) Copy it, open a new browser tab and visit that URL - You will see a "spinner" as Binder launches the repo
すべてがスムーズに動くと、JupyterLabインターフェースが表示されます。
(z2b-background-1)=
### バックグラウンドで何が起こっていますか? - パート1
待っている間は、BinderHub (Binder) のバックエンドは次のとおりです。
- GitHubからリポジトリを取得しています
- 内容を分析する
- リポジトリに基づいて Docker イメージを構築する
- クラウドで Docker イメージを起動する
- ブラウザ経由で接続しています
(z2b-step-3)=
## 3. スクリプトの実行
🚦🚦🚦

````{tabbed} Python
1. 起動パネルから「ターミナル」
2を選択します。 新しいターミナルウィンドウで、`python hello.py` と入力し、return を押します
````

````{tabbed} Julia
1. 起動パネルから「ターミナル」
2を選択します。 新しいターミナルウィンドウで、`julia hello.jl`と入力し、return を押します
````

````{tabbed} R
1. 起動パネルから「ターミナル」
2を選択します。 新しいターミナルウィンドウで、`Rscript -e 'source("hello.R")`と入力し、 return を押します
````

`Binderからこんにちは!` は端末に印刷する必要があります。

(z2b-step-4)=
## 4. 固定依存関係

始めるのは簡単でしたが、私たちの環境は素朴です - **依存関係** を追加しましょう!

🚦🚦🚦

````{tabbed} Python
1) リポジトリで `requirements.txt` というファイルを作成します。
2) `numpy==1.14.5` という行を追加します。
3) タイプミスを確認します！ `main` ブランチにコミットします。
4) 新しいタブで **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** をもう一度開きます。
````

````{tabbed} Julia
1) リポジトリで `Project を編集します。 oml`ファイル
2) 新しいブロックを追加します:

   ```julia
   [deps]
   CSV = "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
   ```

3) タイプを確認します! 次に`main`にコミットします。
4) 新しいタブで **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** をもう一度開く
````

````{tabbed} R
1) リポジトリに`install.R`というファイルを作成します。
2) `install.packages("readr")`
3) タイポを確認します！ Then commit to the `main` branch
4) Visit **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** again in a new tab

```{note}
If using `holepunch`, you can create an `install.R` file and automatically add the code to install all dependencies in your project using `holepunch::write_install()`.
```
````
今回は、大きな水平、灰色のバーにある「ログの構築」をクリックします。 これでビルドの進行状況を見ることができます。 ビルドが失敗した場合や、 __ がインストールされるべきと思うものが見つからない場合に便利です。

```{note}
Binderのビルドログは、赤いフォントで物事を印刷することがあります。 例えば、`pip`が最新ではないという警告（`pip`は定期的に更新されているため、しばしば古くなっています） 特にRを使っている場合は
これらの赤いメッセージは必ずしもあなたのビルドに問題があることを意味しないし、それが失敗することを意味します - それはちょうど不幸なフォントの色の選択です!
```

(z2b-background-2)=
### バックグラウンドで何が起こっていますか? - パート2

今回、BinderHub は追加した構成ファイルを読み取り、要求したパッケージの特定のバージョンをインストールします。

(z2b-dependencies)=
### 依存関係のピン留めの詳細

````{tabbed} Python
上記の例では、`numpy`のバージョンをピン留めするために2つの等号(`==`)を使用しました。
これは Binder に _具体的なバージョンをインストールするように指示します。

バージョン番号をピン留めするもう一つの方法は、(`>=`)以上のバージョンをインストールできるようにすることです。
これは多くの依存関係を持っていて、Binderがコードを壊したり変更したりする可能性のある以前のバージョンを避けながら、互いに競合しないような依存関係の構成を見つけることができる場合に便利です。

最後に バージョン番号(ライブラリ/パッケージの名前だけ)を指定することができず、Binderはそのパッケージの最新バージョンをインストールします。
````

````{tabbed} Julia
上記の例では、インストールしたいパッケージのバージョンに関連する「Project.toml」ファイルにハッシュをコピーしました。
完全な依存関係グラフの場合は、依存関係の依存関係を文書化する `Manifest.toml` ファイルも含める必要があります。
この2つのファイルの間で、Julia環境の正確な複製をインスタンス化することができます。

もちろん、環境が拡大し依存関係がより複雑になるにつれて、私たちは想像することができます。 これらのファイルを手作業で書くのは大変な課税になります!
実際には、手動では決して行わないということです。組み込みのパッケージマネージャ`Pkg`はformat@@0(https://jurialang.github.io/Pkg.jl/v1/environments/)があります。
````

````{tabbed} R
上記の例では、`runtime.txt`に日付を含めることで、プロジェクトでRを使用するように指定しました。
日付は、Binder に R とパッケージのソースへの CRAN スナップショットを伝えます。
これらのスナップショットは、[RStudio Package Manager](https://packager.rstudio.com) (RSPM) から取得されています。
上記の例では、`r-2022-01-01`の日付のRSPMスナップショットが使用されており、その日付で利用可能なRと`readr`のバージョンがインストールされています。
例のワークフローを正しく動作させるには、この例の日付よりも前に日付を入力しないことを確認してください。

これは R ユーザ向けの基本的なパッケージバージョンを提供しますが、Python の `requirements.txt` でのバージョンのピン留めほど堅牢ではありません。
より堅牢で特定のバージョンを R でピン留めするには、[`renv`](https://rstudio.github.io/renv/) パッケージをご覧ください。
````

(z2b-step-5)=
## 5. 環境を確認する

🚦🚦🚦

````{tabbed} Python
1) From the launch panel, select "Python 3" from the Notebook section to open a new notebook
2) Type the following into a new cell:

   ```python
   import numpy
   print(numpy.__version__)
   numpy.random.randn()
   ```

   ```{attention}
   Note the two underscores either side of `version`!
   ```

3) セルを実行してバージョン番号と出力された乱数を確認する

   - メニューバーのSHIFT+RETURNまたは「実行」ボタンを押します
````

````{tabbed} Julia
1) From the launch panel, select "Julia" from the Notebook section to open a new Julia notebook
2) Type the following into a new cell:

   ```julia
   using Pkg
   Pkg.status()
   ```

3) Run the cell to see the version number printed out

   - Press either SHIFT+RETURN or the "Run" button in the Menu bar
````

````{tabbed} R
1) From the launch panel, select "R" from the Notebook section to open a new R notebook
2) Type the following into a new cell:

   ```r
   library(readr)
   packageVersion("readr")
   read_csv(system.file("extdata/mtcars.csv", package = "readr"))
   ```

3) Run the cell

    - Press either SHIFT+RETURN or the "Run" button in the Menu bar
    You should see the following output:
      - the version number of the installed version of `readr`
      - a tibble of the contents of the `mtcars.csv` which is a csv file included in package `readr`
````

```{attention}
このノートブックを保存すると、**GitHubリポジトリには保存されません** 。
Binderでは、コンテナを通じてGitHubリポジトリに変更をプッシュすることはできません。
**ブラウザウィンドウを閉じると、Binder内のファイルに加えた変更は失われます。**
```

(z2b-step-6)=
## 6. あなたの仕事を共有

Binderはあなたの仕事を簡単に共有することであり、2つの方法があります。

- **https://mybinder.org/v2/gh/YOUR-USERNAME/my-first-binder/HEAD** URL を直接共有
- Visit **<https://mybinder.org>**, type in the URL of your repo and copy the Markdown or ReStructured Text snippet into your `README.md` file. このスニペットは、人々がクリックできるバッジをレンダリングします。これは次のようになります。 ![バインダー](https://mybinder.org/badge_logo.svg)

🚦🚦🚦

1) **Markdown** スニペットを追加する **<https://mybinder.org>** リポジトリの `README.md` ファイルに。
   - バインダーバッジを表示する灰色のバーが展開してスニペットを明らかにします。 マークダウンスニペットを自動的にコピーするには、「m」のマークが付いているボックスの横にあるクリップボードアイコンをクリックします。 2) バッジをクリックして動作を確認してください!

(z2b-step-7)=
## 7. Binderでデータにアクセスする

プロジェクトの別の種類の依存関係は、 **data** です。 Binderでデータを利用できるようにするには、データのサイズと共有するための好みに応じて、さまざまな方法があります。

(z2b-small files)=
### 小さな公開ファイル

小規模で公開されたデータファイルの最も簡単な方法は、GitHub リポジトリに直接追加することです。 それらは環境に直接カプセル化され、コードとともにバージョン管理されます。

これは、 **10MB** までのファイルに最適です。

(z2b-medium files)=
### 中程度の公開ファイル

To access medium files **from a few 10s MB up to a few hundred MB**, you can add a file called `postBuild` to your repo. `postBuild` ファイルはイメージ構築の一部として実行されるシェルスクリプトで、新しいイメージが構築されたときにのみ実行されます。 Binderが起動されるたびにではありません。

[postBuild `スクリプトのより多くの使用方法は` バインダーの](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) postBuild `の例` を参照してください。

```{note}
新しい画像は、Binderが新しいコミットを見つけたときにのみ作成され、Binderリンクをクリックするたびに作成されるわけではありません。
したがって、データは Docker イメージがビルドされると一度だけダウンロードされ、Binder が起動されるたびにダウンロードされるわけではありません。
```

(z2b-large files)=
### 大きな公開ファイル

大きなファイルを GitHub リポジトリに配置したり、Binder がビルドするイメージに直接含めたりすることは現実的ではありません。 大容量ファイルの最適な選択肢は、データ形式に固有のライブラリを使用して、使用しているデータをストリーミングしたり、コードの一部としてオンデマンドでダウンロードしたりすることです。

セキュリティ上の理由から、Binderの送信トラフィックはHTTP/SまたはGitHub接続のみに制限されています。 mybinder.org でデータを取得するために FTP サイトを使用することはできません。

(z2b-private-files)=
### プライベートファイル

mybinder.org から公開されていないファイルにアクセスする方法はありません。 Binder内のすべての情報をパブリックとみなす必要があります。つまり:

- GitHub リポジトリにパスワード、トークン、キーなどが記載されている必要はありません。
- mybinder.org上で実行されるBinderにパスワードを入力しないでください。
- SSH 鍵またはAPI トークンを実行中のBinderにアップロードしないでください。

プライベートファイルへのアクセスをサポートするために セキュリティトレードオフを自分で判断できる [BinderHub](https://binderhub.readthedocs.io) のローカルデプロイメントを作成する必要があります。

```{note}
BinderHubの構築は単純な作業ではなく、メンテナンス、セキュリティ、ガバナンスの管理上の理由から、通常はIT/RSEグループによって引き受けられます。
しかし、それはそれらがBinderHubを構築するべき/可能性のある人々の_唯一の_グループであると言うことではありません。
```

(z2b-step-8)=
## 8. `postBuild` でデータを取得する

🚦🚦🚦

````{tabbed} Python
1) Go to your GitHub repo and create a file called `postBuild`
2) In `postBuild`, add a single line reading: `wget -q -O gapminder.csv http://bit.ly/2uh4s3g`
   - `wget` is a program which retrieves content from web servers.
     この行は、ビットURLからコンテンツを抽出し、`-O`フラグ（大文字「O」）で示されるファイル名に保存します。 この場合はギャップマインダーです sv`。
     `-q` フラグは `wget` に静かに実行するように指示します。コンソールに何も出力しないことを意味します。
3) 要件を更新します。 xt`ファイルに`pandas`の行と`matplotlib`の新しい行を追加してください
   - これらのパッケージは、データをダウンロードする必要はありませんが、CSVファイルを読み、プロットを作成するためにそれらを使用します
4) あなたのREADMEのバインダーバッジをクリックして、バインダーを起動します。

バインダーが起動したら。 バッジをクリックしたときにレポに入っていなかった新しいファイルが表示されるはずです

新しいノートブック(ノートブックセクションから「Python 3」を選択)を作成してデータを可視化し、セル内で次のコードを実行します。

```python
%matplotlib inline

import pandas

data = pandas.read_csv("gapminder.csv", index_col="country")

years = data.columns.str.strip("gdpPercap_")  # Extract year from last 4 characters of each column name
data.columns = years.astype(int)              # Convert year values to integers, saving results back to dataframe

data.loc["Australia"].plot()
```

```{note}
See this [Software Carpentry lesson](https://swcarpentry.github.io/python-novice-gapminder/09-plotting/index.html) for more info.
```
````

````{tabbed} Julia
1) Go to your GitHub repo and create a file called `postBuild`
2) In `postBuild`, add a single line reading: `wget -q -O gapminder.csv http://bit.ly/2uh4s3g`
   - `wget` is a program which retrieves content from web servers.
     この行は、ビットURLからコンテンツを抽出し、`-O`フラグ（大文字「O」）で示されるファイル名に保存します。 この場合はギャップマインダーです sv`。
     `-q` フラグは `wget` に静かに実行するように指示します。コンソールに何も出力しないことを意味します。
3) `プロジェクトを更新します。 oml`ファイルに新しい依存関係を追加して`[deps]`に以下の行を追加します:

   ```julia
   DataFrames = "a93c6f00-e57d-5684-b7b6-d8193f3e46c0"
   Plot = "91a5bcddd-55d7-5caf-9e0b-520d859cae80"
   ```

   - これらのパッケージはデータをダウンロードする必要はありませんが、CSVファイルを読むためにそれらを使用します。
4) READMEのバインダーバッジをクリックして、バインダーを起動します。

バッジをクリックしたときにレポに入っていなかった新しいファイルが表示されるはずです

新しいノートブック(ノートブックセクションから「Julia」を選択)を作成してデータを可視化し、セル内で次のコードを実行します。

```julia
using DataFrames
using CSV
using Plots

data = CSV.read("gapminder.csv", DataFrame)

# Extract the row corresponding to Australia
aus_gdp = data[data[:, :country] .== "Australia", :]
aus_gdp = Matrix(aus_gdp[:,2:end])[:]  # as vector

# Extract the years as Ints from the column names
years = [x[end-3:end] for x in names(data)[2:end]]
years = parse.(Int, years)

# Plot
plot(years, aus_gdp)
```
````

````{tabbed} R
1) Go to your GitHub repo and create a file called `postBuild`
2) In `postBuild`, add a single line reading: `wget -q -O gapminder.csv http://bit.ly/2uh4s3g`
   - `wget` is a program which retrieves content from web servers.
     この行は、ビットURLからコンテンツを抽出し、`-O`フラグ（大文字「O」）で示されるファイル名に保存します。 この場合はギャップマインダーです sv`。
     `-q` フラグは `wget` に静かに実行するように指示します。コンソールに何も出力しないことを意味します。
3) `install.R`ファイルを更新して、`"tidyr"`と`"ggplot2"`の2つの依存関係をインストールします。 これを行うには、単一の文字列の代わりに `install.packages()` に必要なパッケージの文字ベクトルを指定します。 The installation command should now look like this:

   ```r
   install.packages(c("readr", "tidyr", "ggplot2"))
   ```

    - These packages aren't necessary to download the data but we will use them to read the CSV file, process it and make a plot
4) Click the binder badge in your README to launch your Binder

Once the Binder has launched, you should see a new file has appeared that was not part of your repo when you clicked the badge.

新しいノートブック(ノートブックセクションから「R」を選択)を作成し、セル内で次のコードを実行してデータを可視化します。

```r
library(readr)
library(tidyr)
library(ggplot2)

data <- read_csv("gapminder.csv") %>%
    pivot_longer(-country,
                 names_to = "year",
                 values_to = "gdpPercap",
                 names_prefix = "gdpPercap_",
                 names_transform = list(year = as.integer))

data[data$country == "Australia", ] %>%
    ggplot(aes(x = year, y = gdpPercap)) +
    geom_line()
```
````
(z2b-beyond-notebooks)=
## インターフェイスの変更
このチュートリアルではJupyterLabインターフェースを使用しています。 これは、新しく作成された Binder インスタンスのデフォルトのインターフェイスです。 しかし、これはmybinder.org で利用可能な唯一のインターフェイスではなく、Classic Notebook ビューと RStudio も利用できます。 (RStudioを利用するにはR環境をインストールする必要があります。
さまざまな方法で異なるインターフェイスにアクセスできます。 最も簡単な方法はJupyterLabランチャーのボタンを使うことです。 しかし、特定のインターフェイス(またはファイル)を直接開くためのURLパラメータを提供することができます。 Binderインスタンスが起動したとき。 Binder URLを操作してインターフェース間を移動する3つの方法について説明します。
### ランニングバインダーの内部から
JupyterLabを実行しているBinderインスタンス内のURLの構造は次のとおりです。
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
