---
layout: post
title:  "FreeBSD 환경설정"
date:   2016-04-25 11:08:19 +0900
categories: FreeBSD
---

FreeBSD 10.x 설치 후 기본적인 환경설정 가이드

### sshd enable  
`/etc/rc.conf`에 다음 내용이  없으면 추가 한다.

```sh
sshd_enable="YES"
```

### ssh로 root login활성화  
`/etc/ssh/sshd_config`의 아래 라인의 comment를 제거하고 yes로 바꿔줌

```sh
PermitRootLogin yes
```

### root권한을 얻을 수 있는 계정 추가  
`/etc/group`의 아래 라인에 계정을 추가

```sh
wheel::0:root,[user_id]
```

### system update

```d
# freebsd-update fetch
# freebsd-update install
# reboot
```

### package install/update

```d
# pkg
# pkg update
```

### port update

```d
# portsnap fetch extract --> 처음 실행 할 경우
# portsnap fetch update
``` 

### 기본 package 설치

```d
# pkg install sudo
# pkg install gnuls
# pkg install vim-lite
# pkg install portmaster
```

### cshrc설정

`# vi ~/.cshrc`파일에 아래 내용 작성한다. 모든 계정에 공통으로 적용하려면 `/etc/csh.cshrc` 파일 수정함 

```sh
setenv LANG ko_KR.UTF-8
setenv LC_ALL ko_KR.UTF-8
alias cp cp -i
alias mv mv -i
alias vi vim
alias ls gnuls --color=always
```

