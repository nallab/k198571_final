# 再現手順

基本的には実験1から4まで全て同様の手順である。また、中枢起源説モデルと末梢起源説モデルは両者とも同じように実行できる。ただし、実験4は中枢起源説モデルのみである。

## データセット構築

アンケート結果等任意の感情を得た時の状況や行動を表した短文から、それを最も象徴していると思わしき単語を抜き出す。中枢起源説に必要な「状況」と、末梢起源説に必要な「行動」は同じタイミングのものが望ましい。\
　単語を抜き出したら、その単語にかかる修飾語を抜き出す。実験1,2は2次元なので象徴する単語1つ、修飾語1つの2つ。3次元以上は修飾語の数を増やす。\
　抜き出してきた象徴する単語と修飾語をひとまとめにし、その時の感情タグを付与するとデータセットが1件できる。これを文章の数繰り返す。

## 辞書構築

データセットを元に中枢起源説、末梢起源説それぞれの多次元辞書を構築する。\
　1次元目のkeyは象徴する単語、その直下の2次元目には1次元目のkeyの修飾語を入れる。次元数が増える場合でも同じである。最終的なvalueはその単語の組み合わせに付与されていた感情タグとする。\
　注意点として、同じ単語が出てきた場合は同じkey内に登録すること。ただし、修飾語に関しては修飾先の単語が同じでない場合は分ける。\
　また、同じ単語の組み合わせに複数の感情タグが当てられていた場合、リスト形式で全て同じところに登録する。

## 入力

入力は、データセットのcsvを読み込ませるとプログラム内で自動的に全ての単語を組み合わせて入力とする。\
　具体的にいうと、抜き出してきた単語と修飾語をそれぞれ全組み合わせにして状況、反応として入力を行う。\
　ただし、実験3と4に関しては手動で単語のリストを作り、入力とする。

## 結果の取得

上記全ての準備が終わり、プログラムを実行すると結果が表示される。\
表示される内容としては

-   象徴する単語

-   修飾語

-   それぞれ何単語ずつあるか

-   組み合わせと出力された感情をまとめたdataframe型の表

-   該当なしが出力された数

-   複数該当ありが出力された数

が中枢起源説、末梢起源説の順で表示される。同時に、dataframe型の表はcsvファイルとしてプログラムのあるディレクトリに作成される。
