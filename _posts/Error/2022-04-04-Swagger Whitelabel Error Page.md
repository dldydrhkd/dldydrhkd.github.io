---
title: "Swagger Whitelabel Error Page"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-04 23:02:00
categories: [Error]
tags: [swagger, whitelabel]
math: true
mermaid: true
---
## Error

- swagger dependency를 다음과 같이 설정했다.
    
    ```xml
    <dependency>
    	<groupId>io.springfox</groupId>
    	<artifactId>springfox-swagger2</artifactId>
    	<version>3.0.0</version>
    </dependency>
    <dependency>
    	<groupId>io.springfox</groupId>
    	<artifactId>springfox-swagger-ui</artifactId>
    	<version>3.0.0</version>
    </dependency>
    <dependency>
    	<groupId>io.springfox</groupId>
    	<artifactId>springfox-boot-starter</artifactId>
    	<version>3.0.0</version>
    </dependency>
    ```
    
- swagger 설정을 제대로 했음에도 불구하고 다음과 같이 whitelabel page가 떴다.
    
    <img width="584" alt="스크린샷_2022-04-04_오후_11 06 15" src="https://user-images.githubusercontent.com/48857296/161670131-55f0fcd9-7eb5-440c-8ffd-94b2d29c6634.png">
    

## Error 해결

- 2.x 버전인 경우 [`http://localhost:8080/swagger-ui.html`](http://localhost:8080/swagger-ui.html)
- 3.x 버전인 경우 [`http://localhost:8080/swagger-ui/index.html`](http://localhost:8080/swagger-ui/index.html) 로 들어가야 한다.
