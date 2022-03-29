---
title: Failed to create the Java Virtual Machine
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-12-23 13:02:00
categories: [Error]
tags: [STS, Spring, VM]
math: true
mermaid: true
---

<aside>
💡 STS를 실행하였더니 Java VM을 생성할 수 없다고 떴다.

</aside>

## 해결 방법

- 응용 프로그램에 들어가 STS 아이콘을 우 클릭 후 패지지 내용 더보기를 눌러 STS.ini를 찾아 다음과 같이 코드를 -vmargs 위에 추가해줍니다.
    
    ```java
    -vm
    /Library/Java/JavaVirtualMachines/[자바 버전]/Contents/Home/bin/java
    ```
    
    <img width="725" alt="스크린샷_2021-12-23_오후_6 14 42" src="https://user-images.githubusercontent.com/48857296/160535564-5940d113-59ab-4111-97b1-e97fe6935f7a.png">
