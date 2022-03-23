(binder)=
# バインダー

この章では、Project Binderとmybinder.orgについて、研究を透過的かつインタラクティブに共有する手段として議論します。

(binder-share)=
## なぜ作品を共有する必要がありますか?

研究成果を共有するための動機は、 {ref}`rr-open` 章でより深く調べられています。

要するに、あなたの研究コードを共有することは、あなたがそれらに到達するために行ったプロセスを示すことによって、あなたが提示する結果にコンテキストを提供するのに役立ちます。 コードを共有することで 研究テーマを進展させるために車輪の再発明も避けています 以前のツールは 上に作られています

しかし、コードを共有する最大の障害は、次の節で見るように、パッケージをインストールし、計算環境を設定することです。 mybinder.orgなどのプラットフォームを介してあなたの作品を共有することによって:

- ソフトウェアパッケージをインストールすることはもはや困難ではありません
- 異なるオペレーティングシステムを使用している人は、ローカルマシンではなく、プラットフォーム上で計算が行われているため、同様の経験を持っています。
- 技術的な障壁が下がったので、あなたの作品はより広い聴衆に配布することができます

(binder-what)=
## Project Binderとは?

作業を共有することが重要な理由について話し合い、いくつかのJupyter Notebookをコラボレーションプラットフォーム上で解析コード付きで公開することにしました。 GitHubなどです

GitHub はコードを静的に共有するための素晴らしいプラットフォーム __ です。 リポジトリが公開されている場合は、誰でもメモ帳に移動して内容を読むことができます。 しかし、 _を実行する_ コードは、GitHubと同じように表示するよりもはるかに複雑です。 コードを実行するには、以下のような多くの相互依存する部品が必要です。

- コードそのもののコピー
- それを実行する適切なソフトウェアを
- 追加のパッケージは、コアソフトウェアの一部として出荷されていないことに依存します。
- 分析に必要な入力データ;
- それを実行するにはハードウェア(コンピュータ)も必要です。

すべての部品を取得する上で また、正しくインストールする必要がありますし、影響を受けたり、マシン上で実行されている可能性のある他のソフトウェアと競合することはありません。 それは多くの仕事です!

ブラウザー **の表示方法と同様に、**でコードを実行することができれば、どれくらい簡単でしょうか？ これがProject Binderが目指すものです。

Project Binder は以下のインフラストラクチャをユーザーに提供します。

- コードを実行するハードウェアもあります。通常はクラウドでホストされているサーバーですが、オンプレミスのハードウェアも可能です。
- 次のような計算環境があります
  - Approriateソフトウェアは
  - 追加のパッケージ依存関係があれば
  - 必要な入力データはすべて
  - そしてコード自体のコピー (ノートブックやスクリプト);
- 環境が実行されている場所へのURLを指定することで、あなたや共同作業者がコードを操作することができます。

Project Binderは可動部品のすべてをまとめており、計算作業をシンプルなインターフェイスに共有するのは困難です。 **mybinder.org** [で動作する**フリーで公開の**バージョンの](https://mybinder.org) があります。

以下の漫画はJuliette Takaによるもので、科学者がBinderを使って採用する可能性のあるワークフローを示しています。

```{figure} ../figures/binder-comic.png
---
name: binder_comic
alt: バインダー化されたプロジェクトを作成するためのステップのイラスト。
---
図のクレジット: [Juliette Taka, Logilab and the OpenDreamKit project](https://opendreamkit.org/2017/11/02/use-case-publishing-reproducible-notebooks/)
```

Project Binderとmybinder.orgについて詳しくは、 [About mybinder.org page](https://mybinder.readthedocs.io/en/latest/about/about.html) をご覧ください。

(binder-disam)=
### 曖昧さ

このセクションでは、明確にするためにここに概説するいくつかの関連する用語があります。

- **プロジェクトバインダー**: 共有可能でインタラクティブで再現可能な環境を作ることを可能にするオープンなコミュニティ。 このプロジェクトの技術的出力は {ref}`rrr-binderhub` です。
- **BinderHub**: Binderを生成するためのクラウドベースのインフラストラクチャ。 最も広く使用されているのは [mybinder.org](https://mybinder.org)で、プロジェクトバインダーチームによって管理されています。 これは、 [JupyterHub](https://z2jh.jupyter.org)を含むさまざまなオープンソースツールを基に構築されています。 ブラウザを介してユーザーにクラウドコンピューティングリソースを提供するために。 そして [ ](https://z2jh.jupyter.org) repo2docker [``](https://repo2docker.readthedocs.io/)、プロジェクトからdocker イメージを構築するためのものです。 オープンなプロジェクトなので、より専門的な構成をサポートできる他のBinderHubを作成することができます。 そのような設定の1つには、プライベートリポジトリを密接な共同作業者間で共有できるようにするための認証が含まれる可能性があります。
- **A Binder**: Webブラウザを介してクラウドで実行されている再現可能な計算環境内で閲覧し、対話できるプロジェクトの共有バージョン。 ( {ref}`rr-renv` 章で説明されているように) コンピューティング環境のインストールを自動化することにより、 Project Binderは、そのような環境を共有するオーバーヘッドをURLの共有に変換します。
- **[mybinder.org](https://mybinder.org)**: public and free BinderHub. 公開されているため、個人的または機密情報(パスワードなど)が必要な場合は使用しないでください。
- **Binderize**: プロジェクトからBinderを作るプロセス。

(binder-propriate)=
## mybinder.orgを使うのが適切なタイミングですか?

クラウドで無料の匿名サービスを維持することは、自発的な仕事の多くであり、多くのお金がかかります。 実行コストを少し削減するために、mybinder.orgは実行中の各Binderインスタンスに計算制限を設けています。 これらの制限は以下の通りです:

- 1 CPU と
- 1 GB のRAM。

したがって、mybinder.org は **** 機械学習ワークフローのエンドツーエンドの複製を実行する適切な場所ではありません。

そして、これがBinderのこの章が「コミュニケーションのためのガイド」に置かれた主な理由です。 これらの計算制限により、mybinder.orgはソフトウェアパッケージや研究分析のためのインタラクティブなデモンストレーションや学習リソースをホストすることに非常によく役立ちます。 このシナリオでは、Binderリンクをクリックした人々はおそらく何かを学びたいと思っています。 時間のかかるモデル訓練の過程で座ってもそれを達成することはできません 代わりに、 事前に訓練されたモデルや、自分のハードウェアでモデルを訓練する方法についての指示を提供し、インタラクティブなチュートリアルの残りの部分については、 __ に戻ってBinderに来ることができます。

それでは、いつmybinder.orgを使うのが適切なのでしょうか?

- 短い解析、チュートリアル、ブログなど、インタラクティブな方法で _何かを_ 伝えたい場合。 チェック [Achintya Rao blog powered by mybinder.org](https://blog.achintyarao.in/about/)!
- コードと関連するデータが公開されている場合
- 対話的に実行したいコードが多くのリソースや専門的なリソース(GPUなど)を必要としない場合。

(binder-faqs)=
## よくある質問

多くのよくある質問は、 [About mybinder.org page](https://mybinder.readthedocs.io/en/latest/about/about.html) で答えられます。

### リポジトリに変更を保存するにはどうすればいいですか?

残念ながら、できません。 少なくとも、実行中の Binder インスタンスのコマンドラインからではありません。

GitHubでも他のプラットフォームでも、ホストされているリポジトリに書き戻します は、そのリポジトリへの書き込みを許可するために、何らかの資格情報が必要になります。 そして、前述のように、マイバインダー。 rgは完全に公開されたサービスであり、実行中のBinderインスタンスに機密情報を提供してはいけません。

However, mybinder.org does run an add-on called [`jupyter-offlinenotebook`](https://github.com/manics/jupyter-offlinenotebook) which provides a download button to save your notebooks locally, _even if your browser has lost its connection with the cloud infrastructure that is providing the compute!_ This means you can save your progress locally, update your repository with your saved notebooks, and relaunch your Binder with the updated notebooks.

```{figure} ../figures/binder_notebook_banner.jpg
---
name: binder_notebook_banner
alt: パープルの長方形でハイライトされたダウンロードボタンを持つJupyter Notebook のコントロールパネルのスクリーンショット。
---
マイバインダー上で動作するJupyter Notebook の「ダウンロード」ボタンを使用します。 rgは、Binderインスタンスが計算リソースから切断された後でも、ノートブックをローカルに保存できます。
```

### mybinder.orgで同僚とコラボレーションするにはどうすればよいですか?

それは不可能ではありませんが、利用可能な他の「無料クラウドコンピューティング」サービスと比較して、この機能を開発する余地は間違いありません。

これに興味がある人 [この Discourse 投稿](https://discourse.jupyter.org/t/collaborating-on-one-binder-instance/407) と [`jupyterlab-link-share` リポジトリ](https://github.com/jtpio/jupyterlab-link-share) で詳細を確認できます。

### mybinder.orgはGoogle Colabとどう違いますか?

Google Colabは、最も人気のあるデータサイエンスソフトウェアパッケージの多くをプリインストールした「キッチンシンク」計算環境を提供します。 対照的に、mybinder.orgは起動された各リポジトリ、特に設定ファイルにリストされているパッケージをインストールするための特注の画像をビルドします。

### ここで `データを提供する`に接続できますか?

mybinder.org上のネットワーク接続は、セキュリティと乱用防止の目的でかなり制限されています。 以下の2つの基準を満たす限り、外部データプロバイダに接続できるはずだと言われています:

- HTTP/HTTPS 接続経由でアクセスできます
- データにアクセスするために資格情報は必要ありません

mybinder.orgは完全に公共サービスであり、資格情報などの機密情報をBinderインスタンスに提供する必要はありません。

(binder-segue)=
## Binder対応のプロジェクトを作成する方法

次の章には、 [Zero-to-Binderチュートリアル](z2b) が含まれており、GitHub上で最初のBinder-Ready プロジェクトを作成する方法について説明します。
