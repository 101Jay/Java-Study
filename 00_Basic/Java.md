# Java
### 자바가 해결하고자 했던 문제
#### 자바의 아버지 제임스 고슬링 팀은 어떤 이유로 자바를 만들고자 했을까?
<br>
기존의 언어는 컴파일러를 이용해 OS에 따라 개별적인 목적 파일을 만들어야 했다. 즉, 소스코드를 운영체제별로 따로 짜야했다.
<br><br>
고슬링 팀은 1991년 '그린 프로젝트'를 시작하며 운영체제별로 JVM(가상머신)을 만들어서 이러한 문제를 해결하고자 했다.
<br><br>
하나의 소스코드만 짜도, JVM이 알아서 OS별 다른 목적 파일을 만들어줌으로써 개발자들의 수고를 덜어줬다.
<br>

다시 말해, `WORA(Write Once Run Anywhere)`를 실현시켰다.
그 결과 이식성이 우수하고 운영체제에 독립적인 언어가 탄생하게 되었다. 

## JVM(Java Virtual Machine)
자바를 실행하기 위한 가상 기계로, 바이트 코드를 해석하고 실행하는 인터프리터.

자바 코드를 실행하는 구조는 다음과 같다
### Java Code -> Java Compiler -> Byte Code -> JVM 
먼저 .java 확장자를 지닌 자바 코드를 자바 컴파일러를 통해
자바 바이트코드로 컴파일한 뒤, 이를 JVM에 전달한다. 

### JVM은 어떻게 구성되어 있나?
`Class Loader`, `Runtime Data Areas`, `Execution Engine`으로 이루어져 있다.
<br><br>
---
### Class Loader의 특징
1. 계층 구조 : Bootstrap Class Loader - Extenstion Class Loader - System Class Loader - User-Defined Class Loader
- 부트스트랩 클래스 로더는 최상위 클래스로더로, 네이티브 코드로 구현되어 있다. JVM이 실행될 때 메모리로 올라가며, Object 클래스와 Java API를 로드한다.
- 익스텐션 클래스 로더는 확장 클래스들을 로드한다.
- 시스템 클래스 로더는 어플리케이션의 클래스들을 로드한다.
- 사용자 정의 클래스 로더는 개발자가 직접 코드상에서 생성하는 클래스 로더이다.
 

2. 위임 모델
- 클래스 로더가 필요한 클래스를 로드할 떄, 다음과 같은 순서로 위임하여 해당 클래스가 있는지 확인하게 된다.
- `클래스 로더 캐시` - `상위 클래스 로더` - `자기 자신` 
- 상위 클래스 로더에 클래스가 있다고 하더라도, 부트스트랩 클래스 로더까지 확인한 뒤 부트스트랩 클래스 로더에도 있다면 그것을 사용


3. 가시성 제한
- 위임의 과정에서 상위 클래스 로더를 확인할 때, 하위 클래스 로더의 클래스는 확인할 수 없다.


4. Unload 불가
- 클래스의 로드는 가능하지만, Unload는 불가능하다.


5. Name Space
- 각 클래스 로더가 가지고 있는 공간으로, 클래스를 보관한다. 
- FQCN(Fully Qualified Class Name)을 기준으로 보관됨 

---
#### Runtime Data Areas
`Method Area`, `Heap`, `Thread(Java Stack, PC Register, Native Method Stacks)s`로 구성되어 있다.
- Heap과 Method Area는 JVM 당 하나씩 존재한다. 

1. Method Area : 인스턴스 생성에 필요한 객체 구조, 생성자, 필드 등이 저장되며, 모든 Thread들은 하나의 Method Area를 공유하게 된다.

2. Heap : 코드 실행을 위한 Java로 구성된 객체가 포함되며, 모든 Java Stack 영역에서 참조된다.

3. Java Stacks : 각 Thread 별로 할당되며, Heap 영역보다 비교적 빠르다. Thread별로 따로 할당함으로 동시성 문제에서 자유롭다.
각 Thread는 메소드를 호출할 때마다 Frame이라는 단위를 Push하고, 결과 반환 후 Pop한다. Frame은 Local Variable, Operand Stack, Constant Pool Reference로 구성되어 있음.
Java Stack 영역에 가득 차게되면 Stack Overflow가 발생함으로 주의가 필요하다.

4. Native Method Stacks : Native Method란 Java가 아닌 다른 프로그래밍 언어로 작성된 메소드를 의미한다. 
Java Stack과 비슷하게 Native Method가 실행될 때 Native Method Stack에 쌓이게 된다.

5. PC(Program Counter) Registers: Thread들은 고유의 PC Registers를 가지게 되며, Thread별로 동시에 실행하는
환경을 보장하기 위해 JVM에서 명령어 주소값을 저장하는 공간으로 활용된다.