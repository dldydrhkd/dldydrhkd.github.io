---
title: "JavaScript 객체"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-08-02 12:12:00
categories: [JavaScript]
tags: [JavaScript, 객체]
math: true
mermaid: true
---

## JS의 객체

- js에서 객체는 다음과 같이 코드를 작성할 수 있다.
    
    ```jsx
    const person = {
      name : '홍길동',
      age : 20
    };
    ```
    
- 객체의 값은 다음과 같이 불러 올 수 있다.
    
    ```jsx
    console.log(person.name);
    ```
    
- 한번 이 객체를 다른 함수에서 사용해보자
    
    ```jsx
    const person = {
        name : '홍길동',
        age : 20
      };
    
    function print(p1){
      const introduce = `제 이름은 ${p1.name}입니다.`;
      console.log(introduce);
    }
    
    print(person);
    ```
    

## 객체 비구조화 할당

- 객체화는 여러가지를 하나로 묶는 packing 느낌이였다면 객체 비구조화는 객체를 풀어버리는 것이다.
    
    ```jsx
    const person = {
        name : '홍길동',
        age : 20
      };
    
    function print(p1){
    	const {name, age} = p1;
      const introduce = `제 이름은 ${name}입니다.`;
      console.log(introduce);
    }
    
    print(person);
    ```
    
    > 객체에서 값들을 추출해서 새로운 상수로 선언해준다.
    > 
- parameter 자체를 객체 비구조화로 사용할 수도 있다.
    
    ```jsx
    const person = {
        name : '홍길동',
        age : 20
      };
    
    function print({name,age}){
      const introduce = `제 이름은 ${name}입니다.`;
      console.log(introduce);
    }
    
    print(person);
    ```
    

## 객체 안에 함수

- 객체 안에는 함수도 선언할 수 있다.
    
    ```jsx
    const person = {
        name : '홍길동',
        age : 20,
    		hi: function hi(){
    			console.log('내 이름은 ' + this.name + ' 이야');
    		}
      };
    person.hi();
    ```
    
    > this는 객체인 자기 자신을 뜻한다.
    > 
    
    > 주의할 점 : 함수를 function이 아닌 화살표 함수로 선언할 수 있지만 this가 들어가는 경우는 자기 자신을 참조할 수 없어 에러가 발생한다.
    > 

## Getter와 Setter

- 다음과 같이 getter와 setter함수를 만들 수 있다.
    
    ```jsx
    const numbers = {
      _a: 1,
      _b: 2,
      sum: 3,
      calculate() {
        console.log('calculate');
        this.sum = this._a + this._b;
      },
      get a() {
        return this._a;
      },
      get b() {
        return this._b;
      },
      set a(value) {
        console.log('a가 바뀝니다.');
        this._a = value;
        this.calculate();
      },
      set b(value) {
        console.log('b가 바뀝니다.');
        this._b = value;
        this.calculate();
      }
    };
    
    console.log(numbers.sum);   // 3 출력
    numbers.a = 5;              // _a를 5로 설정
    numbers.b = 7;              // _b를 7로 설정, sum 12로 설정
    numbers.a = 9;              // _a를 9로 설정, sum 16으로 설정
    console.log(numbers.sum);   // 16 출력
    ```
## 참고 사이트
[벨로퍼트와 함께하는 모던 자바스크립트](https://learnjs.vlpt.us/basics/06-object.html)
