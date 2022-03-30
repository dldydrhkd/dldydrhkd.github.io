---
title: 'Exception in thread "main" java.lang.NoSuchMethodError: com.google.common.base.Preconditions.checkArgument(ZLjava/lang/String;Ljava/lang/Object;)'
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-31 19:12:00
categories: [Error]
tags: [guava, hadoop, hive]
math: true
mermaid: true
---

## 에러 발생

- hive를 실행시켰더니 다음과 같은 에러가 발생하였다.
    
    <img width="977" alt="스크린샷_2022-01-31_오후_7 11 58" src="https://user-images.githubusercontent.com/48857296/160730274-b3b5dfef-048f-4312-b24f-83bcbfc04b0c.png">
    

## 에러 해결

- guava-19.0.jar를 guava-27.0-jre.jar로 바꾸었더니 해결되었다.
    
    ```bash
    rm /home/hadoop/hive-3.1.2/lib/guava-19.0.jar
    cp /home/hadoop/hadoop-3.2.2/share/hadoop/hdfs/lib/guava-27.0-jre.jar /home/hadoop/flume-1.9.0/lib/
    ```
    

## 참고 사이트

[java.lang.NoSuchMethodError: com.google.common.base.Preconditions.checkArgument](https://issues.apache.org/jira/browse/HIVE-22915)
