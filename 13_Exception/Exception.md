### 오류 vs 예외

- 오류 : 프로그램에 심각한 문제를 발생하여 실행중인 프로그램이 종료되는 것
- 예외 : 오류와 마찬가지로 비정상적으로 프로그램을 종료시키지만 미리 예측하고 처리할 수 있는 미약한 오류

### RuntimeException과 IOException

- RuntimeException : 예외처리 문법을 적용하지 않아도 됨
- IOException : 예외처리가 강제되는 에러(checked exception)

### RuntimeException의 후손 클래스들

- ArithmeticException , NullPointerException, NegativeArraySizeException, ArrayIndexOutOfBoundsException, ClassCastException(잘못된 형변환)
- if문으로 처리할 수 있는 정도이기 때문에 굳이 try / catch 문법을 사용하지 않아도 됨.(if를 통해 오류가 발생하지 않도록 사전 예방)
- 이 외의 것들에 대해 예외 처리.

---

### 예외처리란?

- 예외가 발생했을 때, 프로그램의 원래 흐름대로 돌려놓는 것.
- 예외처리 방식
1. thorws로 위임
    - Exception 처리를 호출한 메소드에게 위임
    - 메소드 선언 시 throws ExceptionName문을 추가하여 호출한 상위 메소드에게 처리를 위임
    ```java
    public void checkMoney(int price, int momey) throws Exception{}
    ```
    - 오류 발생시 이 메소드의 동작을 멈추고 이 메소드를 호출한 영역으로 위임.(폭탄 던지기)
2. try-catch로 처리
    - Exception이 발생한 곳에서 직접 처리
    - try : exception 발생할 가능성이 있는 코드를 안에 기술
    - catch : try 구문에서 exception 발생시 해당하는 exception에 대한 처리 기술. 여러 개의 exception처리가 가능하나 exception간의 상속 관계를 고려해야 한다.
    - finally : exception 발생 여부와 관계없이 꼭 처리해야 하는 로직 중간에 return문을 만나도 finally구문은 실행되지만 System.exit()를 만나면 무조건 프로그램 종료. 주로 java.io나 java.sql 패키지의 메소드 처리시 이용
    - 원래 흐름으로 복귀 시킬 목적.
        ```java
        try {
        	System.out.println("상품 구입 가능");
        }catch(Exception e) {
        	System.out.println("상품 구입 불가");
        }
        
        System.out.println("프로그램 계속 진행");
        ```
    - 에러 발생 즉시 catch 블록으로 넘어가고, catch 블록을 실행한 뒤 원래 흐름대로 복귀 시킴
    - 일반적으로 해당 메소드를 사용하는 측에서 try - catch로 처리함.