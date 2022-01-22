---
title:  "[자바 기초] 상속과 다형성 Inheritance & Polymorphism"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 상속, Inheritance, 다형성, polymorphism]
 
date: 2021-06-29
last_modified_at: 2022-01-22
---

# 상속

### 상속의 정의

- 상속(inheritance)은 기존에 존재하는 클래스로부터 데이터와 코드를 이어받고, 필요한 기능을 추가할 수 있는 기법
- 검증된 소프트웨어를 재사용할 수 있어 신뢰성 있는 소프트웨어를 손쉽게 개발, 유지보수 가능

### 상속의 형식

```java
class Child extends Parent { ... }
```

- 자바에서는 extends 키워드를 이용하여 상속을 나타냄
- 상속하는 클래스를 부모 클래스(슈퍼 클래스) 라고 함
- 상속 받는 클래스를 자식 클래스(서브 클래스) 라고 함
    - 자식 클래스는 부모 클래스의 public 멤버, protected 멤버, 디폴트 멤버(부모 클래스가 같은 패키지 내에 존재하는 경우)를 상속 받음
    - private 멤버는 상속되지 않음

### 상속의 필요성

1. 직접 작성할 필요 없이 이미 존재하는 클래스의 필드와 메소드를 재사용 가능
2. 상속을 사용하여 공통되는 부분을 하나로 정의하고 중복되는 코드를 줄일 수 있음

### 상속과 생성자

- 생성자의 호출 순서는 (부모 클래스의 생성자) → (자식 클래스의 생성자) 순
    - 자식 클래스 객체는 부모 클래스에서 상속된 부분을 초기화하기 위해 부모 클래스의 생성자를 호출
    - 부모 클래스의 생성자 호출이 끝나면 자식 클래스가 추가한 부분을 초기화 하기 위해 자식 클래스의 생성자를 실행
- 명시적 호출
    - 자식 클래스의 생성자에 명시적으로 부모 클래스의 생성자를 호출
    - super 키워드를 사용

```java
class Shape {
	public Shape() { 
		System.out.println("Shape 생성자() ");
	}
}

class Rectangle extends Shape {
	public Rectangle() { 
		super();
		System.out.println("Rectangle 생성자() "; 
	}
}
```

- 묵시적 호출
    - 자바에서는 명시적으로 슈퍼 클래스의 생성자를 호출하지 않아도 서브 클래스의 객체가 생성될 때 자동으로 수퍼 클래스의 기본 생성자를 호출
    - 묵시적으로 부모 클래스의 생성자를 호출하는 경우 부모 클래스의 기본 생성자가 반드시 정의되어 있어야 함

### 메소드 재정의

- 메소드 재정의(Overriding)의 정의
    - 부모 클래스로부터 상속 받은 메소드를 재정의 할 때 사용
    - 메소드의 이름과 매개변수, 반환형은 동일
    - 완벽하게 일치하지 않는 경우 메소드 중복 정의(Overloading)로 처리
    - 재정의 된 메소드 이름 앞에는 @Override 어노테이션 사용
- 메소드 오버라이딩을 하는 경우 보통 **super 키워드**를  통해 부모 클래스의 메소드를 호출한 후 자식 클래스의 내용에 맞게 내용을 추가함

```java
class Parent {
	public void print() { 
		System.out.println("부모 클래스의 print() 메소드");
	}
}

class Child extends Parent {
	@Override
	public void print() {
		super.print();
		System.out.println("자식 클래스의 print() 메소드");
	}
}
```
---
# 다형성

### 상속과 다형성

- 자식 클래스 안에는 부모 클래스 부분이 있기 때문에 부모 클래스의 객체로 취급할 수 있음
    - **부모 클래스 참조 변수로 자식 클래스 객체를 참조 가능**
    - 이것을 **상향 형변환(up-casting)**이라고 함
- 참조 변수가 가리키는 실제 객체에 따라 메소드가 자동적으로 선택
    - 부모 클래스의 참조 변수를 통하여 메소드를 호출하면 자식 클래스에 정의된 내용에 따라 적절한 메소드를 자동으로 호출
    - 이것을 **동적 바인딩(dynamic binding)** 또는 **가상 메소드 호출(virtual method invocation)** 이라고 함

```java
class Shape {
	protected int x,y;
		public void draw() { System.out.println("Shape Draw"); }
}
class Rectangle extends Shape {
	private int width, height;
	@Override
	public void draw() { System.out.println("Rectangle Draw"); }
}
class Triangle extends Shape {
	private int base, height
	@Override
	public void draw() { System.out.println("Triangle Draw"); }
}
class Circle extends Shape {
	private int radius;
	@Override
	public void draw() { System.out.println("Circle Draw"); }
}

public class ShapeTest {
	public static void main(String[] args){
		Shape[] arrOfShapes = new Shape[3];
		arrOfShapes[0] = new Rectangle();
		arrOfShapes[1] = new Triangle();
		arrOfShapes[2] = new Circle(); 
		//부모 클래스 참조 변수로 자식 클래스 객체를 참조 (upcasting)
	
		for(int i=0; i<arrOfShapes.length; i++)
			arrOfShapes[i].draw() 
		//실제 객체에 따라 서로 다른 draw()가 호출 (동적 바인딩)
	}
}
```

### instanceof

- 참조 변수가 가리키는 객체의 실제 타입을 알고 싶은 경우 instanceof 연산자 사용
- instanceof 연산자를 통한 연산은 참(true) 또는 거짓(false)을 반환

### 추상 클래스

- 추상 클래스(abstract class)는 완전하게 구현되지 않은 메소드를 포함하는 클래스
- 메소드가 미완성 되어 있어 추상 클래스는 객체 생성이 불가능
- 추상 클래스는 하나 이상의 추상 메소드를 갖고 있어야 함
- 추상 클래스를 상속받는 자식 클래스는 반드시 추상 메소드를 재정의
    
    ```java
    public abstract class Animal {
    	public abstract void move();
    }
    
    public class Lion extends Animal {
    	@Override
    	public void move() {
    		System.out.println("사자의 move() 메소드입니다. ");
    	}
    }
    ```
    

### 인터페이스

- 인터페이스 정의
    - 인터페이스(interface)는 클래스 간의 상호작용을 기술한 일종의 규격
    - 인터페이스를 정의할 때는 interface 키워드를 사용
        
        ```
        interface 인터페이스_이름 {
        	반환형 추상메소드1(...);
        	반환명 추상메소드2(...);
        	...
        }
        ```
        
    - 인터페이스에서 정의되는 메소드들은 public과 abstract를 사용하지 않아도 자동으로 public 및 abstract로 취급
- 인터페이스 구현
    - 인터페이스만으로는 객체를 생성할 수 없음
    - 인터페이스는 다른 클래스에 의하여 구현(implement) 가능
    - 클래스가 인터페이스를 구현하기 위해서는 implements 키워드 사용
    
    ```java
    interface Drawable{
    	void draw();
    }
    
    class Circle implements Drawable {
    	int radius;
    	public void draw() { System.out.println("Circle Draw"); }
    }
    ```
    
- 다른 클래스를 상속하는 동시에 인터페이스를 구현할 수 있음
- 자바에서는 클래스의 다중 상속은 금지되어 있으나 인터페이스를 이용한 다중 상속 효과를 낼 수 있음
- Java 8 에서는 인터페이스 안에 정적 메소드와 디폴트 메소드를 제공할 수 있음
