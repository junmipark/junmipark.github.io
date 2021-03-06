---
title:  "[자바 기초] 프로그래밍 Programming"
image: java.png
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA]
 
date: 2021-06-14
last_modified_at: 2022-01-22
---

# 프로그래밍

### 프로그래밍 관련 용어

- 프로그램 Program
  - 컴퓨터를 작동시키기 위한 순차적으로 작성된 일련의 명렁어들의 모음
- 프로그래밍 Programming
  - 프로그램을 만드는 행위
- 프로그래머 Programmer
  - 프로그램을 만드는 주체
- 프로그래밍 언어 Programming Language
  - 프로그램을 작성하기 위해 사용되는 언어
- 소프트웨어 Software
  - 컴퓨터를 효율적으로 운영하기 위해 개발된 프로그램

# 프로그램 언어별 특성

### 사용자 측면에서의 분류

- 저급 언어 Low Level Language
  - 기계 중심적 언어
  - 타 기계와 호환성이 낮음
  - 오류 수정이 어려움
  - 개발 용이성이 떨어짐
  - 수행속도가 빠름
  - 기계어, 어셈블리어 등
- 고급 언어 High Level Language
  - 사용자 중심적 언어, 컴파일 언어
  - 타 기계와 호환성이 높음
  - 오류 수정이 비교적 쉬움
  - 개발 용이성이 비교적 높음
  - 수행 속도가 느림
  - C, C++, JAVA, C# 등

### 실행 측면에서의 분류

- 컴파일러 언어
    - 고급 언어로 작성된 프로그램을 컴퓨터가 이해 가능한 기계어로 번역
    - 한번 컴파일하면 그대로 계속 사용 가능하여 처리 시간이 매우 빠름
    - 한줄의 소스코드가 많은 기계어로 버역되어 상대적으로 큰 기억용량(Stack)이 필요
    - C, C++, Java, C#
- 인터프리터 언어
    - 프로그램을 한 단계씩 기계어로 해석하여 실행
    - 한 줄씩 해석하여 실행되어 기억장소가 많이 필요하지 않아 자원 효율적
    - 플랫폼에 비의존적이고 자료형과 범위가 동적으로 설정되어 유연함
    - 인터프리터에 의해 해석되면서 실행되어 처리에 많은 시간이 소요
    - Basic, Lisp, PostScript
- 스크립트 언어
    - 배치언어 batch language 또는 작업 제어 언어 job control language
    - 응용 프로그램과 분리하여 작성
    - 프로그램 사용자가 응용프로그램을 요구에 맞게 다루기 위한 목적
    - 특정 실행 환경 상에서 실행되어 플랫폼 독립적
    - 고수준 언어로 작성되어 직관적
    - 단독으로 실행될 수 없어 별도의 런타임 환경을 구축해야 함
    - 경우에 따라 많은 리소스가 요구됨
    - JavaScript, ActionScript, Auto Hot Key, Perl, Python, Ruby, VBS

---

# 자바 Java

### 자바 소개

- 자바 Java
    - 썬 마이크로시스템즈에서 개발하여 발표한 객체지향 언어
    - 운영체제에 영향을 받지 않고 실행
    - 다양한 기종의 컴퓨터와 운영체제가 공존하는 인터넷 환경에 적합한 언어
    - 다양한 클래스 라이브러리(API)를 제공하여 수준급의 프로그램 제작 가능

### 자바의 특징

- 객체 지향 언어
- 플랫폼에 독립적이며 이식성이 높음
- 메모리를 자동으로 관리(GC, Garbage Collection)
- 동적 로딩(Dynamic Loading) 지원
- 멀티 스레드 구현 가능
- 오픈 소스 라이브러리가 풍부함

### 자바의 플랫폼

- Java Standard Edition
    - 자바 기본 플랫폼
- Java Enterprise Edition
    - SE + WEB
- Java Micro Edition
    - 임베디드 플랫폼

### 자바의 프로그래밍 과정

1. .java 언어의 문법에 따라 소스 코드를 작성 (classname.java)
2. JDK에서 제공하는 javac 컴파일러를 바이트 코드 형식으로 소스코드를 컴파일 (classname.class)
3. 컴파일된 class 파일을 JDK가 제공하는 java 인터프리터를 사용하여 실행

** 실행시 필요한 클래스들이 **JVM**에 연결되며 클래스 로더Loader가 필요한 클래스를 동적으로 로딩 Loading

### JVM (Java Virtual Machine)

- 자바 바이트 코드를 해당 운영체제의 기계어로 재번역하여 실행하는 주체
- 운영체제와 자바 프로그램을 연결
- 자바 프로그램을 플랫폼에 독립적으로 동작하도록 하는 역할
- 인터프리터나 JIT 컴파일 방식으로 바이트 코드를 실행할 수 있도록 함
- JRE에 포함되어 배포됨
- GC(Garbage Collection)을 수행
- **JIT 컴파일**
  - 프로그램을 실제 실행하는 시점에 기계어로 번역
  - 실행 시점에 기계어 코드를 생성하여 해당 코드를 캐싱
  - 함수가 여러 번 호출될 때 마다 기계어 코드가 생성되는 걸 방지
  - 인터프리터의 실행속도가 느린 단점을 보완
