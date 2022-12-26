## 객체 지향 프로그래밍(OOP)
- 현실 세계는 사물이나 개념처럼 독립되고 구분되는 각각의 객체로 구성되어 있다.
- 발생하는 모든 사건은 객체간의 상호작용이다.
- 이러한 개념을 프로그래밍에 도입하여 만들어진 방식이 객체 지향 프로그래밍이다. 이를 활용한 프로그래밍 언어를 객체 지향 언어라고 한다.
- 객체 지향 언어는 성능면에서 C언어와 같은 절차 지향 언어에 비해 부족하지만, 재사용이 용이하며 생산성이 높아진다는 장점을 갖는다.
- Java는 대표적인 객체 지향 언어이며, 컴퓨터 성능이 좋아진 요즘 kotlin, JavaScript, Python 등의 언어들은 객체 지향 언어에 속한다.

#### `의인화`의 개념
- 본인의 상태를 스스로 제어하고 행동하도록 하는 것

### OOP의 특징
- 4대 특징 : `캡슐화`, `상속`, `다형성`, `추상화`
- 3대 특징 : `캡슐화`, `상속`, `다형성`

### OOP의 관점에서 보는 클래스와 객체(인스턴스)
#### 클래스란?
- 객체를 `추상화`한 것으로 객체를 생성할 목적으로 정의해놓은 소스 코드
  - 자바에서는 객체를 구현하기 위한 매커니즘으로 클래스를 사용한다.
- 즉, 클래스는 객체를 구현하기 위한 소스 코드에 불과하다.
#### 객체란?
- 현실에 존재하는 독립적이면서 하나로 취급되는 사물이나 개념
- 클래스에 정의된대로 new 연산자를 통해 heap에 할당된 공간(== 인스턴스)

#### `학생`이란 클래스는 실제 인스턴스인 `영희`, `영수`...에서 학생이 가지는 공통적인 기능과 속성을 추상화 시킨 것을 의미한다. 

### 객체간의 상호작용
- 객체간의 상호작용은 `메소드`라는 메시지를 통해 이루어진다.
- 수신자는 그 메시지를 전달 받아 메시지에 해당하는 내용대로 처리하는 방법을 스스로 결정하고, 그 방법대로 처리할 명령어들을 순차적으로 기술한다. 이를 `메소드`라고 한다.

#### 메소드의 동작 수행 책임
- 호출을 받고 메시지를 수신한 곳에서 메소드의 동작 수행에 대한 책임을 갖는다.
- 이러한 동작 수행 책임은 결국 해당 객체가 짊어져야 하고, 이를 `책임 주도 설계`라고 말한다.
- `단일 책임의 원칙` : 객체 지향 설계의 주요 원칙으로, 하나의 객체는 하나의 책임만 가져야 한다는 원칙을 말한다.

### 오버로딩(overloading)
- 같은 이름의 메소드를 중복하여 정의하는 것을 의미한다.
- 매개변수의 종류에 따라 메소드를 다르게 처리해야할 때 사용한다.
- 메소드의 시그니처(signature : 메소드 이름과 매개변수의 조합)가 달라지게 된다.(메소드 이름은 동일하지만..)
- 매개변수를 달리할 때 매개변수의 이름이 아닌 매개변수의 타입이 달라야 한다.

### 메소드의 파라미터(매개변수)
- 가변인자, 클래스 자료형도 매개변수로 넘길 수 있다.


---

### 추상화란?
- 유연성을 확보하기 위해 공통점을 추출하고, 불필요한 공통점을 제거하는 과정
- 복잡한 현실 세계를 그대로 반영하기에는 방대하고 복잡하기 때문에, 현실 세계를 프로그램의 목적에 맞게 단순화 하는 추상화의 과정을 거치게 된다.
- `추상화의 목적` 
  - 유연성의 확보 -> `재사용성의 증가`
  - `중복 제거` : 중복 작성되는 코드를 줄일 수 있다.
  - `오류 발생 가능성을 낮추고`, `유지보수성을 증가`시킨다.
  - 유지보수성을 증가시킨다는 것은 결국 `비용을 줄일 수 있음`을 의미한다.

### 자바 빈 작성 규칙
- 자바 빈이란? : EJB(Enterprise Java Bean)로 어플리케이션을 만들 때 생성되는 객체를 Bean이라고 부른다.
1. 특정 패키지에 속해 있어야 한다. (default 패키지 사용 금지)
2. 멤버 변수의 접근제어자는 private으로 선언해야 한다.
3. 기본 생성자가 명시적으로 존재해야 한다. 이후 매개변수가 있는 생성자를 만들 것을 대비하는 용도이다.
4. 멤버 변수에 접근 가능한 설정자(setter)와 getter가 public으로 작성되어 있어야 한다.
5. 직렬화(serializable)가 구현 되어야한다. 


### DTO(Data Transfer Object) : 데이터 관점의 객체
- 값을 묶어서 상호작용하기 위한 객체로, 행위 위주가 아닌 데이터 관점의 객체이다.
- 연관성 있는 데이터들끼리 뭉쳐서 전달할 수 있다.
- 집합적인 의미가 있어야 한다.
- setter와 getter를 활용하여 필드에 접근하도록 구현하여 최소한의 캡슐화 원칙을 지켜야 한다.

---

### Static 
- 정적 메모리 영역에 프로그램이 시작될 때부터 변수나 메소드를 할당시키고자 할 때 사용하는 키워드
- static으로 할당된 필드나 메소드는 따로 인스턴스를 생성하지 않고도 사용할 수 있다.
- 여러 인스턴스가 공유해서 사용할 수 있다. 이는 다르게 생각해보면 추적이 불가능하다는 관점에서도 문제를 야기할 수 있다.
- stack에서 메인 메서드가 pop될 때까지 고정적으로 존재한다.
- 남발할 경우 유지보수성을 떨어뜨리고 추적이 힘든 코드가 될 수 있음으로 남발해선 안된다.
- static이 붙어있는 변수를 클래스 변수, 그렇지 않은 변수를 인스턴스 변수라고 한다.

<br>

#### Static 변수 

- static 변수의 값은 누적된다.
- 아래의 예시를 보며 생각해보자
```java
public class StaticFieldTest {

  private int nonStaticCount;
  private static int staticCount; // 클래스 변수의 선언

  public int getNonStaticCount() {
    return this.nonStaticCount;
  }

  public int getStaticCount() {
    return StaticFieldTest.staticCount; // 클래스 변수의 사용
  }
  
  public void upNonStaticCount(){
      nonStaticCount++;
      return;
  }
  
  public void upStaticCount(){
      staticCount++;
      return;
  }
}
// different class
public class Application {
    public static void main(String[] args){
        StaticFieldTest staticFieldTest1 = new StaticFieldTest();
        
        staticFieldTest1.upNonStaticCount();
        staticFieldTest1.upStaticCount();
        
        StaticFieldTest staticFieldTest2 = new StaticFieldTest();
        
        int nonStaticNum = staticFieldTest2.getNonStaticCount();
        int staticNum = staticFieldTest2.getStaticCount();
        
        System.out.println(nonStaticNum); // 0 : 누적되지 않고 생성된 StaticFieldTest 인스턴스별로 새롭게 count 된다.
        System.out.println(staticNum); // 1 : 하나의 staticCount가 누적되어 계산된다. 
    }
}
```
- 다음과 같이, 다른 클래스에서 static으로 선언된 `변수`는 메인 클래스에서 인스턴스를 생성하여 조작을 가하면 그 값을 누적하여 가지고 있는 것을 확인할 수 있다.

<br>

#### Static 메소드
- static 메소드 내부에서 클래스의 non-static 멤버에 접근하는 것은 불가능하다.
```java
public class StaticMethodTest{
  private int count;
  private static int staticCount;

  public void nonStaticMethod() {
    this.count ++;
    StaticMethodTest.staticCount ++;
  }

  public static void staticMethod(){
//        this.count ++; // 오류 발생
    StaticMethodTest.staticCount ++;
  }
}
```
- 생각해보면 그럴 수밖에 없는 것 같다. 인스턴스를 생성하지 않아도 사용할 수 있는 static 메소드인데, 그 내부에서 인스턴스를 생성해야만 사용할 수 있는 non-static 필드를 사용한다는 것은 모순적이기 때문이다.
- static 메소드에 접근할 때, 해당 객체를 생성해서 접근할 수도 있지만, 굳이 메모리 영역을 낭비해가면서 그럴 필요가 없다. 바로 `클래스명.메소드명`으로 사용하는 것이 좋다. 
  - 이 때, 동일한 클래스의 경우 클래스명을 생략하고 호출할 수 있다.
  - 만약 다른 클래스에서 클래스명을 생략하고 호출하고 싶다면 해당 메소드를 import 해서 사용하는 것도 가능하다.
  - 디폴트 패키지에 있는 클래스에 선언된 static 멤버(메소드, 필드)는 import가 불가능하니 주의하자.
```java
import static com.great.practice.StaticMethodTest.staticMethod; // static 메소드 import
//... 
```

---

### final
- 변경 불가의 의미를 담고 있는 키워드
- 메소드에서는 `종단`의 의미를 지님
- 클래스에서 필드를 선언할 때 final 키워드를 붙이면, 선언과 동시에 초기화를 하거나 생성자를 통한 초기화를 반드시 해줘야 한다.
- 즉, 선언만 해주면 컴파일 오류를 발생시킨다.
- static 키워드와 함께 사용이 가능하지만, static 키워드가 함께 사용하기 위해선 선언과 동시에 초기화 하거나 static 초기화 블록을 활용해 초기화를 진행해줘야 한다.
  - 즉, 생성자를 통한 초기화가 불가능하다. 
```java
public class FinalStaticTest {
    private static final int STATIC_INT;
    
    static {
        STATIC_INT = 1;
    } // static 블록을 활용한 초기화의 예시
}
```

<br>

#### final 키워드가 붙었을 경우
1. 지역변수 : 초기화 이후 값 변경 불가
2. 매개변수 : 호출시 전달한 인자 변경 불가
3. 전역변수 : 인스턴스 생성 후 초기화 이후에 값 변경 불가
4. 클래스(static) 변수 : 프로그램 start 이후 값 변경 불가
5. non-static 메소드 : 메소드 재작성(overriding) 불가
6. static 메소드 : 메소드 재작성(overriding) 불가
7. 클래스 : 상속 불가

---

### Singleton Pattern
- 어플리케이션에서 특정 클래스를 이용해 인스턴스를 한 개만 메모리에 할당한 후, 하나의 인스턴스를 여러 곳에서 공유해서 사용하며 메모리 낭비를 방지할 수 있게한 디자인 패턴

#### 장점
1. 두 번째로 이용할 때부터는 이미 생성해 둔 인스턴스를 사용하기에 인스턴스를 생성하는데 걸리는 시간을 절약할 수 있다.
2. 인스턴스가 절대적으로 한 개만 존재하는 것을 보장할 수 있다. 

#### 단점
1. 하나의 싱글톤 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유하면 결합도가 높아진다.
2. 동시성 문제를 고려하여 설계를 해야하기 때문에 설계 난이도가 높다.

<br>

#### 동시성 문제란? : 기본적으로 멀티쓰레드를 지원하는 자바에서 병렬로 동작하고 있는 쓰레드간 공유하고 있는 것이 있을 때 발생하는 문제
- 쓰레드간의 동기화 처리를 통해 공유 자원에 한 번에 여러 쓰레드가 접근하지 못하도록 하는 방법으로 해결할 수 있지만, 속도는 늦어진다.

### 싱글톤 구현 방식
#### 1. 이른 초기화(Eager Initialization)
- 선언과 동시에 초기화를 진행하고, 이후에 필요할 때 미리 선언한 인스턴스를 반환해주는 방식
```java
public class EagerSingleton{
    
    private static EagerSingleton eager = new EagerSingleton();
    
    private EagerSingleton(){} // 구현 은닉
  
    public static EagerSingleton getInstance(){
          return eager;
    }
}
```

#### 2. 게으른 초기화(Lazy Initialization)
- 인스턴스를 생성하는 시점에서 해당 인스턴스가 생성되어 있는지를 확인하고, 그렇지 않다면 그 시점에서 최초 생성하는 방식
```java
public class LazySingleton{
    private static LazySingleton lazy;
    
    private LazySingleton(){} // 구현 은닉
  
    public static LazySingleton getInstance(){
      if(lazy == null) {
          lazy = new LazySingleton();
      } // 최초 호출 시점에서 인스턴스 생성
      return lazy;
    }
}
```

--- 
### 예시를 통한 변수의 종류 살펴보기
```java
package com.greedy.section07.kindofvariable; // 패키지 영역 : 가장 위에
// import 영역
public class KindOfVariable {
	
	// 클래스 영역
	// 속성(필드)과 메소드를 작성할 수 있다.
	
	// 클래스 영역에 작성하는 변수를 필드라고 한다.
	// 필드 == 멤버 변수 == 전역변수(클래스 전역에서 사용 가능)
	
	// non-static field : 인스턴스 변수
	private int globalNum; // 인스턴스가 생성될 때 생성
	
	// static field : 정적 필드(클래스 변수)
	private static int staticNum; // 프로그램이 "실행" 될 때 생성
	
	
	public void testMethod(/* 매개변수 선언부 */int num) {
		// 메소드 영역
		// 메소드 영역 내에 선언하는 변수 : 지역 변수
		int localNum; // 메소드가 호출될 때 생성
		
		// 지역 변수는 반드시 초기화 되어 있어야 한다.
		localNum = 0;
		System.out.println(localNum);
		
		// 매개변수는 호출시 초기값이 전달되는 것이 보장되기 때문에 초기화가 필요 없다.
		System.out.println(num);
		
		// 전역변수는 클래스 전역에서 사용 가능하다.
		System.out.println(globalNum);
		System.out.println(staticNum);
		
	}
	
	public void testMethod2() {
		// 다른 메서드에서 선언한 지역변수 localNum은 사용 불가
		
		// 전역변수는 클래스 전역에서 사용 가능하다.
		System.out.println(globalNum);
		System.out.println(staticNum);
	}
}
// public class는 java파일 이름과 동일한 클래스에만 사용 가능
// 디폴트 클래스는 하나의 자바 파일에 여러 가지 작성할 수 있지만 사용하지 않는 것이 좋다.
```

### 변수의 초기화 순서
#### `인스턴스 변수` : JVM 기본값 -> 명시적 초기값 -> 인스턴스 초기화 블록 -> 생성자를 활용한 초기화
#### `클래스 변수` : JVM 기본값 -> 명시적 초기값 -> 정적 초기화 블록 -> 인스턴스 초기화 블록 -> 생성자
- 위와 같은 순서로 덮어 씌워지면서 초기화가 진행된다.

### 초기화 블록
1. 인스턴스 초기화 블록
```java
public class Initialization{
  {
    // 초기화 내용 작성
  }
}
```
- 인스턴스가 생성될 때마다 호출되며, 생성자 호출 이전에 먼저 호출된다.
- 초기화 블록을 사용할 경우, 반복문과 같은 식을 활용하여 초기화를 진행할 수 있다.
- 스태틱 필드도 인스턴스 초기화 블록에 의해 초기화가 가능하다.

2. 정적 초기화 블록
```java
public class InitializaionStatic{
    static{
        // 초기화 내용 작성
    }
}
```
- 클래스가 로드될 때 한 번 동작한다.
- 스태틱 필드를 초기화하며, 인스턴스 변수는 초기화하지 못한다. 