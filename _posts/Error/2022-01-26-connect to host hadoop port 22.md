---
title: ssh: connect to host hadoop port 22: No route to host
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-26 00:35:00
categories: [Error]
tags: [ssh, linux]
math: true
mermaid: true
---

## 에러 발생

- `ssh: connect to host hadoop port 22: No route to host` 라는 에러 문구가 뜬다.

## 문제 해결

- 우선 `hostname -I` 명령어를 통해 내 ip 주소를 확인한다.
- 확인해본 결과 ip가 내가 원하는 ip로 고정되어 있지 않았다.
- ip를 고정하기 위해 `/etc/sysconfig/network-scripts/ifcfg-eth0` 을 다음과 같이 변경하였다.
    
    ```bash
    DEVICE=eth0
    HWADDR=08:00:27:21:95:5B
    TYPE=Ethernet
    ONBOOT=yes
    BOOTPROTO=static
    IPADDR=192.168.56.103
    NETMASK=255.255.255.0
    GATEWAY=192.168.56.1
    NETWORK=192.168.56.0
    ```
    
    - 알아보니 가상머신 설정에 있는 MAC address를 잘못 입력하여 일치하지 않아 에러가 났던 것이다.
