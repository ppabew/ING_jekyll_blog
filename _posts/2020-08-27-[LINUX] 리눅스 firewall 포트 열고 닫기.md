---
title: "[LINUX] 리눅스 firewall 포트 열고 닫기"
date: 2020-08-27 17:04:00
categories: jekyll update
---

포트 오픈(포트 열고 reload)
```
[root@localhost ~]$ firewall-cmd --permanent --zone=public --add-port=80/tcp
[root@localhost ~]$ firewall-cmd --reload
```