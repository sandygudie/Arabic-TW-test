(ch-style-crossref)=

# セクションと章を相互参照する

チャプターやファイルに [Jupyter Book](https://jupyterbook.org/content/citations.html) で説明されているように、相互参照のスタイルを使用することをお勧めします。 各章の内容が異なります

Jupyter Bookでは、ラベルはコンテンツの一部や後で参照できるファイルにタグを追加する方法です。 これは、ファイルの相対パスや絶対パスを心配することなく、ブックの他の部分にラベルを挿入できるため、非常に便利です。

このドキュメントでは、さまざまなチャプターや本内の一部にラベルを使用する方法を説明するための例を提供しています。 また、本内のラベルの位置をその名前で識別できるようにするために、ラベルの命名規則 _The Turing Way_ を定義しました。

## Jupyter Book 中のラベル

セクションまたはチャプター/サブチャプターのラベルを追加するには、ラベル付けしたい要素の前に次のパターンの構文を使用します。

```
(my-label-name)=
# ラベル付けしたいもの
```

次の構文でファイル内のセクションのラベルにクロスリファレンスを挿入できます。

```
{ref}`my-label-name`

```

同様に、チャプターやサブチャプターを相互参照するためにラベルを使用することもできます。

詳細は以下の例をご覧ください。

### _Turing Way_ のラベル命名規則

ラベルには以下の命名基準を使用することをお勧めします。 これにより、 _The Turing Way_ の異なる著者と貢献者が、これらのラベルが作成されたファイルの場所を直感的に特定できるようになります。

異なるチャプターのラベルの命名規則:

```
(sectioninitials-filename)=
```

ここでは、最初のプレースホルダー `セクションイニシャル` を本内の異なるセクションのイニシャルに置き換え、2 番目のプレースホルダー `ファイル名` をラベルが作成されているファイル名に置き換える必要があります。

本の異なるガイドには、以下の `セクション頭文字を使用します。`:

- 再現可能な研究: `rr`
- プロジェクト設計: `pd`
- コラボレーション: `cl`
- 通信: `cm`
- 倫理的研究： `er`
- Community Handbook: `ch`

例えば、ガイド `再現可能な研究`には、 `概要` という章があります。 次のディレクティブを使用して、ヘッダの先頭にラベルを追加することで `rr-overview` という章のラベルを作成しました。

```
(rr-overview)=
# 概要
```

同様に、異なるサブチャプターについては、サブチャプターの名前に別のプレースホルダーを使用してラベル名を拡張することをお勧めします。 例えば、 `rr-overview-resources` は、「概要」章(概要-リソース)のサブチャプター「リソース」の「再現可能なリサーチ」(rr)のラベルです。 このラベルは対応するファイルの中にある以下のディレクティブを使って作成できます。

```
(sectioninitials-filename)=
# リソース
```

同じように、サブチャプター内の異なるセクションでは、ラベル名を別のプレースホルダーで拡張することをお勧めします。 これは、ラベルが作成されているセクションの短くても分かりやすい名前であるべき作者によって選択することができます。 例えば、 `rr-overview-resources-addmaterial` は、「追加材料」のセクションの「概要」章(概要-リソース)の「リソース」のサブチャプター「リソース」のガイド「再現可能なリサーチ」(rr)のラベルです。 このラベルは、次のディレクティブを使用して、推奨セクション名に対応するファイルに作成できます。

```
(sectioninitials-filename-section)=
## 追加素材
```

### 相互参照の例

**章とサブチャプターのセクションを相互参照するための例**

`book/website` ディレクトリにある"Reproductible Research"ガイドの章の例を使用します。

**_Case 1_**: When you cross-reference a section of the chapter within the same file _before_ a label has been created.

Taking the previous example of `rr-overview-resources-addmaterial`, we can use this label to cross-reference it in an earlier section within the same file using the following:

```
{ref}`rr-overview-resources-addmaterial`
```

これは次のようにオンライン本に表示されます: {ref}`rr-overview-resources-addmaterials`.

**_Case 2_**: When you cross-reference a section of the chapter within the same file _after_ a label has been created.

同じサブチャプター「リソース」では、「さらに読む」セクションのラベル `rr-overview-resources-reading` を作成しました。 以下を使用して、同じファイル内の後のセクションで相互参照できます。

```
{ref}`rr-overview-resources-reading`
```

次のようにあなたのチャプターに表示されます: {ref}`rr-overview-resources-reading`.

**_ケース 3_**: ラベルが作成される前後に別のファイル (章) の章のセクションを相互参照するとき。

「概要」章のサブ章「定義」では、「再現性の定義表」のセクションにラベル `rr-overview-definitions` を作成しました。

別の章または章で相互参照することができます。 この場合、以下を使用して、「概要」章のランディング(メイン)ページでそれを相互参照します。

```
{ref}`rr-overview-definitions`
```

次のようにあなたのチャプターに表示されます: {ref}`rr-overview-definitions`.

私たちは、同じ章(「概要」)内のサブチャプターについてこの例を説明しています。 同様の構文は本の他の章の相互参照にも使えます

**クロス参照章とサブチャプターの例**

**_ケース 4_**: ラベルが作成される前後に、別のファイル(チャプター/サブチャプター)の章またはサブチャプターを相互参照する。

例えば、「オープンリサーチ」章のランディングページでは、ラベル `rr-open` を作成しました。 「概要」章の異なる章「リソース」の章で、以下を使用して、「次に何を学ぶべきか?」セクションで相互参照することができます:

```
{ref}`rr-open`
```

次のようにあなたのチャプターに表示されます: {ref}`rr-open`.

私たちはこの例を本全体にわたって相互参照する章とサブチャプターのために示していますが、 同じ構文を使って、同じ章内のサブチャプターを相互参照することができます。

### 参照に代替タイトルを提供

上記のいずれかの参考文献について この例のようにラベルの前にタイトルを追加することで、参照中に代替タイトルを指定することができます。

```
{ref}`研究チャプター<rr-open>`
```

ここでは「オープンリサーチチャプター」の代替タイトルを付けます 次のようにあなたのファイルに表示されます: {ref}`オープンリサーチの章 <rr-open>`