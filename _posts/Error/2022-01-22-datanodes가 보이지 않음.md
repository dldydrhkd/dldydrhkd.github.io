---
title: datanodes가 보이지 않음
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-22 12:39:00
categories: [Error]
tags: [datanodes, hadoop, jps]
math: true
mermaid: true
---

# 에러 발생

- 하둡 실행 후 jps 명령어를 통해 실행중인 Java Virtual Machine에 올라간 프로세스를 볼 수 있는데 datanodes가 올라와 있지 않는다.

# 문제 해결

- 기존 데이터 폴더를 모두 삭제하고 다시 만든 후 `dhfs namenode -format` 을 하고 `./start-all.sh` 로 실행하면 datanodes가 다시 뜰 것이다.
