## 제네릭(Generic)
데이터의 타입을 일반화하는 것
- 클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 지정하는 방법을 말한다.
  - 컴파일 시에 미리 타입 검사를 시행하게 되면 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성을 높일 수 있다.
- primitive type은 올 수 없으며, Reference type이나 사용자 정의 클래스는 활용 가능하다.
- 제네릭을 활용하면 타입 변환 및 타입 검사에 들어가는 코드 생략이 가능하다.
  - instanceof를 활용한 타입 변환 및 타입 검사에 들어가는 코드 생략이 가능
- 제네릭 클래스에 extends 키워드를 사용해 타입 변수에 올 수 있는 자료형을 제한할 수 있다.
  - extends로 명시한 해당 자료형을 상속 받은 후손들만 오도록 한다.

### Generic Method 
- 기본적으로 static 메소드는 인스턴스화 전에 메모리에 올라가기 때문에 제네릭 타입을 쓸 수 없다.
- 이럴 때 사용하는 것이 Generic Method이다. 
- 제네릭 메소드는 호출시에 타입을 지정한다.
- 이 때, 클래스의 Generic 타입과는 같은 변수명을 쓰더라도 다르다는 점을 주의하자.
```java
// Generic Class 예시
public class GenericTest<T> {
    private T value; // 아직 결정되지 않은 타입의 변수

    public void setValue(T value) {
        this.value = value;
    }
    public T getValue() {
        return this.value;
    }
    
    // 클래스와는 독립적인 또 다른 제네릭 타입 E
    public static <E> E genericMethod(E element){
        return element;
    }
}

public class Application {
    public static void main(String[] args) {

        GenericTest<String> testString = new GenericTest<String>();
        GenericTest<Integer> testInt = new GenericTest<Integer>();

        testString.set("10");
        testInt.set(10);

        System.out.println("testString data : " + testString.get());
        System.out.println("testInt data : " + testInt.get());
    }
}
```

```java
// extends 키워드를 사용해 타입 변수 T에 올 수 있는 자료형을 제한할 수 있다.
public class RabbitFarm<T extends Rabbit>{}
```
---
### 와일드카드(wildcard) : <?>

제네릭 클래스 타입의 객체를 메소드의 매개변수로 받을 때 그 객체의 타입 변수를 제한할 수 있다.

### 1. `<?>` : 제한 없음
- 어떠한 타입을 이용해서 생성했는지 제한 없음
```java
public void anyType(RabbitFarm<?> farm){}
```
- 즉, RabbitFarm이기만 하면 됨.

<br>

### 2. `<? extends Type>` : 상한 제한
- Type과 Type의 후손을 이용해 생성한 인스턴스만 인자로 사용 가능
```java
public void extendsType(RabbitFarm<? extends Bunny> farm){
}
```
- 즉, Bunny 또는 그 후손을 이용해 생성한 RabbitFarm만 올 수 있음.

<br>

### 3. `<? super Type>` : 하한 제한
- Type과 Type의 부모를 이용해 생성한 인스턴스만 인자로 사용 가능
```java
public void superType(RabbitFarm<?> farm){}
```
- Bunny와 그 조상들을 이용해 생성한 RabbitFarm이어야 함.

