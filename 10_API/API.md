## API 
- Application Programming Interface
- 응용 프로그램에서 사용할 수 있도록 운영체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스

### Java에서 제공하는 API 중 자주 사용하는 클래스를 살펴보자

### Object 클래스
- 모든 클래스는 Object 클래스의 후손이다.
- Object 클래스가 가지고 있는 메서드 중 관례상 많이 오버라이딩 하는 메소드들
  - toString() / equals() / hashCode()

#### 1. toString() 
- 인스턴스가 가지는 타입을 풀 클래스명으로 하고 @를 구분자로 하여 뒤에는 16진수 주소값이 합쳐져 하나의 문자열로 반환하는 메소드.
- 사람이 쉽게 인지할 수 있는 구문으로 오버라이딩해서 사용한다. 
- 입출력 구문에서 `인스턴스만 쓰면` 자동으로 toString() 메소드를 쓰는 것으로 인지한다. 

#### 2. equals()
- 매개변수로 전달 받은 인스턴스와 해당 인스턴스를 `==` 연산하여 true or false의 결과 값을 반환하는 메서드
- 동일한 인스턴스인지 비교하는 기능을 제공
- 기본적으로 `동일객체`만 같은 것으로 인식한다. 
- 우리는 이를 오버라이딩해서, `동등객체`일 때도 true를 반환하도록 오버라이딩하여 사용한다. 
- 동등객체란 참조하는 주소 값이 다르더라도, 그 안의 값들이 같은 객체를 의미한다. 
```java
Book book1 = new Book("홍길동전");
Book book2 = new Book("홍길동전");
// book1과 book2는 동일객체는 아니지만, 동등객체이다.
```

#### 3. hashCode()
- equals 메소드를 재정의하는 경우 hashCode() 메소드도 재정의하도록 되어 있다.
- 그렇지 않을 경우, equals 메소드로 동등객체로 결과값이 나온 두 객체가 같은 해쉬코드 값을 가져야한다는 규약을 위반하게 된다.

---

### String 클래스의 자주 사용하는 메소드
#### charAt()
- 인자로 넘어온 숫자를 인덱스로 인식하고, 해당 문자열의 특정 인덱스에 해당하는 문자 반환
- 인덱스를 벗어난 정수를 인자로 전달하는 경우 예외 발생

#### compareTo()
- 인자로 전달된 문자열과 해당 문자열을 사전 순으로 비교하여 두 문자열이 같으면 0을 반환
- 인자 > 해당 문자열 : 음수 반환
- 인자 < 해당 문자열 : 양수 반환 
- 대소문자를 구분하여 비교한다.

#### concat()
- 문자열에 인자로 전달된 문자열을 합쳐 새로운 문자열 반환
- 원본 문자열에는 영향을 주지 않는다.

#### indexOf()
- 해당 문자열에서 특정 문자를 탐색하여 처음 일치하는 인덱스 위치를 정수형으로 반환
- 일치하는 문자가 없을 경우 -1을 반환

#### lastIndexOf()
- 문자열 탐색을 뒤에서부터 하고 처음 일치하는 위치의 인덱스를 반환
- 일치하는 문자가 없을 경우 -1을 반환

#### trim()
- 문자열의 앞, 뒤 공백을 제거한 문자열을 반환
- 원본 문자열에는 영향을 주지 않는다.

#### toLowerCase(), toUpperCase()
- 모든 대/소문자를 반대 방향으로 변환시킨다.
- 원본 문자열에는 영향을 주지 않는다.

#### substring()
- 문자열의 일부분을 잘라내어 새로운 문자열을 반환한다.
- 원본 문자열에는 영향을 주지 않는다.
```java
"helloworld".substring(2,4); // ll
// 2번 인덱스 문자부터 4번 인덱스 전 문자까지 잘라내서 반환
```

#### replace()
- 해당 문자열에서 첫 번째 인자로 넘어온 문자열과 일치하는 부분을 두 번째 인자로 넘어온 문자열로 변경해서 반환
- 원본 문자열에는 영향을 주지 않는다.

#### length()
- 문자열의 길이를 정수형으로 반환한다.
- 빈 문자열의 경우 0을 반환한다.

#### isEmpty()
- 빈 문자열이면 true, 그렇지 않으면 false
- 비어있는 문자열과 길이가 0인 문자열은 다름으로 주의

#### split(특정 기호, 잘라낼 수)
- 문자열을 특정 기호를 기준으로 잘라내어 배열로 반환한다.
- 두 번째 인자가 존재하면 해당 수만큼으로 문자열을 잘라낸다.

### StringTokenizer 객체
- java.util 패키지 안에 있는 객체로, 문자열 분리에 활용
- 구분자를 기준으로 나뉘어진 목록 생성
- 여러 구분자를 쓰고 싶을 때 대괄호 없이 /#* 와 같이 작성 가능
- 목록에서 한 번 꺼내어 사용했으면, 해당 목록으로는 재사용 불가
```java
public class Application {
  public static void main(String[] args) {
    java.lang.String example = "java/C++/C/javascript/dart";
    StringTokenizer stringTokenizer = new StringTokenizer(example, "/");

    System.out.println(stringTokenizer);
    System.out.println(stringTokenizer.nextToken()); // java
    System.out.println(stringTokenizer.nextToken()); // C++
    System.out.println(stringTokenizer.nextToken()); // C
    System.out.println(stringTokenizer.hasMoreTokens());
    System.out.println(stringTokenizer.nextToken()); // javascript
    System.out.println(stringTokenizer.nextToken()); // dart
    System.out.println(stringTokenizer.hasMoreTokens()); // false
  }
}
```

### escape sequence
- 역슬래스 ( \ ) 기호가 붙은 특수한 기능을 하는 문자 
-  \n : 개행문자, \t : 탭, \ ' : 작은따옴표, \ " : 큰 따옴표, \ \ : 역슬래쉬 등
- split() 메서드 사용시, 구분자로 특수문자를 사용할 경우, 정규표현식에 사용되는 특수기호($ ^ * ( ) + | { } [ ] . ?) 등은 escape sequence를 활용해 작성해줘야 한다.


### 문자열 객체를 만드는 방법
- 자바에서 문자열을 선언하는 방법은 다음 두 가지이다.
```java
// 1. 문자열 리터럴 생성
String str2 = "example";

// 2. new 연산자 활용한 문자열 생성
String str1 = new String("example");
```
#### 1. 리터럴 형태를 활용한 문자열 객체 생성
- 리터럴 형태로 만든 문자열 인스턴스는 단일 인스턴스로 관리한다.
- 따라서 주소 값을 비교하는 == 연산시 true를 반환한다.

#### 2. new 연산자를 활용한 문자열 객체 생성
- 같은 값을 가져도 기존 인스턴스가 아닌 새로운 인스턴스를 생성한다.
- == 연산시 false를 반환한다. 
- 그러나 hashCode() 메소드의 경우 String 객체 자체에서 동등객체일 경우 같은 값을 반환하도록 오버라이딩 되어 있기 때문에 같은 값은 인스턴스끼리는 같은 주소를 반환한다.
- hashcode를 기반으로 한 equals 연산 또한 동등객체일 경우 true를 반환한다.

#### 결론적으로 문자열 비교를 진행할 때는 == 연산이 아닌 hashcode 기반의 `equals 연산을` 사용해야 동등객체를 같다고 인식할 수 있다.

#### 문자열의 불변 특성
- 기존 문자열에 +(합치기) 연산을 수행하는 경우 문자열을 수정하는 것이 아닌 새로운 문자열을 할당하게 된다.
- 따라서 문자열을 계속 변경할 경우 새로운 문자열을 계속해서 할당하는 것임으로 성능이 저하될 수 있다.

### StringBuilder
- 기존 인스턴스를 수정하는 방식을 사용한다.
- capacity(), append(), delete(), insert(), reverse() 등의 메서드를 사용할 수 있다.
```java
public class Application {
    public static void main(String[] args) {
        
        StringBuilder sb = new StringBuilder("hello");
        String str = "hello";

//        str.append("hi"); // 불가
        sb.append("hi");
        System.out.println(sb);

    }
}
```

### Wrapper
- 원시 데이터 타입을 인스턴스화 해주는 클래스
- 기본 값을 값으로서 처리하는게 아니라 객체로서 처리해야 할 때 사용.
- 박싱과 언박싱
  - 박싱 : 기본 타입을 Wrapper 클래스의 인스턴스로 인스턴스화 하는 것
  - 언박싱 : Wrapper 클래스 타입의 인스턴스를 기본 타입으로 변경하는 것
```java
public class Application {
  public static void main(String[] args) {

    int value = 20;
    Integer boxingValue = Integer.valueOf(value); // Boxing
    int unBoxingValue = boxingValue.intValue(); // unBoxing

    System.out.println(value == boxingValue); // true
  }
}
```
- Java 1.5 부터는 박싱과 언박싱이 필요한 상황에서 컴파일러가 자동으로 처리해준다. (오토 박싱, 오토 언박싱)

### parsing 
- 문자열(String) 값을 기본 자료형 값으로 변경하는 것을 parsing이라고 한다.
```java
public class Application {
  public static void main(String[] args) {

    int example = Integer.parseInt("4"); // 문자열 값을 Integer로 parsing 
  }
}
```

### valueOf()
- 기본 자료형 값을 Wrapper 클래스 타입으로 변환시키는 메소드

### String 클래스의 valueOf()
- 각 자료형별로 오버라이딩 되어 있어서 

---

### Date
- Date 시스템으로부터 현재 날짜, 시간 정보를 가져와서 다룰 수 있게 만들어진 클래스

### Calendar와 이를 상속 받은 GregorianCalendar 
- Calendar는 추상 클래스로 만들어졌고, 이를 상속 받아 GregorianCalendar 클래스가 만들어졌다.

### Calendar 클래스의 활용 
- 추상 클래스이기 때문에 인스턴스를 생성할 수 없다.
1. getInstance() 메소드를 활용해서 생성
   - GregorianCalendar를 이용하여 구현되어 있다.
   - GregorianCalendar을 은닉하여 구현부에 변경이 생기더라도 사용하는 측에서는 변경하지 않도록 하기 위함

2. new GregorianCalendar() 를 활용한 생성
   - 다양한 생성자를 이용할 수 있도록 오버로딩 해놓음

- get(Calendar.YEAR); 등을 이용해서 해당 값을 가져올 수 있다. 

### SimpleDateFormat 객체 
- 원하는 포맷을 잡아주는 객체
- SimpleDateFormat smf = new SimpleDateFormat(”yyyy년 mm월 dd일”);