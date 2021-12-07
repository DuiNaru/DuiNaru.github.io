+++
categories = ["tips"]
tags = ["tips", "utils", "command", "linux"]
title = "명령어 실행 시간 측정해보기"
permalink = "2021-12-07-command-line-benchmark"
date = 2021-12-07T12:25:45.691Z
description = "명령어의 실행 시간을 알아보는 방법을 몇 가지 적어보려고 합니다"
i18n = "ko"
+++
# time

리눅스의 기본 명령어입니다.

> **[time](https://linux.die.net/man/1/time)**
>
> *time a simple command or give resource usage*

명령어를 실행시키고, 총 소요시간 / 유저영역 / 커널영역 의 실행 시간을 알려줍니다.

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

간단히 프로그램의 실행 시간을 알아보고자 할 때, 유용합니다.

단점이라면, 단하다는 것!

# bench

조금 더 자세히 알아봅시다.

> **[Gabriel439/bench](https://github.com/Gabriel439/bench)**
>
> *This project provides the bench command-line tool, which is a more powerful alternative to the time command. Use bench to benchmark a command using Haskell's criterion library.*

명령어를 반복 실행시킬 수 도 있고, 결과를 자세히 알아볼 수 도 있습니다.

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

파일 출력도 가능하지요.

> HTML출력 예시 ![HTML output](https://camo.githubusercontent.com/186e84512d02d553670d4eb9281106b74714b8a49251a13065a2f4ff7c7dd4ac/687474703a2f2f692e696d6775722e636f6d2f324d434b4263322e706e67)

# hyperfine

또 다른 방법으로 알아보는 것도 가능합니다.

> **[sharkdp/hyperfine](https://github.com/sharkdp/hyperfine)**
>
> *A command-line benchmarking tool.* ![demo](https://camo.githubusercontent.com/88a0cb35f42e02e28b0433d4b5e0029e52e723d8feb8df753e1ed06a5161db56/68747470733a2f2f692e696d6775722e636f6d2f7a31394f5978452e676966)

반복 실행, 파일 출력도 되면서 보기도 좋습니다.