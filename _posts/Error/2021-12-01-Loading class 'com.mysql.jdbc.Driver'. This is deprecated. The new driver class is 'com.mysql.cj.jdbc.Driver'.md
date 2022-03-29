---
title: Loading class 'com.mysql.jdbc.Driver'. This is deprecated. The new driver class is 'com.mysql.cj.jdbc.Driver'.
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-12-01 11:49:00
categories: [Error]
tags: [Java, JDBC, driver]
math: true
mermaid: true
---

💡 Loading class `'com.mysql.jdbc.Driver'`. This is deprecated. The new driver class is `'com.mysql.cj.jdbc.Driver'`.

## Deprecated

- 의미를 찾아봤더니 사용 되지 않는다는 뜻이다.

## Error 해석

- `'com.mysql.jdbc.Driver'`가 더 이상 쓰이지 않으니 `'com.mysql.cj.jdbc.Driver'`를 사용하라는 이야기이다.

## 해결

- 현재 내가 새용하고 있는 JDBC 커넥터 라이브러리는 mysql-connector-java-8.0.27.jar이다.
- `'com.mysql.jdbc.Driver'`를 `'com.mysql.cj.jdbc.Driver'`로 바꾸니 잘 연동이 된다.

## 참고 사이트

[[JAVA] Loading class 'com.mysql.jdbc.Driver'. This is deprecated. The new driver class is 'com.mysql.cj.jdbc.Driver'.](https://6161990src.tistory.com/76)
