---
title: "Error: (conn=335) Table 'CTLGS' already exists (state=42S01,code=1050)"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-31 19:27:00
categories: [Error]
tags: [MySQL, hadoop, hive]
math: true
mermaid: true
---

## 에러 발생

- mysql에 hive 스키마를 생성하려고 `schematool -initSchema -dbType mysql` 명령어를 사용하니 다음과 같은 에러가 나왔다.
    
    <img width="984" alt="스크린샷_2022-01-31_오후_7 27 24" src="https://user-images.githubusercontent.com/48857296/161248893-906055fb-d289-446b-a33d-019fcea87a66.png">
    

## 에러 해결

- 위 에러는 database의 이름이 중복되었기 때문에 발생한 에러이다.
- 다음과 같이 해결하였다.
    
    ```bash
    mysql -u root -p
    drop database hive;
    ```
