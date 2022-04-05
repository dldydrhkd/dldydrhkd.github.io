---
title: "FileZilla 500 OOPS: chroot"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-21 18:32:00
categories: [Error]
tags: [filezilla]
math: true
mermaid: true
---
## Error

- vsftpd를 설치 후 FileZilla로 연결 요청을 보냈지만 다음과 같은 에러가 발생
    
    <img width="392" alt="스크린샷_2022-02-21_오후_8 42 08" src="https://user-images.githubusercontent.com/48857296/161662001-8d2e7034-c33c-41c2-b6d4-039148373ad9.png">
    

## Error 해결

- SELinux의 방화벽을 닫아준다.
    
    ```bash
    setenforce 0
    ```
    
    - SELinux를 임시로 비활성화 시킨다.
    - `getenforce` 를 하면 permissive 상태로 되어 있는 것을 볼 수 있다.
- SELinux 완전히 끄기
    - 권장 하지 않는 방법이지만 `/etc/sysconfig/selinux` 로 들어가 SELINUX를 disabled로 바꿔준다.
        
        ```bash
        vim /etc/sysconfig/selinux
        ```
        
        <img width="651" alt="스크린샷_2022-02-21_오후_9 08 26" src="https://user-images.githubusercontent.com/48857296/161662036-abf0660f-b1ea-43f9-959b-9b8ee05fe173.png">
        
        - 위 그림과 같이 SELINUX를 disabled로 바꿔준다.

## 참고 사이트

[Linux SELinux 끄기 및 임시 비활성화 방법 - JooTC](https://jootc.com/p/201806241113)
