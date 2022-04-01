---
title: "Permission denied (publickey,gssapi-keyex,gssapi-with-mic)"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-01 18:10:00
categories: [Error]
tags: [hadoop, ssh]
math: true
mermaid: true
---

## 에러 발생

- 원격 접속을 하려고 하니 다음과 같은 에러가 발생했다.
    
    <img width="720" alt="스크린샷_2022-02-01_오후_6 10 01" src="https://user-images.githubusercontent.com/48857296/161253155-fcd35722-08db-4858-b1e1-b63f8f5d6862.png">

    

## 에러 해결

- 에러를 해결하기 위해 여러가지 의심을 해봐야한다.
- A→B로 원격 접속을 한다면 B의 /etc/ssh/sshd_config 파일에서 PasswordAuthentication을 yes로 바꿔주어야 한다.
    - 다음 명령어를 통해 sshd_config 파일을 편집해준다.
        
        ```bash
        vi /etc/ssh/sshd_config
        ```
        
        <img width="658" alt="스크린샷_2022-02-01_오후_6 14 42" src="https://user-images.githubusercontent.com/48857296/161253190-b0674196-5851-4d3d-a0f0-3c4d80cf3547.png">

        
    - 변경을 완료하였으면 다음 명령어로 sshd를 재시작해줘야한다.
        
        ```bash
        systemctl restart sshd
        ```
        
- B계정에서의 .ssh 파일의 권한을 700으로 바꿔준다.
    
    ```bash
    chmod 700 .ssh
    ```
    
- 만약 위와 같은 상황을 모두 했는데도 hadoop을 실행할 때 에러가 난다면 master의 workers에 slave를 제대로 추가했는지 확인해보자
    
    ```bash
    vi hadoop-3.2.2/etc/hadoop/workers
    ```
    
    <img width="719" alt="스크린샷_2022-02-01_오후_6 22 11" src="https://user-images.githubusercontent.com/48857296/161253245-995a2d5c-aad8-4e46-86ab-a2cf6872857b.png">
