在home/judge文件夹中：
```shell
├── backup				#用于某些文件的备份
├── data
│   └── 1000			#此文件夹表示题目序号，.in和.out存储判题的数据
├── etc/java0.policy	#功能位置
├── etc/judge.conf		#oj的配置文件
├── etc/judge.pid		#用于存储一个正在运行的进程的进程标识
├── log					#存放日志文件，OJ运行出错/调试时可能生成
├── run0				#存放自系统启动以来描述系统信息的文件,常见于daemon进程将自己的pid保存到这个目
├── src					#src是source的简称，存放源代码
├── .bash_logout		#离开控制台就清空控制台的输出
├── .bashrc				#"alias"自定义指令的别名
├── .profile			#设置权限（umask）为022。如果用户的私有可执行二进制（bin）存在，则设置bin路径来包含用户的
└── hustoj.tar.gz		#解压缩得到judge/src/等文件
```
在home/src/core文件夹(判题核心)中：

```shell
├── conf						#功能不知道,是config的缩写，属于配置文件
├── judge_client				#judge_client进程为实际判题程序，负责准备运行环境、数据，运行并监控目标程序的系统调用，采集运行指标，判断运行结果。当配置为启用抄袭检查时，judge_client将调用sim，判断相似性结果，并写回数据库或web端。
│   ├── getindocker.sh
│   ├── judge_client
│   ├── judge_client.cc
│   ├── judge_client.http
│   ├── judge_client.o
│   ├── loggedcalls.sh
│   ├── makefile
│   ├── ncalls.h
│   ├── okcalls32.h
│   ├── okcalls64.h
│   ├── okcalls_aarch64.h
│   ├── okcalls_arm.h
│   ├── okcalls.h
│   └── okcalls_mips.h
├── judged					#judged为服务进程，d即daemon。负责轮询数据库或web端，提取判题队列。
│   ├── judged
│   ├── judged.cc
│   ├── judged.http
│   ├── judged.o
│   ├── judgehub
│   ├── judgehub.cc
│   └── makefile
├── make.sh					#赋予/core执行权限,复制判题核心到可执行二进制/usr/bin,生成可执行文件
└── sim						#查重功能
    ├── sim_3_01
    │   ├── add_run.c
    │   ├── add_run.h
    │   ├── add_run.o
    │   ├── algollike.c
    │   ├── algollike.h
    │   ├── algollike.o
    │   ├── any_int.c
    │   ├── any_int.h
    │   ├── any_int.o
    │   ├── ChangeLog
    │   ├── clang.c
    │   ├── c++lang.l
    │   ├── clang.l
    │   ├── compare.c
    │   ├── compare.h
    │   ├── compare.o
    │   ├── debug.c
    │   ├── debug.h
    │   ├── debug.o
    │   ├── debug.par
    │   ├── fname.c
    │   ├── fname.h
    │   ├── fname.o
    │   ├── ForEachFile.c
    │   ├── ForEachFile.h
    │   ├── ForEachFile.o
    │   ├── hash.c
    │   ├── hash.h
    │   ├── hash.o
    │   ├── idf.c
    │   ├── idf.h
    │   ├── idf.o
    │   ├── javalang.l
    │   ├── Korean1.txt
    │   ├── Korean2.txt
    │   ├── lang.c
    │   ├── lang.h
    │   ├── language.c
    │   ├── language.h
    │   ├── lex.c
    │   ├── lex.h
    │   ├── lex.o
    │   ├── LICENSE.txt
    │   ├── lisplang.l
    │   ├── m2lang.l
    │   ├── Makefile
    │   ├── Malloc.c
    │   ├── Malloc.h
    │   ├── Malloc.o
    │   ├── miralang.l
    │   ├── newargs.c
    │   ├── newargs.h
    │   ├── newargs.o
    │   ├── option-i.inp
    │   ├── options.c
    │   ├── options.h
    │   ├── options.o
    │   ├── pascallang.l
    │   ├── pass1.c
    │   ├── pass1.h
    │   ├── pass1.o
    │   ├── pass2.c
    │   ├── pass2.h
    │   ├── pass2.o
    │   ├── pass3.c
    │   ├── pass3.h
    │   ├── pass3.o
    │   ├── percentages.c
    │   ├── percentages.h
    │   ├── percentages.o
    │   ├── README
    │   ├── runs.c
    │   ├── runs.h
    │   ├── runs.o
    │   ├── settings.par
    │   ├── sim.1
    │   ├── sim.c
    │   ├── sim.h
    │   ├── Similarity_Percentage_Computation.tex
    │   ├── sim.o
    │   ├── sim.pdf
    │   ├── sortlist.bdy
    │   ├── sortlist.spc
    │   ├── stream.c
    │   ├── stream.h
    │   ├── stream.o
    │   ├── system.par
    │   ├── TechnReport
    │   ├── text.c
    │   ├── text.h
    │   ├── textlang.l
    │   ├── text.o
    │   ├── ToDo
    │   ├── tokenarray.c
    │   ├── tokenarray.h
    │   ├── tokenarray.o
    │   ├── token.c
    │   ├── token.h
    │   ├── token.o
    │   ├── utf8test.c
    │   └── VERSION
    └── sim.sh
```

home/src/debian文件，编写了适应debian操作系统的代码，不常用，此处省略说明

home/src/docker文件，编写了适应docker的代码，不常用，此处省略说明

在home/src/install文件夹中

```shell
```



