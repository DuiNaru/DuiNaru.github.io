+++
categories = ["tips"]
tags = ["tips", "utils", "command", "linux"]
title = "コマンド実行時間を測定する方法"
permalink = "2021-12-07-command-line-benchmark"
date = 2021-12-07T12:53:19.898Z
description = "コマンド実行時間を測定する方法について、いくつか書きたいと思います。"
i18n = "ja"

[[images]]
src = "https://www.dataquest.io/wp-content/uploads/2019/07/command-line-courses-dataquest-1000x520-1.gif"
alt = "bash image"
+++
# time

Linuxのコマンドに一つです。

> **[time](https://linux.die.net/man/1/time)**
>
> *time a simple command or give resource usage*

コマンドを実行させ、userとsysの領域での所要時間、合計所要時間を測定できます。

```
$ time sleep 1

real    0m1.002s
user    0m0.001s
sys     0m0.000s

$ time echo 'Hello World!'
Hello World!

real    0m0.000s
user    0m0.000s
sys     0m0.000s
```

簡単にプログラムの実行時間を調べる際に、便利です。

単純ということが限界ではありますが。

# bench

もうちょっと調べてみましょう。

> **[Gabriel439/bench](https://github.com/Gabriel439/bench)**
>
> *This project provides the bench command-line tool, which is a more powerful alternative to the time command. Use bench to benchmark a command using Haskell's criterion library.*

コマンドを数回実行できて、結果も詳しいです。

```
$ bench 'sleep 1'  # Don't forget to quote the command line
benchmarking sleep 1
time                 1.003 s    (1.002 s .. 1.003 s)
                     1.000 R²   (1.000 R² .. 1.000 R²)
mean                 1.003 s    (1.003 s .. 1.003 s)
std dev              92.92 μs   (0.0 s .. 101.8 μs)
variance introduced by outliers: 19% (moderately inflated)

$ bench true
benchmarking true
time                 410.3 μs   (382.3 μs .. 443.3 μs)
                     0.974 R²   (0.961 R² .. 0.987 R²)
mean                 420.7 μs   (406.8 μs .. 435.7 μs)
std dev              47.69 μs   (40.09 μs .. 57.91 μs)
variance introduced by outliers: 81% (severely inflated)
```

ファイルでの出力も可能です。

> HTML出力の例![HTML output](https://camo.githubusercontent.com/186e84512d02d553670d4eb9281106b74714b8a49251a13065a2f4ff7c7dd4ac/687474703a2f2f692e696d6775722e636f6d2f324d434b4263322e706e67)

# hyperfine

別の方法もあります。

> **[sharkdp/hyperfine](https://github.com/sharkdp/hyperfine)**
>
> *A command-line benchmarking tool.* ![demo](https://camo.githubusercontent.com/88a0cb35f42e02e28b0433d4b5e0029e52e723d8feb8df753e1ed06a5161db56/68747470733a2f2f692e696d6775722e636f6d2f7a31394f5978452e676966)

コマンドの数回実行、詳しい情報に加え、見やすい結果も得られます。