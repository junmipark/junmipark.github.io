---
title:  "[자바 기초] 컬렉션 Collection (2)"
excerpt: ""

categories:
  - JAVA
tags:
  - [프로그래밍, Programming, 자바, JAVA, 컬렉션 Collection]
 
date: 2021-07-20
last_modified_at: 2022-01-22
---

# 컬렉션 Collection

## 맵 Map

### 맵의 정의
- 컬렉션 프레임 워크에서 List와 Set과는 다르게 사용됨으로써 독자적인 인터페이스를 가지고 있는 컬렉션 프레임워크
- 다른 컬렉션과는 다르게 키Key 와 값Value 로 구성되어 있으며 이를 한 쌍으로 묶어서 Map 인터페이스 내부 클래스 Map.Entry로 다뤄짐
- 저장되있는 데이터에 접근하려면 키를 통해 접근해야하기 때문에 키는 고유한 값을 갖는다.

### 맵을 구현한 컬렉션
- HashTable
- HashMap
- Properties
- TreeMap

---

## HashMap

### 정의
  - Map 인터페이스를 구현한 클래스로 해싱Hashing 을 이용하여 많은 양의 데이터를 검색하는데 있어서 뛰어난 성능을 지님
    ```
      Map map = new HashMap(); // Map 인터페이스 다형성을 이용한 생성
      HashMap hMap = new HashMap(); // 직접 생성
    ```

### 주요 메서드
|Method                     |Return Type            |Description|
|---------------------------|-----------------------|-----------|
|put(K key, V value)        |V                      |주어진 키와 값을 추가, 저장이 되면 값을 리턴|
|containsKey(Object Key)    |boolean                |주어진 키가 있는지 확인하여 결과 리턴|
|containsValue(Object value)|boolean                |주어진 값이 있는지 확인하여 결과 리턴|
|entrySet()                 |Set\<Map.Entry\<K,V\>\>|키와 값의 쌍으로 구성된 모든 Map.Entry 객체를 set에 담아서 리턴|
|get(Object key)            |V                      |주어진 키의 값을 리턴|
|isEmpty()                  |boolean                |컬렉션이 비어있는지 여부|
|keySet()                   |Set\<K\>               |모든 키를 Set 객체에 담아서 리턴|
|size()                     |int                    |저장된 키의 총 수를 리턴|
|values()                   |Collection\<V\>        |저장된 모든 값을 Collection에 담아서 리턴|
|clear()                    |void                   |모든 Map.Entry를 삭제함|
|remove(Object key)         |V                      |주어진 키와 일치하는 Map.Entry 삭제, 삭제가 되면 값을 리턴|
  
### HashMap에 저장된 데이터를 연속적으로 처리하는 방법
  1. entrySet()
  
      key-value 쌍으로 연결된 값들을 Entry로 묶어서 Set 형태로 반환하는 메서드
      ```
        HashMap map = new HashMap();
        map.put("user1", "123");
        map.put("user2", "123");
        map.put("user3", "123");
  
        Set set = map.entrySet(); // entrySet()은 맵에 저장된 Key,Value 값을 Entry로 다뤄서 Set으로 반환
        Iterator it = set.iterator(); // set에 저장된 내부데이터에 접근하기 위해서 Iterator 생성
        
        while (it.hasNext()) {
          Map.Entry me = (Map.Entry) it.next(); // Set에 저장된 데이터 타입이 Map.Entry이기 때문에 iterator을 통해서 Map.Entry에 데이터를 다시 담는다
          System.out.println(entry.getKey() + "=" + entry.getValue());
        }
      ```
  
  2. keySet()
  
      ```
        HashMap map = new HashMap();
        map.put("user1", "123");
        map.put("user2", "123");
        map.put("user3", "123");

        Set keys = map.keySet();
        Iterator it = keys.iterator();.

        while (it.hasNext()) {
          String key = (String) it.next(); // next() 반환자가 object임
          String value = (String) map.get(key); // get()도 반환자가 Object 여서 String으로 형변환
          System.out.println(key + "=" + value);
        }
      ```

---

## 프로퍼티스 Properties

### 정의
  - Key, Value 값의 데이터 타입을 String으로 제한한 Map 컬렉션
  - .properties 확장자를 가진 데이터 파일을 다루는데 주로 사용
  - 문자열만 다루는 컬렉션으로 프로그램의 유지 보수를 편리하게 함
  - DB의 연결 정보를 저장하는 용도로 많이 사용

### 주요 메서드
|Method                                      |Return Type |Description|
|--------------------------------------------|------------|-----------|
|setProperties(Key key, Value value)         |void        |Properties에 데이터를 저장하는 기능|
|containsKey(Object key)                     |boolean     |매개변수로 전달되는 key값을 포함하고 있는지 확인|
|containsValue(Object value)                 |boolean     |매개변수로 전달되는 value값을 포함하고 있는지 확인|
|entrySet()                                  |Set         |properties에 저장된 데이터를 Set 컬렉션으로 저장하여 반환|
|get(Object key)                             |Object      |매개변수로 전달하는 key값을 반환, 만약 없다면 null 반환|
|getProperty(String key)                     |String      |매개변수로 전달하는 key값을 반환, 만약 없다면 null 반환|
|store(OutputStream os, String comment)      |void        |Properties에 저장된 데이터를 외부의 파일로 옮기기 위한 메서드|
|storeToXml(OutputStream os, String comment) |void        |Properties에 저장된 데이터를 외부의 XML로 옮기기 위한 메서드|
|load(InputStream is)                        |void        |외부 파일로부터 데이터를 입력 받을 수 있는 메서드|
|loadFromXml(InputStream is)                 |void        |외부 XML 파일로부터 데이터를 입력받을 수 있는 메서드|

### 예제
```
public void test() {
  Properties prop = new Properties();

  prop.setProperty("driver", "oracle.jdbc.driver.OracleDriver");
  prop.setProperty("url", "jdbc.oracle.thin:@127.0.0.1:1521:xe");
  prop.setProperty("user", "kh");
  prop.setProperty("password", "kh");

  System.out.println(prop);

  try {
    prop.store(new FileOutputStream("driver.properties"), "jdbc driver");
    prop.store(new FileWriter("driver.txt"), "jdbc driver");
    prop.storeToXML(new FileOutputStream("driver.xml"), "jdbc driver");
  } catch (FileNotFoundException e) {
    e.printStackTrace();
  } catch (IOException e) {
    e.printStackTrace();
  }
}
```
