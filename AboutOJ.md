### **热门OJ：**

- 华中科技大学OJ php+shell （维护人数多，使用人数多）

- 青岛大学OJ  VUE+Python开发
- HydroOJ（首批接入洛谷开放平台，与洛谷关系密切）
- 洛谷OJ 闭源
- VJudge 闭源
- 牛客竞赛OJ 闭源
- 杭州电子科技大学OJ 闭源

由于洛谷的商业行为，洛谷不支持HUSTOJ爬取题目。

### 所需基础知识

PHP（重要）、Linux、Shell、HTML/CSS/JS、MySQL、YAML（了解）、apache（了解）

### 在home/judge文件夹中：

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
### 在home/src/core文件夹(判题核心)中：

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

### 在home/src/install文件夹中

```shell
├── A+B.xml
├── add_dns_to_docker.sh
├── ans2out
├── archive
│   ├── install-debian10-gitee.sh
│   ├── install-deepin15.9.sh
│   ├── install-raspbian8.sh
│   ├── install-raspbian9.sh
│   ├── install-ubuntu14.04.sh
│   ├── install-ubuntu14-bytgz.sh
│   ├── install-ubuntu16-bytgz.sh
│   ├── install-ubuntu16+.sh
│   ├── install-ubuntu18-bytgz.sh
│   ├── install-ubuntu18-gitee.sh
│   ├── install-ubuntu20-gitee.sh
│   └── install-vjudge.sh
├── autocpu.sh
├── backup+.sh
├── bak.sh
├── cleanproblem.sh
├── db.sql
├── default.conf
├── Dockerfile
├── docker.sh
├── fixdb.sh
├── fixext.sh
├── fixextxt.sh
├── fixing.sh
├── fixtxt.sh
├── gcc.sh
├── g++.sh
├── hustoj
├── install-centos7.sh
├── install-debian10+.sh
├── install-deepin20+.sh
├── install-fedora21-loongson.sh
├── install-judge.sh
├── install-raspbian10.sh
├── install+.sh
├── install.sh
├── install-ubuntu18.04.sh
├── install-ubuntu20.04.sh
├── install-ubuntu22.04-bt.sh
├── install-ubuntu22.04.gitee.sh
├── install-ubuntu22.04.sh
├── install-ubuntu-bt.sh
├── install-uos20.sh
├── java0.policy
├── jol.tar.gz
├── judge_client
├── judge.conf
├── judged
├── makeout.sh
├── moodle.sql
├── multiOJ.sh
├── my-ifconfig.te
├── my-phpfpm.te
├── mysql.sh
├── nginx.conf
├── oomsaver.sh
├── podman.sh
├── README
├── restore+.sh
├── restore.sh
├── rsync.sh
├── selinux.sh
├── sim.sh
├── sources.list.sh
├── stop.sh
├── uninstall.sh
├── update-by-download
├── update-hustoj
├── update.old.sql
├── update-sources-ubuntu.sh
└── update.sql
```

### 在home/src/web文件夹中

```shell
├── ace					#实现在线代码编辑器的功能
├── admin				#管理员页面
├── bbs					#网站的论坛功能
├── bsadmin
├── highlight			#通用代码高亮插件
├── image				#存储网站的背景、图标
├── include
├── kindeditor
├── lang				#语言文件，通过变量赋值的方式，翻译成不同的语言
│   ├── cn.php			#--简体中文
│   ├── cnt.php			#--繁体中文
│   ├── en.php			#--英文
│   ├── fa.php			#--法语
│   ├── ko.php			#--朝鲜/韩国
│   ├── ru.php			#--俄罗斯语言
│   ├── th.php			#--泰国语言
│   └── ug.php			#--乌干达语言
├── mergely				#文档对比和合并工具
├── swadmin
├── template			#此处存储着前端模板
├── upload
│   └── index.html		#此处为空，作用未知
├── 404.html			#404，找不到网页时显示，装饰性作用
├── active.php
├── balloon.php
├── balloon_view.php
├── bbs.php
├── bootstrap
├── category.php
├── ceinfo.php
├── comparesource.php
├── config.yaml
├── contest-check.php
├── contest-header.php
├── contest.php
├── contestrank2.php
├── contestrank3.php
├── contestrank4.php
├── contestrank5.php
├── contestrank-oi.php
├── contestrank.php
├── contestrank.xls.php
├── conteststatistics.php
├── csrf.php
├── discuss_func.inc.php
├── discuss.php
├── download.php
├── export_ac_code.php
├── export_contest_code.php
├── faqs.cn.php
├── faqs.php
├── favicon.ico
├── getsource.php
├── gpl-2.0.txt
├── index.php
├── install.php
├── loginpage.php
├── login.php
├── login_qq.php
├── login_renren.php
├── login_weibo.php
├── logout.php
├── lostpassword2.php
├── lostpassword.php
├── mail.php
├── modify_email.php
├── modify_info.php
├── modifypage.php
├── modify_password.php
├── modify.php
├── newpost.php
├── oj-header.php
├── online.php
├── post.php
├── printer.php
├── printer_view.php
├── problem-ajax.php
├── problem.php
├── problemset.php
├── problemstatus.php
├── ranklist.php
├── recent-contest.php
├── refresh-privilege.php
├── registerpage.php
├── register.php
├── reinfo.php
├── remote.php
├── saasinit.php
├── sae_app_wizard.xml		#新浪云应用服务，冗余功能
├── session.php
├── setlang.php
├── sharecodelist.php
├── sharecodepage.php
├── showsource2.php
├── showsource.php
├── status-ajax.php
├── status.php
├── submitpage.php
├── submit.php
├── superthread.php
├── suspect_list.php
├── test.lst
├── threadadmin.php
├── thread.php
├── userinfo.php
├── user_set_ip.php
├── vcode.php
└── viewnews.php
```
