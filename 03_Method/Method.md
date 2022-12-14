## 메서드(Method)
#### : 특정 작업을 수행하기 위한 명령문의 집합
- 사전에 미리 만들어 놓은 기능을 외부에서 사용할 수 있도록 만들어 놓은 것
- 사용자는 메서드 내부가 어떻게 구현되어 있는지 알 필요 없이 메서드를 활용할 수 있다.
- 메소드는 또 다른 메소드를 호출할 수 있다.
- 메소드 호출이 종료되면 메소드를 호출한 곳으로 다시 돌아간다.

#### 메서드 명명 규칙
- 첫 문자는 소문자로 시작하며, 동사형, 명령형으로 작성한다. 

#### 전달인자와 매개변수 
- 메서드 실행시 외부에서 메서드로 전달하는 값을 `전달인자`라고 한다.
  - 변수를 전달인자로 넘길 수 있다.
  - 자동형변환, 강제형변환을 이용하여 값을 전달할 수 있다.
  - 연산 결과를 이용하여 값을 전달할 수 있다.
- 외부에서 전달한 전달인자를 메서드 내부에서 받아서 사용하기 위해 선언하는 변수를 `매개변수`라고 한다.
- `매개변수`도 Stack에 생성되며, 개수나 자료형의 제한은 없다. 상수(`final`)도 사용 가능하다.
```java
methodA(50) // 50은 전달인자

public void methodA(int var){
		System.out.println(var);
} // var는 매개변수
```
#### return
- 메서드 내부에서 해당 메서드를 종료하고, 자신을 호출한 메소드로 돌아가는 예약어
- 반환값과 함께 return 한다면 해당 값을 가지고 메서드를 호출한 곳으로 돌아갈 수 있다.

#### 메서드 호출과 메모리 구조
- 메인 메서드에서 다른 메서드를 호출할 경우, Stack에서 메인 메서드 위로 해당 메서드가 push됨
- 해당 메서드가 return되면 Stack에서 해당 메서드가 pop됨

#### static 
- `static`이란 여러개의 객체들이 공유하는 영역.
- `static` 키워드가 있는 메소드는 `클래스명.메서드명`으로 호출함.
- 같은 클래스 내의 static 메소드는 클래스명을 생략하고 사용할 수 있다.
1. non-static 메서드 호출
   - ```java
     ClassA classA = new ClassA(); // 클래스 선언
     classA.methodA(); // 메서드 호출
     ```
2. static 메서드 호출
   - ```java
     ClassA.methodA(); // 선언 없이 바로 호출 가능
     ```

#### 패키지와 임포트
- 패키지 : 서로 관련 있는 클래스 또는 인터페이스의 묶음 
  - 다른 패키지에 존재하는 클래스를 사용하는 경우에는 반드시 패키지를 포함한 풀 클래스 명을 사용해야 한다.
  - 그러나 쓸 때마다 그러면 너무 귀찮을 것 같은데?
- 임포트 : 서로 다른 패키지에 있는 클래스나 인터페이스를 사용하는 경우에도 패키지명을 생략하고 사용할 수 있도록 미리 선언해놓는 것
  - 어떠한 패키지 내에 있는 클래스를 사용할 것인지에 대해 미리 선언하는 효과를 갖는다. 

---

### 자바에서 제공하는 라이브러리에 있는 클래스
### 1. 난수를 발생시키는 Math와 Random
#### Math를 활용한 난수 발생
```java
int random1 = (int) (Math.random() * 10);
// 강제 형변환으로 소수점 이하 생략 가능.
// 0 ~ 9 까지의 정수 형태의 난수 발생

int random2 = (int) (Math.random() * 10) + 1;
// 1 ~ 9

int random3 = (int) (Math.random() * 6) + 10;
// 10 ~ 15

int random4 = (int) (Math.random() * 256) - 128;
// -128 ~ 127
```
- Math는 java.lang 패키지에 속해 있기 때문에 따로 import 하지 않고 그대로 사용할 수 있다. 
- `범위의 갯수`를 곱해준 뒤, 해당 위치를 만들어주기 위해 더하거나 빼준다.
<br><br><br>

#### Random을 활용한 난수 발생 
```java
import java.util.Random;

...

Random random new Random();

int randNum1 = random.nextInt(10);
```

### 2. 자료형 입력을 위한 Scanner 
- Scanner 객체 생성
```java
import java.util.Scanner
...
Scanner sc = new Scanner(System.in);
```
- 값 입력 받기
```java
System.out.println(" ~ 입력해주세요! : ");
String name = sc.nextLine();
int age = sc.nextInt();
float height = sc.nextFloat();
```
#### nextLine() vs next()
- `nextLine()` : 말 그대로 한 문장, 즉 개행문자 전까지를 읽는다. 이때, 공백을 포함한다.
- `next()` : 공백 문자나 개행 문자 전까지를 읽어서 문자열로 반환. 공백을 포함하지 않는다.