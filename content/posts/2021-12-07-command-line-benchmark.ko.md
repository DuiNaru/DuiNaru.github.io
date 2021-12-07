+++
categories = ["tips"]
tags = ["tips", "utils", "command"]
title = "명령어 실행 시간 측정해보기"
permalink = "2021-12-07-command-line-benchmark"
date = 2021-12-07T09:22:44.820Z
i18n = "ko"
+++
명령어의 실행 시간을 알아보는 방법을 몇 가지 적어보려고 합니다.

# time

리눅스의 기본 명령어입니다.

> **[time](https://linux.die.net/man/1/time)**
>
> time a simple command or give resource usage

해당 명령어를 실행시키고, 총 소요시간 / 유저영역 / 커널영역 의 실행 시간을 알려줍니다.

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

# bench

# hyperfine
