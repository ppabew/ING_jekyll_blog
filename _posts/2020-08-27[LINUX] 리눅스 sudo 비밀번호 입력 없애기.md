---
title: "[LINUX] service 작성법"
date: 2020-08-19 08:46:00
categories: jekyll update
---

아래 경로로 이동 후 아래 sudoers 파일을 다음과 같이 수정하면 된다.<br>
sudo vim /etc/sudoers
```
사용자명 ALL=NOPASSWD: ALL
```