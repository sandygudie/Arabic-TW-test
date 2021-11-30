(cm-citable-steps)=
# 研究対象を陽性にするためのステップ

著者が使用するデータとソフトウェアを引用しない理由はたくさんあります。 しかし最大のものの一つは明らかではないということです できるだけ簡単にするためにいくつかのステップに従うことによって、この障壁を減らすために長い道のりを行くことができます。

(cm-citable-steps-object)=
## 1. 研究オブジェクトを特定する

我々の研究対象のほとんどを共有し、他の研究者が再現し再利用できるようにすべきであることを強調したい。 したがって、最初のステップは、オンラインで共有するすべての研究コンポーネントを特定することです。 オープンリサーチを実践することは、データやソフトウェアの信用を得るために不可欠ではありません。 だがそれは他の人があなたの貢献を認める方法であなたの仕事を構築することをはるかに容易にします。 オープンな研究が同等の質と意義の非オープンな研究よりも多く引用される傾向を示すエビデンスの増加団体があります。

研究対象の引用の一環として、論文以外に研究対象を公開することが重要です。 例えば画像、データ、ソフトウェア、プロトコル、研究に関連付けられた方法angワークフローなど。

これを始める最善の方法は、どのような研究対象がどのようなものであるか、あるいは引用されるべきかの例を調べることです。 あなたの専門分野で一般的に参照される研究オブジェクトを見つけることは、以下の2つの目的を果たします。
1. ソフトウェア & データは引用できるものであることを示しています。
2. それは著者に、彼らが彼らのドキュメントに直接コピーして貼り付けることができる参照とフォーマットを与えます。
<!-- TODO: Cite relevant paper for this (Piwowar et al 2013?) -->

```{note}
{ref}`研究をオープンにする<rr-open>` と {ref}`研究FAIR<rr-rdm> ` の章で、さまざまなタイプの研究オブジェクトについて学ぶことができます。
```

(cm-citable-steps-publish)=
## 2. オンラインで作品を公開する

オンラインの出版物は、それらを引用するために使用される永続的な識別子に添付されます。 オンラインで公開されているすべてのものが一意の識別子を取得するわけではないことに注意することが重要ですが、以下で説明されているように、研究対象がオンラインでDOIで公開されていることが重要です。

(cm-citable-steps-doi)=
### DOIs

```{figure} ../../figures/DOI.jpg
---
name: doi
alt: この画像には材料のある3つのボックスが表示されます。 中央のメインボックスには、その上に「データセット」とラベル付けされた3枚のディスクが書かれています。 彼らの側の両方の箱はそれらの上にジャーナル記事を持っている。 画像の上部にある矢印は、これらの画像を「デジタルオブジェクト識別子」として示しています。 画像の下部に「永続的」、「ユニーク」、「信頼されている」というテキストがあります。
---
Digital Object IdentifierまたはDOIは永続的でユニークで信頼されています。 _Scriberiaによるチューリング方法_プロジェクトのイラスト。 CC-BY 4.0ライセンスの下で使用される。 DOI: [10.5281/zenodo.3332807](https://doi.org/10.5281/zenodo.3332807)
```

デジタルオブジェクトの固有の識別子や永続的なリンクは、より正式には [デジタルオブジェクト識別子またはDOI](https://en.wikipedia.org/wiki/Digital_object_identifier)と呼ばれます。 DOIを使用すると、他の人があなたのデータを引用することがはるかに簡単になります。 リンクが腐敗するリスクを減らし研究がどのように使用されているかを追跡できることを意味します

### DOIを提供するサーバー

論文とは無関係に、DOIを提供するサーバー上で異なる研究対象をオンラインで公開することができます。 Some of these servers are [Zenodo](https://zenodo.org/) and [FigShare](https://figshare.com/) (for different objects such as figures, presentations and reports), [Data Dryad](https://datadryad.org/stash) (for data), [Open Grants](https://www.ogrants.org/) (for grant proposals) and [Open Science Framework (OSF)](https://osf.io/) (for different components of an open research project).

データセットやソフトウェアパッケージを直接引用することは完全に可能であり、主要な出版社のほとんどがこれをスタイルガイドで許可しています。 しかし、時にはより従来の論文を引用するのに役立つことがあります。ここではソフトウェアやデータジャーナルが登場します。 これらの雑誌はメソッドジャーナルと似ています 重要な結果は含まれず再利用を可能にするのに十分な詳細なデータとソフトウェアを記述することに集中する傾向があります いくつかの例は次のとおりです。
- [Open Research Software](https://openresearchsoftware.metajnl.com/)
- [オープンソースソフトウェアの雑誌](https://joss.theoj.org/)

(cm-citable-steps-referencing)=
## 3. 機械読み取り可能な参照情報を追加

さらに一歩進むには、リサーチオブジェクトに関する情報を自分の好みの参照データベースにインポートすることができます。 If [BibTeX](https://en.wikipedia.org/wiki/BibTeX) is popular in your field for managing references, post a `.bib` file of *all* your outputs (not just your papers). [Endnote](https://endnote.com/) がより一般的な場合は、Endnote のエクスポートを利用できるようにします。 GitHub、GitLabなどをご利用の場合 プロジェクトからの異なる研究成果をどのように参照できるかについてのガイダンスを含む各リポジトリに `CITATION` ファイルを作成することを検討してください。

可能であれば、いくつかの形式を提供してください:あなたはこれらの非常に頻繁に更新する必要はありませんし、それは報酬を支払います。

```{note}
多くのオンラインツールは、さまざまな形式の研究対象の引用をエクスポートすることができます。
例えば、[https://www.citethisforme.com/](https://www.citethisforme.com/)を参照してください。
```