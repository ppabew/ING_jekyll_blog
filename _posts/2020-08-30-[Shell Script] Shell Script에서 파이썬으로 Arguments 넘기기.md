---
title: "[Shell Script] Shell Script에서 파이썬으로 Arguments 넘기기"
date: 2020-08-30 22:15:00
categories: jekyll update
---
리눅스 Shell script에서 Python으로 arguments를 넘기는 다음과 같다.
```
jsonData="$(cat /home/python_study/python_log)"
echo $jsonData
python /home/python_study/python_study_03.py $jsonData
```
나의 경우 json data를 넘겼는데, 아무래도 shell에서는 space로 index 처리가 되다보니 파이썬에서 
받을 떄 아래와 같이 표시가 되었다.
json data로 전달하는 것에 대해 확인이 필요할 듯 싶다.
<img src='/assets/img/20200830_221925.png'>