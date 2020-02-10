# cmm

## Description

cmm (C--) is a C-like programming language.

The cmm is extended a cmm of a book, 'Compiler' ([コンパイラ - コロナ社](http://www.slis.tsukuba.ac.jp/~nakai.hisashi.gt/Compiler/))

## Usage

The cmm compiler is compile from cmm to pl0i' assembly.

```sh
# setup cmm
$ make

# setup pl0i
$ curl http://www.slis.tsukuba.ac.jp/~nakai.hisashi.gt/Compiler/Compiler.tar.gz > Compiler.tar.gz
$ tar -zxvf Compiler.tar.gz 
$ cd Compiler/pl0i_src/
$ make
$ cd ../../
$ mv Compiler/pl0i_src/pl0i ./
$ rm -rf Compiler Compiler.tar.gz 

# compile ./sample/test (cmm) -> ./code.output (pl0i's assembly)
$ cat sample/test | ./cmm

# run code.output
$ ./pl0i
```

## Sample programs

```sh
cat extended_sample/cond.cmm | ./cmm && ./pl0i
cat extended_sample/exp.cmm | ./cmm && ./pl0i
cat extended_sample/for.cmm | ./cmm && ./pl0i
cat extended_sample/mod.cmm | ./cmm && ./pl0i
cat extended_sample/while.cmm | ./cmm && ./pl0i
```

## Extended syntax

1. conditions

- `&&` ... AND
- `||` ... OR
- `!` ... NOT

There is connect conditions.

```cmm
main {
  var i;
  read i;
  if ! i>0 then
    write 0;
  else
    write 1;
  writeln;
}
```

2. for

for &lt;initial statement&gt; &lt;conditions&gt;; &lt;increment statement&gt; do &lt;statement&gt;

```cmm
main {
  var i;
  for i:=0; i<10; i:=i+1; do 
    write i;
  writeln;
}
```

3. mod

```cmm
main {
  var i;
  read i;
  write i % 3;
  writeln;
}
```

4. exp

```
main {
  var i;
  read i;
  write i ^ 3;
  writeln;
}
```

## License

GPL ([License](./LICENSE))

## Author

The cmm is extended by Keisuke, Nakayama.

The basis on this cmm is developed by Hisashi Nakai. 

## Reference

- [コロナ社 コンパイラ](https://www.coronasha.co.jp/np/isbn/9784339027082/)
- [コンパイラ サポートページ - 中井央](http://www.slis.tsukuba.ac.jp/~nakai.hisashi.gt/Compiler/)

