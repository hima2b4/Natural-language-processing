# Natural-language-processing

## nlplot+word_cloud+TF-IDF+word2vec
Word Cloud、nlplot（頻出ワードグラフや共起ネットワーク等の可視化や分析）、TF-IDF計算を実行します。
分析したい文書をテキストファイルに貼って読み込ませ、「ランタイム→すべてのセルを実行」するだけです。
前処理（改行, 空白等の処理）→形態素分析→各種視覚化は自動で行います。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/nlplot%2Bword_cloud%2BTF-IDF%2Bword2vec.ipynb)
：クリックでGoogle Colab起動します。
\
\
## word2vec
Word2Vecは、当時Googleに在籍していた研究者であるトマス・ミコロフ氏らが考案。2層のニューラルネットワークのみで構成されるシンプルな構造により、大規模データによる分散表現学習が現実的な計算量で可能となり、分散表現での自然言語処理が飛躍的に進む等、自然言語処理に大きな技術的進展をもたらしたツール。
***
以下は、学習済モデル→ 20170201.tar.bz2（解凍後のファイル名はentity_vector.model.bin） を利用し、類似語抽出、単語の加減算や複数単語の類似度、類似語の分布をグラフ表示させることができるようにしたもの。\
学習モデルをダウンロードし、GoogleDriveに保存（初回のみ）\
ランライム実行すると（最初のセルで）URLへのアクセスが要求されるのでアクセスしログイン。表示されるauthorization codeをコピーし、セルに表示される [ Enter your authorization code: ] の入力枠にコピペ⏎するだけです。
学習済モデルの保存フォルダの初期設定は「/content/drive/My Drive/NLP」です。変更の場合は任意に設定してください。
類似語、加算、減算、加減算等、文字を書き換え、セルを実行してください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/word2vec.ipynb)
：クリックでGoogle Colab起動します。
\
\
## fastText
fastTextは2016年にFacebookが公開した自然言語処理ライブラリ。単語をベクトル化することによって単語間の距離を計算し、コンピューター上での言葉の処理を可能にしたWord2Vec（Googleが開発）というライブラリがベース。100～300次元のベクトル生成が高速化され、さらにはテキストの分類も高速で行える特徴がある。
***
以下は、この 学習済モデル：NEologd を利用し、類似語抽出、単語の加減算や複数単語の類似度、類似語の分布をグラフ表示させることができる。
学習モデルをダウンロードし、GoogleDriveに保存（初回のみ）\
実行すると（最初のセルで）URLへのアクセスが要求されるのでアクセスしログイン。表示されるauthorization codeをコピーし、セルに表示される [ Enter your authorization code: ] の入力枠にコピペ⏎するだけです。
学習済モデルの保存フォルダの初期設定は「/content/drive/My Drive/NLP」です。変更の場合は任意に設定してください。
類似語、加算、減算、加減算等、文字を書き換え、セルを実行してください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/fastText.ipynb)
：クリックでGoogle Colab起動します。
\
\
## pysummerization
pysummarizationは、自然言語処理とニューラルネットワーク言語モデルを用いたPythonのテキスト自動要約ライブラリ。
テキストクラスタリングによって元の文書やウェブスクレイピングされたテキストの主要なポイントをまとめた要約が作成できる。Accel-brain-baseを用いて、LSTMをベースとしたEncoder/Decoderを実装し、Sequence-to-Sequence（Seq2Seq）学習により要約精度を向上させているようだ。
***
「ランタイム→すべてのセルを実行」し、ライブラリが読み込まれた後、表示される[ファイル選択] ボタンをクリックし、要約したいテキストファイル（.txt）指定するだけです。
要約結果に「原文書」「要約文書」「要約文書:SF」が表示されます。
SF（SimilarityFilter｜類似性フィルター）：文章内にある文字列に対し類似性の尺度を使って計算し冗長な文章を短くまとめる機能。カットオフ設定はスライドバーにて設定できます。※設定幅：0.05～0.5（Default=0.25, 0.05Step）\
**[注意]** テキストファイルは文字コードを「UTF-8」としてください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/pysummarization.ipynb)
：クリックでGoogle Colab起動します。
\
\
## pysummarization‗English‗string
pysummarizationは、自然言語処理とニューラルネットワーク言語モデルを用いたPythonのテキスト自動要約ライブラリ。
テキストクラスタリングによって元の文書やウェブスクレイピングされたテキストの主要なポイントをまとめた要約が作成できる。Accel-brain-baseを用いて、LSTMをベースとしたEncoder/Decoderを実装し、Sequence-to-Sequence（Seq2Seq）学習により要約精度を向上させているようだ。
***
これは **英文要約専用** です。\
「ランタイム→すべてのセルを実行」し、ライブラリが読み込まれた後、表示される[ファイル選択] ボタンをクリックし、要約したいテキストファイル（.txt）指定するだけです。
要約後、result_summary.txt と result_summary.docx を生成します。（※docxファイルは DeepL翻訳サイトでドラックするだけで翻訳できます。）
要約結果に「原文書」「要約文書」「要約文書:SF」が表示されます。
SF（SimilarityFilter｜類似性フィルター）：文章内にある文字列に対し類似性の尺度を使って計算し冗長な文章を短くまとめる機能。カットオフ設定はスライドバーにて設定できます。※設定幅：0.05～0.5（Default=0.25, 0.05Step）\
**[注意]** テキストファイルは文字コードを「UTF-8」としてください。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hima2b4/Natural-language-processing/blob/main/pysummarization‗English‗string.ipynb)
：クリックでGoogle Colab起動します。
