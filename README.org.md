# README.org

このリポジトリは書籍「コンパイラ」(コロナ社)に記載のプログラムを拡張したものである。
元プログラムに添付していたREADMEをこのページに記す。

## README.eng

```README.eng
cmm compiler

2004.08.19
Hisashi Nakai

This compiler has been developed for a lecture of compilers
at University of Library and Information Science, and
University of Tsukuba. 
The cmm (C minus minus) language has C-like syntax and
this compiler is implemented using Yacc and Lex

This compiler reads a source program via standard input
and emit the code for an interpreter which is altered
the pl0 machine in a compiler text book [1].
It emits the code to a file named "code.output".
You can execute the code with pl0i command,
which is the interpreter at the directory the code is in.

[1] Masataka Sassa : Programming Language Processors,
    Iwanami Shoten, 1988 (written in Japanese).
```

## README.euc

```README.euc
cmm コンパイラ 

2004.08.19
中井央

このコンパイラは図書館情報大学および筑波大学図書館情報専門学群
におけるコンパイラの授業の題材としたものである。
C 言語風の構文を持つ、簡易な言語 cmm (C minus minus のつもり)
を Yacc と Lex を使って実装したものである。

標準入力からソースプログラムを受け付け、
参考文献[1]に記載されている pl0 マシンを改造した
インタプリタ用のコードを出力する。
出力は code.output というファイルに行われる。
code.output が置かれているディレクトリで pl0i コマンド
を実行することで、出力されたコードの実行ができる。


[1] 佐々政孝 : プログラミング言語処理系, 岩波書店, 1988.
```

## CHANGES.jp

```CHANGES.jp
変更履歴(??)

2005.06.17

  関数呼び出しの生成規則のうち、引数部分の生成規則に問題が
  あったため、変更した。

2005.06.10

  入れ子のブロックによる、変数宣言に対応。
  具体的には st : body の生成規則で、ブロックに入る直前に
  ブロック要素の登録をし、ブロックから出た時点で局所の記号
  を削除するようにした。

2005.06.13

  C 言語型のブロックに対応するための変更。
  C 言語型のブロックの規則は次の通り。

    a) 関数(手続き)は入れ子に宣言できない。
    b) 変数宣言は入れ子に宣言できる。

  b) の素直な実装としては、ブロック内のブロックを無名(無引数)の
  関数呼び出しとして扱うことが考えられる。

    しかし、ここではそのような関数呼び出し形式にはせず、関数単位
  でメモリを確保することにした。
    ある関数の全体ブロックに子ブロックがない場合、必要なメモリの
  量はそのブロック内で宣言された変数の個数である。
    子ブロックが一つあって、その子ブロックがブロックを含まないと
  するとその関数内で必要とされるメモリ量は全体ブロックでの変数の
  数と内側ブロックにおける変数の数となる。
    一般には、子ブロックは並列に設置でき、入れ子にも設置できるの
  で、必要メモリ数は次のように求められる。
    関数 f0 における宣言された変数の数を m_0 とする。
    関数内に b_1 〜 b_n のブロックが設置されていたとすると、関数
  内における必要メモリ数は

      m_0 + max(b_1, ..., b_n) となる。

    ただし、b_i の値はそれぞれがブロックを含む場合、再帰的に計算
  されることになる。
```
