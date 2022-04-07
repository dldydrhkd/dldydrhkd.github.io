---
title: "The dependencies of some of the beans in the application context form a cycle:"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-06 20:43:00
categories: [Error]
tags: [spring]
math: true
mermaid: true
---

## Error

- rest template을 다음과 같이 사용했을 때 Error가 발생했다.
- service 인터페이스
    
    ```java
    package kr.pe.playdata.service;
    
    import java.util.concurrent.CompletableFuture;
    
    public interface RecommandService {
        /*
            관광지 추천 서비스 인터페이스
         */
    
        public CompletableFuture<String> recommand(String keywords);
    }
    ```
    
- service 구현
    
    ```java
    package kr.pe.playdata.service.impl;
    
    import kr.pe.playdata.service.RecommandService;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.scheduling.annotation.Async;
    import org.springframework.stereotype.Service;
    import org.springframework.util.LinkedMultiValueMap;
    import org.springframework.util.MultiValueMap;
    import org.springframework.web.client.RestTemplate;
    import java.util.concurrent.CompletableFuture;
    
    @Service
    public class RecommandServiceImpl implements RecommandService {
        /*
            관광지를 추천해주는 서비스 구현체
         */
    
        @Autowired
        private RestTemplate restTemplate;
    
    		@Bean
        public RestTemplate restTemplate(){
            return new RestTemplate();
        }
    
        @Async("asyncExecutor")
        public CompletableFuture<String> recommand(String keywords){
            String url = "http://127.0.0.1:5000/recommand";
            MultiValueMap<String, String> param = new LinkedMultiValueMap<String, String>();
            param.add("keywords",keywords);
            String sb = restTemplate.postForObject(url, param, String.class);
            return CompletableFuture.completedFuture(sb);
        }
    }
    ```
    
- Error 발생
    
    <img width="1151" alt="스크린샷_2022-04-06_오후_8 34 10" src="https://user-images.githubusercontent.com/48857296/162194933-a5b0f095-97d1-4e34-9e28-406b3def7714.png">
    
## Error 해결

- RestTemplate Config를 만들어 RestTemplate을 미리 Bean에 등록하였다.
    
    ```java
    package kr.pe.playdata.config;
    
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;
    import org.springframework.web.client.RestTemplate;
    
    @Configuration
    public class RestTemplateConfig {
        /*
            rest Config
         */
    
        @Bean
        public RestTemplate restTemplate(){
            return new RestTemplate();
        }
    }
    ```
    

## 참고 사이트

[Circular Dependency in Spring Boot](https://stackoverflow.com/questions/43706287/circular-dependency-in-spring-boot)
