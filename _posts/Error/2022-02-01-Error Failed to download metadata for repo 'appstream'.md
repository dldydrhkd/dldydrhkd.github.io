---
title: "Error: Failed to download metadata for repo 'appstream': Cannot prepare internal mirrorlist: No URLs in mirrorlist"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-01 09:41:00
categories: [Error]
tags: [CentOS8]
math: true
mermaid: true
---

## Error

- CentOS8에서 wget을 설치하기 위해 `dnf install`을 사용했더니 다음과 같은 에러가 났다.
    
    <img width="983" alt="스크린샷_2022-02-01_오전_9 42 40" src="https://user-images.githubusercontent.com/48857296/161250256-67448082-2e87-498f-b698-c3df6b505510.png">
    
    - CentOS8의 서비스가 22년부터 서비스가 중단되고 CentOS Stream으로 전환된다.

## 해결 방법

1. CentOS7을 사용하자.
2. 기존에 Mirror site를 Vault로 전환하여 dnf를 사용한다.
    
    ```bash
    sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*
    ```
    
    - 당장은 해결이 가능하지만 해당 Reop는 더 이상 Package의 유지보수가 없으므로 보안에 취약하다.
    - 근본적인 해결을 위해서는 다른 배포판(ex. rocky linux 등)이나 CentOS 8 Stream, REHL 8로 전환해야 한다.

## CentOS 8 Stream 전환 방법

[Update CentOS 8 to CentOS Stream [in 3 Easy Steps]](https://linuxhandbook.com/update-to-centos-stream/)
