---
title: "스프링 부트 embedded port 변경 방법"
date: 2020-09-02 09:21:00
categories: jekyll update
---
스프링 부트의 embedded tomcat의 port를 아래와 같이 이미 사용하고 있는 문제가 발생하였다.<br>
그렇기 때문에 해당 tomcat의 port를 변경해줘야 한다.
<img src='/assets/img/20200902_092707.png'>

아래와 같이 포트 resources > application.properties에서 server port를 지정해준다.
<img src='/assets/img/20200902_093205.png'>

그럼 다음과 같이 정상 구동되는 것을 확인할 수 있다.
<img src='/assets/img/20200902_093217.png'>