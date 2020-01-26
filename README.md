# cmm

## Description

cmm (C--) is a C-like programming language.

The repository's cmm is extended a cmm of a book, 'Compiler' ([コンパイラ - コロナ社](http://www.slis.tsukuba.ac.jp/~nakai.hisashi.gt/Compiler/))

## Usage

The cmm compiler is compile from cmm to pl0i' assembly.

Run cmm with [cmm compiler](https://github.com/basd4g/cmm) and [pl0i](https://github.com/basd4g/pl0i).

```sh
# setup cmm
$ git clone https://github.com/basd4g/cmm.git
$ cd cmm
$ make

# compile ./sample/test (cmm) -> ./code.output (pl0i's assembly)
$ cat sample/test | ./cmm

# setup pl0i
$ git clone https://github.com/basd4g/pl0i.git
$ cd pl0i
$ make

# run code.output
$ ./pl0i ../code.output
```

## Extended syntax

1. conditions

&& ... AND
|| ... OR
! ... NOT

There is connect conditions.

## License

GPL ([License](./LICENSE))

## Author

The cmm is extended by [basd4g](https://github.com/basd4g).

The basis on this repository's cmm is developed by Hisashi Nakai. 

## Reference

- [コロナ社 コンパイラ](https://www.coronasha.co.jp/np/isbn/9784339027082/)
- [コンパイラ サポートページ - 中井央](http://www.slis.tsukuba.ac.jp/~nakai.hisashi.gt/Compiler/)


