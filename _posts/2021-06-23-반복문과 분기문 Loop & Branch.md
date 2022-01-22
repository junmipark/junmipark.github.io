---
title:  "[자바 기초] 반복문과 분기문 Loop & Branch"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 반복문, Loop, 분기문, Branch]
 
date: 2021-06-23
last_modified_at: 2022-01-22
---

# 반복문 Loop

### 반복문의 정의

- 프로그램의 수행 흐름을 바꾸는 역할을 하는 제어문 중 하나
- 특정 문장들을 반복해서 수행하도록 함

### 반복문의 종류

- for문
- while문

### for문

```java
for (초기식; 조건식; 증감식) {
	수행될 문장;
}
```

### while문

```java
while (조건식) {
	수행될 문장;
	[증감식 or 분기문];
}
```

```java
do {
	수행될 문장;
	[증감식 or 분기문];
} while (조건식);
```

<aside>
💡 do ~ while은 조건문이 true가 아니더라도 무조건 한 번 이상 수행

</aside>

### 중첩 반복문

```java
for(초기값1; 조건식1; 증감식1) {
	수행될 문장1;
	for(초기값2; 조건식2; 증감식2){
			수행될 문장2;
			break;
	}
	수행될 문장3;
	[break;]
}
```

# 분기문 Branch

### 분기문 종류

- break
- continue

### break

- 반복문에서 자신(break)이 포함된 가장 가까운 반복문을 빠져나가는 구문

### continue

- 반복문 내에서만 사용 가능
- 반복문 실행 시 continue 아래 구문은 실행하지 않고 반복문 재실행
- for문은 증감식으로 이동, while문은 조건식으로 이동
- 전체 반복 중에 특정 조건을 만족하는 경우를 제외하고자 할 때 유용

---

# 실습 예제

### 반복문 예제

- 문제
    
    <반복문실습>
    
    - 실행용 클래스 : com.silsub1.main.Main.java
    - 기능제공용 클래스 : com.silsub1.example.ForWhile.java
    ** 키보드 입력은 Scanner 클래스 사용할 것 **
    => Field 로 선언
        - * 기타 필요한 외부 클래스가 있다면
        import 하여 사용할 것 **
    
    [문제 1]
    : 정수를 하나 입력받아, 그 수가 양수일 때만
    입력된 수를 줄 수로 적용하여 다음과 같이 출력되게 함
    
    - if문과 이중 for문 사용
    - 메소드명 : public void printStar1(){}
    ex>
    정수 하나 입력 : 5
    1
    *2
    **3
    ***4
    ****5
    정수 하나 입력 : -5
    양수가 아닙니다.
    
    [문제 2]
    : 정수를 하나 입력받아, 양수일 때와 0일때 음수일 때 각각
    아래와 같이 출력되게 함.
    
    - if문과 for문 사용
    - 메소드명 : public void printStar2(){}
    ex>
    정수 입력 : 5
    *
    **
    ***
        
        ****
        
        *****
        ================
        정수 입력 : -5
        *****
        ****
        
        ***
        
        **
        *
        ================
        정수 입력 : 0
        출력 기능이 없습니다.
        
    
    [문제 3]
    : 문자열 값을 입력받고, 그 다음 문자 하나를 입력받아,
    문자열 값 안에 입력문자가 몇 개 존재하는지 그 갯수를 출력함
    단, 영문자만 입력받도록 함.
    
    - 메소드명 : public void countInputCharacter(){}
    ex>
    문자열 입력 : application
    문자 입력 : p
    포함된 갯수 : 2 개
    문자열 입력 : apple_test123
    영문자가 아닙니다.

```java
package com.silsub1.example;

import java.util.Scanner;

public class ForWhile {
	Scanner sc = new Scanner(System.in);
	
	public void printStar1() {
		System.out.print("정수 하나 입력 : ");
		int num = sc.nextInt();
		
		if(num<0)
			System.out.println("양수가 아닙니다.");
		else {
			for(int i = 1; i<=num; i++) {
				for(int j=1; j<=i; j++) {
					if(j==i) System.out.print(j);
					else System.out.print("*");
				}
				System.out.println();
			}
		}
	}
	
	public void printStar2() {
		System.out.print("정수 하나 입력 : ");
		int num = sc.nextInt();
		int i,j=1;
		
		if(num>0) {
			for(i=1; i<=num; i++) {
				for(j=1; j<=i; j++)
					System.out.print("*");
				System.out.println();
			}
		} else if (num<0){
			int num2 = -num;
			for(i=1; i<=num2; i++) {
				for(j=1; j<=num2-i+1; j++) {
					System.out.print("*");
				}
				System.out.println();
			}
		}
		else {
			System.out.println("출력 기능이 없습니다.");
		}
	}
	
	public void countInputCharacter(){
		System.out.print("문자열 하나 입력 : ");
		String str = sc.next();
		
		for(int i=0;i<str.length();i++) {
			if(!Character.isAlphabetic(str.charAt(i))) {
				System.out.println("영문자가 아닙니다.");
				return;
			}
		}

		System.out.print("문자 하나 입력 : ");
		char c = sc.next().charAt(0);
		
		int cnt = 0;
		
		for(int i=0; i<str.length();i++) {
			if(str.charAt(i)==c)
				cnt++;
		}
		
		System.out.println("포함된 갯수 : " + cnt);
		
	}
	
}
```

### 연습 문제

- 문제
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9cae0621-59f4-4825-8cd6-a4b3ba31c01a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9cae0621-59f4-4825-8cd6-a4b3ba31c01a/Untitled.png)
    

```java
package com.silsub2.example;

import java.util.Scanner;

/*
 * 1  2  3  4  5
 * 6  7  8  9  10
 * 11 12 13 14 15
 * 16 17 18 19 20
 * 21 22 23 24 25
 */

public class Exercise {
	public void exercise1() {
		int i,j=1;/*
		for(i=1; i<=5; i++) {
			for(j=1; j<=5; j++) {
				int num = (i-1)*5 + j;
				System.out.print(num + " ");
			}
			System.out.println();
				
		}
	
		System.out.println();
		*/
		int left = 0, right = 0;

		for(i=1; i<=5; i++) {
			for(j=1; j<=5; j++) {
				if(i==j)
					left+=(i-1)*5+j;//해당 좌표의 값
				else if(i+j==6)
					right+=(i-1)*5+j;
			}	
		}

		System.out.println("left : " + left);
		System.out.println("right : " + right);
		System.out.println("left + right : " + (left + right));
		
	}
	
	public void exercise2() {
		int random = (int) (Math.random()*100+1);
		int answer;
		Scanner sc = new Scanner(System.in);
		System.out.println("random : " + random);
		
		for(int i=0;;i++) {
			System.out.print("1에서 100사이의 정수를 입력하세요 : ");
			answer = sc.nextInt();
			
			if(answer > random)
				System.out.println("입력하신 정수보다 작습니다");
			else if(answer < random)
				System.out.println("입력하신 정수보다 큽니다");
			else {
				System.out.print("정답입니다. " + (i+1) + "회 만에 정답을 맞추셨습니다.");
				break;
				}
			
		}
	}
}
```

```java
package com.silsub1.main;

import com.silsub1.example.*;
import com.silsub2.example.*;

public class Main {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ForWhile fw = new ForWhile();
		
		
		System.out.println("[ 문제 1 ]");
		fw.printStar1();
		System.out.println();
		System.out.println("[ 문제 2 ]");
		fw.printStar2();
		System.out.println();
		System.out.println("[ 문제 3 ]");
		fw.countInputCharacter();
		
		System.out.println("-----");
		
		Exercise ex = new Exercise();
		System.out.println("[ 연습 1 ]");
		ex.exercise1();
		System.out.println();
		System.out.println("[ 연습 2 ]");
		ex.exercise2();
	}

}
```
