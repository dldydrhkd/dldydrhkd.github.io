---
title: Failed to open file
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-11-24 19:04:00
categories: [Error]
tags: [MySQL]
math: true
mermaid: true
---

💡 외부 파일을 불러오려고 했는데 파일을 찾을 수 없다는 문구가 떴다.

# Error

- 외부 파일 `employees.sql` 을 불러오려고 했지만 찾을 수 없다고 에러가 나왔다.
    
    <img width="649" alt="스크린샷_2021-11-24_오후_7 09 39" src="https://user-images.githubusercontent.com/48857296/155893028-d4ac84db-4d2e-4577-a783-bf402756e330.png">
    
- 현재 경로가 잘못되었다고 판단하여 파일의 절대 경로로 실행해보았다.
    
    <img width="660" alt="스크린샷_2021-11-24_오후_7 12 58" src="https://user-images.githubusercontent.com/48857296/155893043-3be6e351-f6a2-4793-9509-4170f21a0d7d.png">
    
- 처음에 잘 되다가 dump 파일을 못 읽어오는 상태가 되었다.

# 해결방법

- MySQL을 처음에 실행하기 전에 디렉토리를 파일들이 있는 곳으로 이동시킨 후 MySQL을 실행했다.
    
    ```bash
    cd /Users/lyk/workspace/eclipse-workspace/DB01/employees
    
    mysql -u root -p
    
    source employees.sql
    ```
