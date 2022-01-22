---
title:  "[자바 기초] 예외 Exception"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 예외, Exception]
 
date: 2021-06-29
last_modified_at: 2022-01-22
---

# 예외

## 예외 Exception

### 예외 정의

- "Exceptional Event"의 약자
- 소스 수정으로 해결 가능한 에러

### 자바에서의 오류(에러), 예외 구분

|비교            |오류 Error                                         |예외 Exception|
|--------------|-------------------------------------------------|------------|
|문제 원인         |시스템 자원 부족으로 발생                                   |소스 코드로 인해 발생|
|복구 가능 여부      |X                                                |O           |
|처리 방법         |소스 코드 상에서 해결 불가능                                 |try, catch / throw 키워드 사용|
|발생 결과         |비정상적인 프로그램 종료                                    |try-catch문 또는 throw를 통한 처리 결과 표시|
|패키지           |java.lang.Error                                  |java.lang.Exception|
|예             |메모리 부족, 스텍 오버플로우 등                               |널 포인트 오류, 인덱스 범위 초과 등|

- 참고 

![image](https://user-images.githubusercontent.com/92344242/150640415-d881ba68-4fc9-4793-bc77-45c5cc7a4702.png)    
    

## 예외 클래스

![image](https://user-images.githubusercontent.com/92344242/150640427-d5d54398-c1b0-487d-b968-fe71a4f9d81d.png)

### **Exception 클래스** 분류

- **Checked Exception**
    - 개발자가 소스코드 상으로 반드시 예외 처리를 해야함
    - ClassNotFoundException, NoSuchMethodException 등
- **Unchecked Exception**
    - 예외 처리가 따로 필요하지 않음
    - ArithmetricException, NullPointerException, ArrayIndexOutOfBoundsException등

### RuntimeException 클래스

- Unchecked Exception
- 예외 처리를 하기 보다는 코드를 수정하여 문제 해결
- 프로그래머의 부주의로 발생
- 후손 클래스
    - ArithmetricException
    - ArrayIndexOutOfBoundsException
    - NullPointerException
    - ClassCastExceptioin
    - NegativeArraySizeException

## 예외 처리

### 예외 확인

- [Java API Document](https://docs.oracle.com/javase/8/docs/api/)
    - [java.io.BufferedReader 클래스 항목](https://docs.oracle.com/javase/8/docs/api/java/io/BufferedReader.html)    
    - 원하는 클래스의 생성자 또는 메소드 명을 검색하여 해당 메소드가 발생시킬 수 있는 Exception을 확인 가능
        ![image](https://user-images.githubusercontent.com/92344242/150640447-e33b3692-0c90-4ad3-8cb0-63f09c7d4fd0.png)        
        *java.io.BufferedReader의 readLine() 메소드*
        
    - 해당 메소드를 사용하려면 반드시 뒤에 명시된 예외 클래스를 처리해야 함

### 예외 처리 방법

1. ***throws***로 예외 던지기
    1. 메소드 선언 시 **throws ExceptionName** 문을 추가하여 상위 메소드에게 처리 위임
    2. 연쇄적으로 위임이 가능하나 메인 메소드까지 위임되는 경우 이에 대한 처리가 필요
        1. 메인 메소드에서 처리되지 않은 경우 비정상 종료  
1. ***try~catch***로 예외 잡기
    1. 메소드 내 예외가 발생할 가능성이 있는 부분을 **try-catch**문을 이용하여 처리
    2. **try** : 예외가 발생할 가능성이 있는 코드를 기술
    3. **catch** : try 구문에서 예외 발생 시 해당하는 예외에 대한 처리 기술
        1. 여러개의 예외 처리 가능
        2. 예외들간의 상속 관계 고려
    4. **finally** : 예외 발생 여부와 관계 없이 실행되야 하는 로직 기술
        1. 코드 중간에 return문을 만나도 수행
        2. System.exit()을 만나면 무조건 프로그램 종료
        3. 주로 java.io나 java.sql 패키지의 메소드 처리시 이용

```
try {
	// 예외가 발생할 수 있는 코드
} catch (예외종류 참조변수) {
	// 예외를 처리하는 코드
} finally {
	// try 블록이 끝나면 무조건 실행
}
```

```java
try {
	int result = 10/0;
} catch (ArithmetricException e) {
	e.printStackTrace()
} finally {
	System.out.println("try/catch 통과");
}
```

1. ***try~with~resource* (자동 리소스 관리)**
    1. Java 7에서 도입된 새로운 예외 처리 매커니즘
    2. try catch 블록 내에서 사용되는 리소스를 자동으로 닫음(close)
    
    ```java
    try (BufferedReader br = new BufferedReader(new FileReader("text.txt"))) {
    	String s;
    	while ((s = br.readline()) != null)
    		System.out.println(s);
    } catch (FileNotFoundException e) {
    	System.out.println("File Not Found");
    } catch (IOException e) {
    	e.printStackTrace();
    } catch (Exception e) {
    	e.printStackTrace();
    }
    ```
    

### 예외와 오버라이딩

- 오버라이딩된 메소드를 throws를 통해 예외 처리할 때 처리 범위가 원래 메소드의 예외 처리 범위보다 좁아야 함

```java
// 부모 클래스 Parent
public class Parent {

	public void method() throws IOException {
		...
	}
}
```

```java
// 자식 클래스 Child
public class Child extends Parent {
	@Override
	public void method() throws EOFException {
		// IOException의 하위 예외인 EOFException 처리
	}
}
```

## 사용자 정의 예외

- Exception 클래스 상속받아 예외 클래스를 작성
- 예외가 발생한 곳에서 **throw new 예외 클래스명()**으로 작성

```java
package com.chap03.myException;

public class MyException extends Exception {
	public MyException() {
		System.out.println("내가 만든 예외클래스다!");
	}
	public MyException(String msg) {
		super(msg);
	}
}
```

```java
package com.chap03.myException;

import java.util.Scanner;

public class Run {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.print("정수 하나 입력 : ");
		int no = sc.nextInt();
		// throws로 던진 예외 잡기
		try {
			checkNum(no);
		} catch (MyException e) {
			e.printStackTrace();
		}
	}

	public static void checkNum(int num) throws MyException {
		if (num < 10) {
			// 사용자 정의 예외 클래스 사용
			throw new MyException();
		} else {
			System.out.println(num + "은 10보다 크거나 같은 수");
		}
	}
}
```
