### Getter, Setter 
- 캡슣화를 위해 클래스의 필드를 외부에서 직접 접근하지 못하도록 하는 과정에서, 필드의 접근제한을 private으로 설정하고, 해당 필드를 외부에서 간접적으로 접근할 수 있도록 하기 위한 메서드를 만들게 되는데, 이를 Getter와 Setter라고 한다. 
- Setter는 해당 인스턴스의 필드 값을 설정하는 역할을 하고, Getter는 해당 인스턴스의 필드 값을 가져오는 역할을 한다. 
- 작명 규칙에 의해 `set + 필드명`, `get + 필드명`으로 이름짓게 되는데, 이는 원칙적으로 캡슐화의 원칙에 위배된다.
```java
public class MemberDTO(){

    private String name;
    
    public String getName() {
        return this.name;
    } // name 필드를 가져오는 getter 예시
    
    // ...
}
```

### Constructor(생성자)
- new 연산자를 통해 객체가 Heap에 할당될 때 1회적으로 호출되며, return 타입이 없다.
- 인스턴스 생성시 필드 초기화의 목적으로 주로 사용된다. 
- 매개변수가 없는 기본 생성자와 매개변수가 있는 생성자로 구분할 수 있다.
- 기본 생성자의 경우 기본적으로 컴파일러가 자동으로 생성해주기 때문에, 기본 생성자만 이용한다면 명시적으로 작성할 필요는 없다.

### 매개변수가 있는 생성자를 사용해야 한다면
- 이 경우에는 위의 경우와 달리 컴파일러가 기본 생성자를 자동으로 만들어주지 않기 때문에, 기본 생성자가 필요한 경우 반드시 기본 생성자도 명시적으로 작성해줘야 한다.


- DTO 클래스를 예시로 생성자와 Getter, Setter을 살펴보자
```java
public class RecordDTO() {
    
    private String name;
    private int age;
    private String grade;
    
    public RecordDTO(){} // 기본 생성자


    public RecordDTO(String name){
        this.name = name;
    }

    public RecordDTO(String name, int age){
        this(name);
        this.age = age;
    }

    public RecordDTO(String name, int age, String grade){
//        this.name = name;
//        this.age = age;
//        this.grade = grade;
        this(name, age); // 다른 생성자를 활용하여 생성자를 만들어 줄 수 있다. 
        this.grade = grade;
    } // 세 필드를 초기화할 수 있는 매개변수가 있는 생성자.
    
    public void setName(String name){
        this.name = name;
    } 
    
    public String getName() {
        return this.name;
    } 
    
    // ... 이하 생략
}
```
- 여기서 this는 실제로 생성된 인스턴스의 주소를 가리킨다.
- 매개변수를 갖는 생성자는 필요한 종류만큼 다양하게 만들 수 있다. 이 때, 기존에 만들어둔 다른 매개변수가 있는 생성자를 이용할 수 있다.

### this
- 모든 인스턴스의 메소드(static 키워드가 붙지 않은 메소드)에 숨겨진 채 존재하는 레퍼런스 변수로, `할당된 인스턴스의 주소가 저장`된다.
- 매개변수를 가지는 생성자에서 매개변수명이 필드명과 같은 경우 매개변수의 변수명이 우선이므로 this를 이용하여 필드라는 것을 구분.

<br>

### 복사 생성자
- 이미 만들어진 동일한 타입의 인스턴스가 가지는 필드값을 이용해서 새로운 인스턴스를 생성해주는 생성자.
- 이를 사용해서 만들어진 인스턴스는 인자로 전달한 인스턴스와 동일한 필드 값을 가지지만 새롭게 할당되는 인스턴스이기 때문에 서로 다른 주소값을 가진다. (깊은 복사)

```java
public User(User otherUser) {
		this(otherUser.id, otherUser.name, otherUser.age); // 기존의 생성자를 이용해서 복사 생성자를 만들 수 있다.
}
```
<br>

### 생성자를 이용한 초기화와 Setter(설정자)를 이용한 초기화의 비교
1. 생성자를 이용한 초기화

   → 장점 : setter메소드를 여러번 호출해서 사용하지 않고, 단 한번의 호출로 인스턴스를 생성 및 초기화 할 수 있다.

   → 단점 : 필드를 초기화 할 매개변수의 갯수를 경우의 수 별로 모두 만들어주어야 한다.(사용자가 초기화를 원하는 변수의 종류나 갯수가 다를 수 있을 것을 대비하기 위해) 또한 호출시 인자가 많아지는 경우 어떠한 값이 어떤 필드를 의미하는지 눈으로 확인하기 힘들다.


2. 설정자를 이용한 초기화

   → 장점 : 필드를 초기화하는 각각의 값들이 어떤 필드를 초기화하는지 명확하게 알 수 있다.

   → 단점 : 하나의 인스턴스를 생성할 때 한 번의 호출로 끝나지 않는다.

   (상황에 따라 interrupt 등 여러가지 문제가 발생할 수 있다.)

- 최근에는 builder pattern을 활용하여 초기화 하는 경우도 많다.