---
title:  "[자바 기초] 컬렉션 Collection - 1"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 컬렉션 Collection]
 
date: 2021-07-20
last_modified_at: 2022-01-23
---

# 컬렉션 Collection

## 자료 구조 Data Structure

### 정의 
- 다수의 데이터를 효율적으로 사용할 수 있도록 구조를 만들어 저장한 것

### 특징
1. 데이터를 넣을 공간, 즉 크기에 제약이 없다. (동적 할당)
2. 데이터의 추가, 삭제가 용이하다.
3. 여러 타입의 데이터를 저장 가능하다.

### 컬렉션 프레임워크 Collection FrameWork
- Group of Object
- 그룹으로 존재하는 데이터를 저장하고 관리하기 위해 사용되는 자료 구조

---

## 리스트 List

### 특징
1. 객체마다 고유한 인덱스 번호가 존재하여 순서를 유지하여 저장할 수 있다.
2. 고유한 인덱스 번호가 존재하기 때문에 데이터를 중복 저장할 수 있다.

### 리스트 인터페이스를 상속받은 클래스
- ArrayList
- LinkedList
- Vector
- Stack

### 주요 메서드

|Method                     |Return Type            |Description                |
|---------------------------|-----------------------|---------------------------|
|add(E e)                   |boolean                |주어진 객체를 맨 끝에 추가            |
|add(int index, E element)  |void                   |주어진 인덱스에 객체를 추가            |
|set(int index, E element)  |void                   |주어진 인덱스에 저장된 객체를 주어진 객체로 변경|
|contains(Object o)         |boolean                |주어진 객체가 존재하는지 여부 검색        |
|get(int index)             |E                      |주어진 인덱스에 저장된 객체 리턴         |
|isEmpty()                  |boolean                |컬렉션이 비어있는지 여부 확인           |
|size()                     |int                    |컬렉션에 저장된 전체 객체 수를 리턴       |
|remove(int index)          |E                      |주어진 인덱스에 저장된 객체 삭제         |
|clear()                    |void                   |컬렉션에 저장된 모든 요소 삭제          |
|remove(Object o)           |boolean                |주어진 객체를 삭제                 |


---
