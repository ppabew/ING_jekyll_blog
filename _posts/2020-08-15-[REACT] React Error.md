---
title: "[REACT] create-react-app, installation error (“command not found”) 에러"
date: 2020-08-15 08:26:28
categories: jekyll update
---

리액트 [REACT] create-react-app, installation error (“command not found”) 에러 발생시 다음과 같이 진행하면 문제를 해결할 수 있다.

```
$ npm config set prefix /usr/local
$ sudo npm install -g create-react-app
$ create-react-app my-app
```