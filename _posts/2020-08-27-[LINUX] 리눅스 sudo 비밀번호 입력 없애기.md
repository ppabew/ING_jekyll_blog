---
title: "[LINUX] 리눅스 sudo 비밀번호 입력 없애기"
date: 2020-08-27 14:24:00
categories: jekyll update
---

아래 경로로 이동 후 아래 sudoers 파일을 다음과 같이 수정하면 된다.<br>
sudo vim /etc/sudoers
```
사용자명 ALL=NOPASSWD: ALL
```