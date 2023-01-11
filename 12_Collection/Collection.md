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
