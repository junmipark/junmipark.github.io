---
title:  "[자바 기초] 조건문 Conditional"
image: java.png
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 조건문, Conditional]
 
date: 2021-06-21
last_modified_at: 2022-01-22
---

# 조건문

### 조건문의 정의

- 프로그램의 수행 흐름을 바꾸는 역할을 하는 제어문의 종류 중 하나
- 조건에 따라 다른 문장이 수립되도록 함

### 조건문의 종류

- if문
- switch문

### if문

- 조건을 수식으로 표현하는데, 이를 조건식이라고 함
- 조건식의 결과 값이 참(true)이면 조건절 안의 내용을, 거짓(false)이면 조건 절 밖의 내용 수행
    
    ```java
    if(x%2==0){
    	System.out.println(x + "는 짝수 입니다.);
    } else {
    		System.out.println(x + "는 홀수 입니다.);
    }
    ```
    
- 실행되는 문장이 하나인 경우 중괄호를 생략하고 사용 가능
    
    ```java
    if(x>10)
    	System.out.println(x);
    ```
    
- 여러개의 If문을 중첩하여 사용할 수 있음
    
    ```java
    if(x>90){
    	grade = "A";
    	if(x>95)
    		grade += "+";
    }
    ```
    

### 다중 if - else 문

- If - else 문장이 연속하여 사용
    
    ```java
    if(num > 0){
    	System.out.println("양수입니다.");
    } else if(num == 0) {
    		System.out.println("0입니다.");
    } else { //num < 0
    	System.out.println("음수입니다.");
    }
    ```
    

### switch문

- 조건식 하나로 많은 경우의 수를 처리할 때 사용
- 조건식에는 실수 변수 또는 수식을 사용할 수 없음
- 조건식의 결과는 정수, 문자, 문자열
- 조건식의 결과 값과 일치하는 case문으로 이동
- default문은 일치하는 경우가 없을 때 수행

```java
int score, num;
char grade;
Scanner sc = new Scanner(System.in);

score = sc.nextInt();
num = score / 10;

switch(num) {
	case 10 :
	case 9 :
		grade = 'A';
		break;
	case 8 :
		grade = 'B';
		break;
	case 7 :
		grade = 'C';
		break;
	case 6 :
		grade = 'D';
		break;
	default : 
		grade = 'F';
		break;
}
```
