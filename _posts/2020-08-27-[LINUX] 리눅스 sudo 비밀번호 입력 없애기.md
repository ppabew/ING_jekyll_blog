---
title: "[LINUX] 리눅스 sudo 비밀번호 입력 없애기"
date: 2020-08-27 14:24:00
categories: jekyll update
---

아래 경로로 이동 후 아래 sudoers 파일을 다음과 같이 수정하면 된다.<br>
sudo vim /etc/sudoers<br>
주의할게 해당 명령어를 제일 아래로 입력해야한다.
```
사용자명 ALL=NOPASSWD: ALL
```

만약 위와 같이 했음에도 불구하고 동일한 문제가 있다면 해당 파일에서 다음을 추가하자<br>
```
%wheel         ALL = (ALL) NOPASSWD: ALL
```