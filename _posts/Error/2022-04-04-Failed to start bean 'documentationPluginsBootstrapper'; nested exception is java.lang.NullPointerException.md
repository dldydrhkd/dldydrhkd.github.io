---
title: "Failed to start bean 'documentationPluginsBootstrapper'; nested exception is java.lang.NullPointerException"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-04 22:45:00
categories: [Error]
tags: [spring boot, swagger]
math: true
mermaid: true
---
## Error

- swagger를 적용하기 위해 maven dependency에 다음과 같이 추가하였다.
    
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
    
- swagger config는 다음과 같이 작성하였다.
    
    ```java
    package kr.pe.playdata.config;
    
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;
    import springfox.documentation.annotations.ApiIgnore;
    import springfox.documentation.builders.ApiInfoBuilder;
    import springfox.documentation.builders.RequestHandlerSelectors;
    import springfox.documentation.service.ApiInfo;
    import springfox.documentation.spi.DocumentationType;
    import springfox.documentation.spring.web.plugins.Docket;
    import springfox.documentation.swagger2.annotations.EnableSwagger2;
    
    @Configuration
    public class SwaggerConfig {
    
        @Bean
        public Docket swaggerApi(){
            return new Docket(DocumentationType.SWAGGER_2).ignoredParameterTypes(ApiIgnore.class)
                    .apiInfo(swaggerInfo()).select()
                    .apis(RequestHandlerSelectors.basePackage("kr.pe.playdata.controller"))
                    .build()
                    .useDefaultResponseMessages(false);
        }
    
        private ApiInfo swaggerInfo() {
            return new ApiInfoBuilder().title("API Documentation")
                    .description("제주들려섬 API 문서 ")
                    .license("license : 제주들렸섬").licenseUrl("http://playdata.io/").build();
        }
    }
    ```
    
- 빌드를 하니 다음과 같은 에러가 나왔다.
    
    <img width="1409" alt="스크린샷_2022-04-04_오후_10 53 14" src="https://user-images.githubusercontent.com/48857296/161669726-a7ef0864-49fc-4622-af59-fd9b63cda48b.png">
    

## Error 해결

- Spring boot 2.6버전 이후에 spring.mvc.pathmatch.matching-strategy 값이 ant_apth_matcher에서 path_pattern_parser로 변경되면서 몇몇 라이브러리(swagger포함)에 오류가 발생한다고 한다.
- application.properties에 다음과 같이 추가를 한다.
    
    ```java
    spring.mvc.pathmatch.matching-strategy = ANT_PATH_MATCHER
    ```
    
- application.yml이라면 다음과 같이 추가해준다.
    
    ```java
    spring:
    
      mvc:
    
        pathmatch:
    
          matching-strategy: ant_path_matcher
    ```
    
- spring-boot-starter-parent의 버전을 2.5.x 버전으로 낮추는 방법도 있다.

## 참고 사이트

[swagger 연동을 할려고 하는데 에러가 발생합니다 - 인프런 | 질문 & 답변](https://www.inflearn.com/questions/230160)

[](https://velog.io/@pkw3136/Failed-to-start-bean-documentationPluginsBootstrapper-in-spring-data-rest)
