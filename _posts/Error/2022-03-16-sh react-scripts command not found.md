---
title: "sh: react-scripts: command not found"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-16 18:45:00
categories: [Error]
tags: [npm, react]
math: true
mermaid: true
---
## Error

- github에서 react가 있는 폴더를 pull을 하여 `npm start` 명령어를 실행하였지만 script가 없어 실행이 불가능하다고 다음과 같은 에러가 나왔다.
    
    ```bash
    > test@0.1.0 start
    > react-scripts start
    
    sh: react-scripts: command not found
    ```
    

## Error 해결

- 다음 명령어를 실행하여 node_modules를 만들어줌
    
    ```bash
    npm add react-scripts
    
    or
    
    npm install -save react-scripts
    ```
    

## 참고 사이트

[[오류] /bin/sh: react-scripts: command not found](https://lhwn.tistory.com/entry/%EC%98%A4%EB%A5%98-binsh-react-scripts-command-not-found)
