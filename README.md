# **Natural language analysis library**
テキスト分析を行うためのライブラリです。**txtデータ版とcsvデータ版があります。**\
自然言語分析は、まず文書を語彙に分解し、その後 語彙数や語彙の出現傾向を可視化するなどして文書全体の訴えや傾向を把握します。\
このライブラリは、分析したい文書を保存した「ファイル」を読込むだけで、自動で前処理、以下の可視化を行うライブラリです。

- **nlplot**（自然言語可視化・分析ライブラリ）：ワードカウントグラフや共起ネットワーク等の可視化や分析を行います。文書の語彙の特徴や傾向を掴むことができます。
- **Word Cloud**：出現頻度が高い語を複数選び出し、その頻度に応じた大きさで図示します。文書に含まれる語がどれだけ重要かを示すTF-IDFというベクトル計算を行った結果によるWord Cloudも図示します。
- **センテンスのグループ分け①**：このライブラリは、テキストの語彙傾向でグループ分けを行います。[ベクトル計算：TF-IDF⇒クラスタリング：k-means]
- **センテンスのグループ分け②**：Doc2Vecという文章をベクトル化する技術によるテキストのグループ分けを行います。[ベクトル計算：Doc2Vec⇒クラスタリング：k-means]

***
## **前準備**
1. [**このサイト**](https://yag-ays.github.io)から「dbow300d：distributed bag of words (PV-DBOW)」（学習済モデル）をダウンロード。
2. 解凍後、jawiki.doc2vec.dbow300d📂を/content/drive/My Drive/NLPに保存。
- [**注意**] 学習済モデルは、Google DriveのMy Driveの下にNLPフォルダに保存する設定としています。NLPフォルダは作成してください。
***
## **実行手順**
1. メニューバーの「ランタイム」から「すべてのセルを実行」をクリック。
2. ライブラリインストール完了後、[ファイル選択]ボタンをクリックし、分析したい文書を指定する。
- [**注意**] テキストファイルは文字コードを「UTF-8」としてください。
3. Doc2Vecは、Google Driveに保存した学習済モデルをLoadします。初回実行時のみ表示されるURLをクリック⇒ログインし、表示されるコードをコピーし、セルに戻ってペーストする必要があります。
- [**注意**] Doc2Vecは処理に数分かかります。**時にクラッシュする**ことがあります。このような場合は**ランタイムを再起動してやり直し**てください。
***
## **このライブラリの使い方について**
- テキスト分析は文書量が多いと目を通すだけでも大変です。このライブラリで文書全体把握につながる語彙の特徴やセンテンスのグルーピングができますので、初手として活用することで効率化できます。
- Word Cloudで文書全体の訴えをながめた上、ライブラリが行ったグループ分け毎に個々のテキストに目を通すとよいと思います。
###**その他**
- グループ分けの数（クラスター数）は任意に設定できます。
- 満足度を数値化している場合、高い/低いランクを任意に設定できます。
- Word Cloudは、🍩型に変更することができます。
- **csvデータの表形式は以下としてください。**
- **カラム名は1列目を userID、2列目を comment（自由記述）、3列目を cs（満足度）としてください。3列目はなくても構いません。**

|userID|comment|cs|
|---|---|---|
|U001  |総合的には満足してますが、○○が細かく調整できたらもっと使いやすいと思います。|4  |
|U002  |○○ボタンが押しにくいです。|2  |
|U003  |特にありません。|3  |
|U004  |既存品と取付位置が合わないことがつらいです。|1  |
- [**注意**] k-means はアルゴリズム上、実行ごとに結果が変わることがあります。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/Natural_language_analysis_library_for_txt_v1.ipynb)
：txtデータ取込版：クリックでGoogle Colab起動。\
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/Natural_language_analysis_library_for_csv_v1.ipynb)
：csvデータ取込版：クリックでGoogle Colab起動。

---
## word2vec
Word2Vecは、当時Googleに在籍していた研究者であるトマス・ミコロフ氏らが考案。2層のニューラルネットワークのみで構成されるシンプルな構造により、大規模データによる分散表現学習が現実的な計算量で可能となり、分散表現での自然言語処理が飛躍的に進む等、自然言語処理に大きな技術的進展をもたらしたツール。
### 使用方法
以下は、学習済モデル→ 20170201.tar.bz2（解凍後のファイル名はentity_vector.model.bin） を利用し、類似語抽出、単語の加減算や複数単語の類似度、類似語の分布をグラフ表示させることができるようにしたもの。\
学習モデルをダウンロードし、GoogleDriveに保存（初回のみ）\
ランライム実行すると（最初のセルで）URLへのアクセスが要求されるのでアクセスしログイン。表示されるauthorization codeをコピーし、セルに表示される [ Enter your authorization code: ] の入力枠にコピペ⏎するだけです。
学習済モデルの保存フォルダの初期設定は「/content/drive/My Drive/NLP」です。変更の場合は任意に設定してください。
類似語、加算、減算、加減算等、文字を書き換え、セルを実行してください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/word2vec.ipynb)
：クリックでGoogle Colab起動します。

---
## fastText
fastTextは2016年にFacebookが公開した自然言語処理ライブラリ。単語をベクトル化することによって単語間の距離を計算し、コンピューター上での言葉の処理を可能にしたWord2Vec（Googleが開発）というライブラリがベース。100～300次元のベクトル生成が高速化され、さらにはテキストの分類も高速で行える特徴がある。
### 使用方法
以下は、この 学習済モデル：NEologd を利用し、類似語抽出、単語の加減算や複数単語の類似度、類似語の分布をグラフ表示させることができる。
学習モデルをダウンロードし、GoogleDriveに保存（初回のみ）\
実行すると（最初のセルで）URLへのアクセスが要求されるのでアクセスしログイン。表示されるauthorization codeをコピーし、セルに表示される [ Enter your authorization code: ] の入力枠にコピペ⏎するだけです。
学習済モデルの保存フォルダの初期設定は「/content/drive/My Drive/NLP」です。変更の場合は任意に設定してください。
類似語、加算、減算、加減算等、文字を書き換え、セルを実行してください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/fastText.ipynb)
：クリックでGoogle Colab起動します。

---
## pysummerization
pysummarizationは、自然言語処理とニューラルネットワーク言語モデルを用いたPythonのテキスト自動要約ライブラリ。
テキストクラスタリングによって元の文書やウェブスクレイピングされたテキストの主要なポイントをまとめた要約が作成できる。Accel-brain-baseを用いて、LSTMをベースとしたEncoder/Decoderを実装し、Sequence-to-Sequence（Seq2Seq）学習により要約精度を向上させているようだ。
### 使用方法
「ランタイム→すべてのセルを実行」し、ライブラリが読み込まれた後、表示される[ファイル選択] ボタンをクリックし、要約したいテキストファイル（.txt）指定するだけです。
要約結果に「原文書」「要約文書」「要約文書:SF」が表示されます。
SF（SimilarityFilter｜類似性フィルター）：文章内にある文字列に対し類似性の尺度を使って計算し冗長な文章を短くまとめる機能。カットオフ設定はスライドバーにて設定できます。※設定幅：0.05～0.5（Default=0.25, 0.05Step）\
**[注意]** テキストファイルは文字コードを「UTF-8」としてください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/pysummarization.ipynb)
：クリックでGoogle Colab起動します。

---
## pysummarization‗English‗string
pysummarizationは、自然言語処理とニューラルネットワーク言語モデルを用いたPythonのテキスト自動要約ライブラリ。
テキストクラスタリングによって元の文書やウェブスクレイピングされたテキストの主要なポイントをまとめた要約が作成できる。Accel-brain-baseを用いて、LSTMをベースとしたEncoder/Decoderを実装し、Sequence-to-Sequence（Seq2Seq）学習により要約精度を向上させているようだ。
### 使用方法
これは **英文要約専用** です。\
「ランタイム→すべてのセルを実行」し、ライブラリが読み込まれた後、表示される[ファイル選択] ボタンをクリックし、要約したいテキストファイル（.txt）指定するだけです。
要約後、result_summary.txt と result_summary.docx を生成します。（※docxファイルは DeepL翻訳サイトでドラックするだけで翻訳できます。）
要約結果に「原文書」「要約文書」「要約文書:SF」が表示されます。
SF（SimilarityFilter｜類似性フィルター）：文章内にある文字列に対し類似性の尺度を使って計算し冗長な文章を短くまとめる機能。カットオフ設定はスライドバーにて設定できます。※設定幅：0.05～0.5（Default=0.25, 0.05Step）
**[注意]** テキストファイルは文字コードを「UTF-8」としてください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/pysummarization‗English‗string.ipynb)
：クリックでGoogle Colab起動します。
