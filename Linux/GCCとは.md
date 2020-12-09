## GCCとは

### 概要
- GNU Compiler Collectionの略
- GNUプロジェクトが開発および配布している、さまざまなプログラミング言語のコンパイラ集

### 使ってみる
```
[root@cent8 tmp]# vi hello.c

#include <stdio.h>
  main(){
  printf("hello world.\n");
}

[root@cent8 tmp]# gcc hello.c
hello.c:2:3: 警告: 戻り値の型をデフォルトの ‘int’ にします [-Wimplicit-int]
   main(){
   ^~~~
[root@cent8 tmp]# ls
a.out  hello.c  ks-script-oghl0ckp  systemd-private-45a3dac695654c2c8f0ca3ee0299fdcc-chronyd.service-3pmtqI
[root@cent8 tmp]# ./a.out
hello world.
[root@cent8 tmp]#
```

### 参考
- https://qiita.com/chihiro/items/1725f9dbb51942534641
- https://linuc.org/study/knowledge/374/https://linuc.org/study/knowledge/374/
