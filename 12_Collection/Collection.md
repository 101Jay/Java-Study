## 컬렉션(Collection)
- 여러 개의 다양한 데이터들을 쉽고 효과적으로 처리할 수 있도록 표준화된 방법을 제공하는 클래스들의 집합
- java.util 패키지에 포함되어 있다.

### 컬렉션의 주요 인터페이스
- List / Set / Map

### List 컬렉션
- 자료들을 순차적으로 나열한 자료구조
- 인덱스로 관리되며, 중복해서 인스턴스 저장이 가능하다.
- 대표적인 List 인터페이스가 지원하는 클래스는 ArrayList가 있다.

### ArrayList
- 가장 많이 사용하는 컬렉션 클래스
- 내부적으로는 배열을 이용하여 요소를 관리한다.
- 배열의 단점을 보완하기 위해 만들어졌다.
- add, remove, set 등의 메소드 사용이 가능하다.
```java
public class Application1{
    public static void main(String[] args){
        
        List alist = new ArrayList();

        alist.add(0, "banana");
        System.out.println(alist);

        alist.remove(1);
        System.out.println(alist);

        alist.set(0, "hahaha");
        System.out.println(alist);
    }
}
```
- 타입의 안정성을 위해 제네릭을 사용하여 ArrayList에 들어갈 타입을 제한해주는 것이 좋다.
```java
public class Application2{
    public static void main(String[] args){
        List<String> sList = new ArrayList<>();
    }
}
```

### LinkedList
- ArrayList의 성능적 단점 보완
- 이중 연결 리스트로 구현되어 있다.
- ArrayList에서 사용하는 메소드들을 모두 가져다 쓸 수 있음
- 삽입, 삭제가 빈번하다면 LinkedList를 쓰는 것이 효율적이다.

---

### Queue 컬렉션
- 선형 메모리 공간에 데이터를 저장하는 FIFO 방식의 자료구조
- 별도의 Queue를 구현해 놓은 구현체가 없고, LinkedList 클래스를 이용하여 구현한다. 
- offer()와 poll()을 이용한다.

---

### Set 컬렉션
- 순서를 유지하지 않고, 데이터의 중복을 허용하지 않는 데이터의 집합
- 대표적으로 HashSet 클래스, TreeSet을 활용하여 구현한다.

### HashSet
- 검색 속도가 빠르며 add, contains 메서드를 사용할 수 있다.
- 인덱스를 사용할 수 없기 때문에 반복 처리를 위해서는 조치가 필요하다.
  - toArray() 메소드를 활용해 배열로 바꾼 뒤 for loop를 이용한다.
  - Iterator() 메소드를 활용해 목록으로 만들어서 처리한다. 

### LinkedHashSet
- HashSet에 저장 순서를 유지하는 특성을 추가한 클래스

### Map

- 키와 값으로 구성되어 있으며, 키와 값은 모두 인스턴스
- 키는 중복 저장을 허용하지 않고(Set), 값은 중복 저장 가능(List)
- 키가 중복되는 경우, 기존에 있는 키에 해당하는 값을 덮어씀
- 구현 클래스 : HashMap, HashTable, LinkedHashMap, Properties, TreeMap

  → put(key, value), size(), get(Object key), keySet(), values() 등의 메소드를 활용할 수 있음


---

### Map 인터페이스 특징

- 다른 Collection 인터페이스(List, Set)와는 다른 저장 방식을 가진다.
- key : 값을 찾기 위한 이름 역할의 객체.
- 요소의 저장 순서는 유지하지 않는다.
- HashMap을 주 구현 클래스로 활용

```java
public class Application{
  public static void main(String[] args){
    Map hashMap = new HashMap();
    hashMap.put("one", "red apple");

    // 키와 값의 타입을 제한할 수 있다.
    Map<String, String> hashMap2 = new HashMap();
  }
}
```

### Map 인터페이스의 반복 처리

1. keySet()을 이용하여 키만 따로 Set으로 만들고, iterator()로 목록을 만들어서 반복문 처리.

```java
Iterator<String> iter = hmap2.keySet().iterator();

while(iter.hasNext()){
  String key = iter.next();
  String value = hmap2.get(key);
}
```

2. 저장된 value 객체들만 values()로 분리하여 Collection으로 만듦.

 ```java
Collection<String> values = hmap.values();
```

  - 이후 iterator()로 목록 만들어서 처리하거나 배열로 만들어서 처리
3. Map의 내부클래스인 EntrySet을 이용

```java
Set<Map.Entry<String, String>> set = hmap2.entrySet();
Iterator<Map.Entry<String, String>> entryIter = set.iterator();

while(entryIter.hasNext()) {
  Map.Entry<String, String> entry = entryIter.next();
  System.out.println(entry.getKey() + entry.getValue());
}
```

- Map.Entry는 맵 한 뭉텅이 자체를 set의 형태로 저장해 놓은 것

### Properties

- 키와 값을 String 타입으로 제한한 Map 컬렉션의 하나
- 주로 .properties 파일을 읽어 들일 때 사용
- 작성하는 방식이 정해져 있는 텍스트 파일
- 키와 값이 = 기호로 연결되어 있다.
- 앱에서 주로 변경이 잦은 문자열을 저장하여 관리.
- 데이터베이스와 연동할 때 외부 파일로 빼놓는데, 그 때 properties를 사용하기도 함.


```java
public class Application{
  public static void main(String[] args) {
      
      Properties prop = new Properties();
      prop.setProperty("driver", "oracle.jdbc.driver.OracleDriver");
     
      System.out.println(prop);
     
      try { // 앞서서 작성한 Properties 파일을 driver.dat이라는 파일로 작성
          prop.store(new FileOutputStream("dirver.dat"), "jdbc.driver");
          // Declaration : public void store(OutputStream out,String comments)
      } catch (FileNotFoundException e) {
          e.printStackTrace();
      } catch (IOException e) {
          e.printStackTrace();
      }

      Properties prop2 = new Properties();
               
      try { // 앞서 썼던 Properties 파일을 .load 메소드를 이용해서 읽어옴.
      // prop2.load(new FileInputStream("driver.dat"));
          prop2.load(new FileReader("driver.txt"));
          prop2.loadFromXML(new FileInputStream("driver.xml"));
      } catch (FileNotFoundException e) {
          e.printStackTrace();
      } catch (IOException e) {
          e.printStackTrace();
      }
      
      System.out.println(prop2.getProperty("driver"));
  }
}
```