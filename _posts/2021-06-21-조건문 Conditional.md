---
title:  "[자바 기초] 연산자 Operator"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 조건문, Conditional]
 
date: 2021-06-21
last_modified_at: 2022-01-22
---

# 조건문 Conditional

### 조건문의 정의

- 프로그램의 수행 흐름을 바꾸는 역할을 하는 제어문의 종류 중 하나
- 조건에 따라 다른 문장이 수립되도록 함

### 조건문의 종류

- if문
- switch문

### if문

- if / if~else / if~else if~else
- 조건식의 결과 값이 true이면 조건절 안의 내용 수행
- false면 조건 절 밖의 내용 수행
- 중첩하여 사용 가능

### switch문

- 조건식 하나로 많은 경우의 수를 처리할 때 사용
- 조건식의 결과는 정수, 문자, 문자열
- 조건식의 결과 값과 일치하는 case문으로 이동
- default문은 일치하는 경우가 없을 때 수행

---

# 실습 예제

### 조건문 예제

- 문제
    
    <실습>
    
    - 실행용 클래스 : com.silsub1.main.SilsubMain.java (main 포함)
    - 기능 제공용 클래스 : com.silsub1.example.Munjae.java
    
    [문제 1]
    
    - 메소드명 : public void test1(){}
    //국, 영, 수 세 과목(int)의 점수를 키보드로 입력받고,
    //합계와 평균을 계산하고,
    //세 과목의 점수와 평균을 가지고 합격 여부 처리함
    //합격의 조건 : 세 과목의 점수가 각각 40점이상이고,
    // 평균이 60점 이상이면 합격,
    // 아니면 불합격 처리함
    //합격인 경우에는 과목별 점수와 합계, 평균을 출력하고,
    //불합격인 경우는 "불합격" 출력함
    
    [문제 2]
    
    - switch문 사용함
    - 메소드명 : public void test2(){}
    <ex> 화면에 출력함
    *** 초기 메뉴 ***
        1. 입력
        2. 수정
        3. 조회
        4. 삭제
        5. 종료
        메뉴번호 입력 : 번호입력받음
        => 처리내용 :
        1 입력 --> "입력메뉴가 선택되었습니다."
        2 입력 --> "수정메뉴가 선택되었습니다."
        3 입력 --> "조회메뉴가 선택되었습니다."
        4 입력 --> "삭제메뉴가 선택되었습니다."
        7 입력 --> "프로그램이 종료됩니다."
        다른값 입력시 "번호가 잘못 입력되었습니다."
        "다시 입력하십시오." 출력되게 함
    
    [문제 3]
    
    - 메소드명 : public void test3(){}
    - 메소드 안 구현 내용 :
    1. 정수 변수 선언
    2. 키보드로 부터 정수 하나 입력받음
    3. 입력받은 정수가 양수이면 "양수다." 출력
    양수가 아니면 "양수가 아니다." 출력
    4. main 에서 실행 테스트함.
    
    [문제 4]
    
    - 메소드명 : public void test4(){}
    - 메소드 안 구현 내용 :
        1. 정수 변수 선언
        2. 문자열 변수 선언
        3. 키보드로 부터 정수를 하나 입력 받음
        단, 양수일 때만
        4. 입력받은 정수가 짝수이면 "짝수다" 를 문자열에 기록하고 출력,
        짝수가 아니면 "홀수다"를 문자열에 기록하고 출력함
        <짝수의 조건>
        어떤 수를 2로 나눈 나머지가 0과 같으면 짝수임.
    
    [문제 5]
    
    - 메소드명 : public void inputTest(){}
    - 구현할 내용 :
        1. 이름(String), 나이(int), 키(double) 변수 선언
        2. 각 값을 키보드로 입력받아, 각 변수에 저장함
        3. 이름이 null이 아니면서 글자갯수가 0보다 크고,
        나이와 키가 양수일 때만 화면에 출력함.
        ex>
        이름 : 홍 길동
        나이 : 25
        키 : 187.5
        확인 : 홍 길동의 나이는 25세이고, 키는 187.5 cm 이다.
    
    [문제 6]
    
    - 메소드명 : public void test6(){}
    - 구현 내용 :
        1. 두 개의 정수 변수 선언
        2. 키보드로 두 개의 정수를 입력받아, 단, 두 수 모두 양수일 때만
        3. 두 수의 합, 차, 곱, 몫을 출력함
        ex>
        첫번째 정수 : 25
        두번째 정수 : 7
        25 + 7 = 32
        25 - 7 = 18
        25 * 7 = 175
        25 / 7 = 3
        25 % 7 = 4
    
    [문제 7]
    
    - 메소드명 : public void test7(){}
    - 구현 내용 :
    1. 정수변수와 문자변수 선언
    2. 키보드로 점수를 입력받아, 정수변수에 저장
    단, 점수는 반드시 0 이상의 값이여야 함.
    3. 다중 if문으로 점수가 90 이상이면 문자변수에 'A' 대입
    80 이상 90 미만 'B'
    70 이상 80 미만 'C'
    60 이상 70 미만 'D'
    60 미만 'F' 대입함
    4. 점수와 학점 출력 확인

```java
package com.silsub1.example;

import java.util.Scanner;

public class Munjae {

	// 문제 1
	public void test1() {
		int kor, eng, math;
		int tot, avg;
		boolean pass = true;
		
		Scanner sc = new Scanner(System.in);
		
		System.out.print("점수를 순서대로 입력하세요(국어, 영어, 수학) : \n");
		kor = sc.nextInt();
		if(kor < 40) pass = false;
		eng = sc.nextInt();
		if(eng < 40) pass = false;
		math = sc.nextInt();
		if(math < 40) pass = false;
		
		tot = kor + eng + math;
		avg = tot / 3;
		if (avg < 60) pass = false;
		
		if(!pass)
		{
			System.out.println("불합격");
			return;
		}
		
		System.out.println("- 과목별 점수 -");
		System.out.println("국어 : " + kor);
		System.out.println("영어 : " + eng);
		System.out.println("수학 : " + math);
		System.out.println("평균 : " + avg);
		
	}
	// 문제 2
	public void test2() {
		int num;
		String str = "";
		boolean full = false;
		
		Scanner sc = new Scanner(System.in);
		
		System.out.println("*** 초기 메뉴 ***");
		System.out.println("1. 입력\n2. 수정\n3. 조회\n4. 삭제\n7. 종료");
		System.out.println("메뉴 번호 입력 : ");
		num = sc.nextInt();
		
		switch(num){
		case 1 : 
			str = "입력";
			break;
		case 2 : 
			str = "수정";
			break;
		case 3 : 
			str = "조회";
			break;
		case 4 : 
			str = "삭제";
			break;
		case 7 : 
			str = "프로그램이 종료됩니다.";
			full = true;
			break;
		default : 
			str = "번호가 잘못 입력되었습니다. \n다시 입력하십시오.";
			full = true;
		}
		
		if(full) System.out.println(str);
		else System.out.println(str+"메뉴가 선택되었습니다.");
		
	}
	
	// 문제 3
	public void test3() {
		int i;
		Scanner sc = new Scanner(System.in);
		
		System.out.print("정수를 하나 입력하세요 : ");
		i = sc.nextInt();
		
		if(i>0) System.out.println("양수다.");
		else System.out.println("양수가 아니다.");
	}
	
	// 문제 4
	public void test4() {
		int i;
		String str;
		
		Scanner sc = new Scanner(System.in);
		
		System.out.print("정수를 하나 입력하세요 : ");
		i = sc.nextInt();
		
		if(i<0) return;
			
		if(i%2==0)
			str = "짝수다";
		else
			str = "홀수다";
		
		System.out.println(str);
	}
	
	// 문제 5
	public void inputTest() {
		String name;
		int age;
		double height;
		
		boolean flag = true;
		
		Scanner sc = new Scanner(System.in);

		System.out.print("이름을 입력하세요 : ");
		name = sc.next();
		if(name.length()<=0 || name == null) flag = false;
		System.out.print("나이를 입력하세요 : ");
		age = sc.nextInt();
		if(age<0) flag = false;
		System.out.print("키를 입력하세요 : ");
		height = sc.nextDouble();
		if(height<0) flag = false;
		
		if(flag)
			System.out.println(name + "의 나이는 " + age + "이고, 키는 " + height + " cm 이다.");
	}
	
	// 문제 6
	public void test6() {
		int i,j;
		boolean flag = true;
		Scanner sc = new Scanner(System.in);

		System.out.print("정수를 입력하세요 (1) : ");
		i = sc.nextInt();
		if(i<0) flag = false;
		System.out.print("정수를 입력하세요 (2) : ");
		j = sc.nextInt();
		if(j<0) flag = false;
		
		if(!flag) return;

		System.out.println(i + " + " + j + " = " + (i+j));
		System.out.println(i + " - " + j + " = " + (i-j));
		System.out.println(i + " * " + j + " = " + (i*j));
		System.out.println(i + " / " + j + " = " + (i/j));
		System.out.println(i + " % " + j + " = " + (i%j));
	}
	
	// 문제 7
	public void test7() {
		int i;
		char c;
		
		Scanner sc = new Scanner(System.in);

		System.out.print("점수를 입력하세요 : ");
		i = sc.nextInt();
		
		if(i<0) return;
		
		if(i>=90)
			c = 'A';
		else if(i>=80)
			c = 'B';
		else if(i>=70)
			c = 'C';
		else if(i>=60)
			c = 'D';
		else c = 'F';

		System.out.println("점수 : " + i);
		System.out.println("학점 : " + c);
	}
}
```

```java
package com.silsub1.main;

public class SilsubMain {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		com.silsub1.example.Munjae m = new com.silsub1.example.Munjae();

		System.out.println("[ 문제 1 ]");
		m.test1();
		System.out.println();
		System.out.println("[ 문제 2 ]");
		m.test2();
		System.out.println();
		System.out.println("[ 문제 3 ]");
		m.test3();
		System.out.println();
		System.out.println("[ 문제 4 ]");
		m.test4();
		System.out.println();
		System.out.println("[ 문제 5 ]");
		m.inputTest();
		System.out.println();
		System.out.println("[ 문제 6 ]");
		m.test6();
		System.out.println();
		System.out.println("[ 문제 7 ]");
		m.test7();
		System.out.println();
	}

}
```
