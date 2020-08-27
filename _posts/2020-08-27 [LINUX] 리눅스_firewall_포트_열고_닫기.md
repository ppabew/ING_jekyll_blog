---
title: "[LINUX] 리눅스 firewall 포트 열고 닫기"
date: 2020-08-27 17:04:00
categories: jekyll update
---

포트 오픈(포트 열고 reload)
```
[root@localhost ~]$ firewall-cmd --permanent --zone=public --add-port=3000/tcp
[root@localhost ~]$ firewall-cmd --reload
```

포트 닫기(포트 닫고 reload)
```
[root@localhost ~]$ firewall-cmd --permanent --zone=public --remove-port=3000/tcp
[root@localhost ~]$ firewall-cmd --reload
```

정상적으로 열렸는지 확인하려면 telnet으로 확인하면된다.<br>
리액트 실행하고 해야함
```
[mw@centos7-frontend ~]$ telnet 192.168.0.20 3000
Trying 192.168.0.20...
Connected to 192.168.0.20.
```
<img src='/assets/assets/img/start_react.png'>