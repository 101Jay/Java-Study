## 제어문
- 프로그램의 흐름을 사용자의 입력에 따라 제어하는 문장
- `조건문`, `반복문`, `분기문`

### 1. 조건문
- `if`, `switch`
- `switch`문은 조건문임에도 분기문(break)를 사용한다는 특징이 있다.
  - break를 적절하게 사용하지 못할 경우 모든 경우의 수에 해당하는 프로그램이 수행될 수 있음에 주의하자

### 2. 반복문
- `for`, `while`
- 반복문을 쓰기전에 먼저 쓰지 않고 프로그램을 구성해보고, 규칙을 확인한 뒤 사용하자
- `do while`을 사용할 경우, `do` 내부의 변수를 while 조건에서 사용할 수 없기 때문에 반약 함께 쓰고 싶다면 미리 선언해둬야 한다.
```java
public void testDoWhile() {
    Scanner sc = new Scanner(System.in);
    String str = "";
    do {
        System.out.print("문자열을 입력해주세요 : ");
        str = sc.nextLine();
        System.out.println(str);
    }while(!str.equals("exit"));
}
```
### 3. 분기문 
- `break`, `continue`
- `break` : 반복문 내에서 해당 반복문을 빠져 나오기 위해 사용하며, 반복문 자체의 조건식의 결과와 상관 없이 빠져 나온다.
  - switch문은 반복문이 아니지만 break를 사용한다.
  - `label`의 활용 : 반복문이 여러 개 중첩되어 있다면 탈출하고자 하는 반복문을 명시하기 위해 `label`을 사용한다.
    - ```java
      label:
      for(;;) {
        for(int i = 0; i<10; i++) {
            System.out.println(i);
            if(i==3) {
                break label;
            }
        }
      }
      ```
    - `label`은 프로그램의 흐름을 사람의 인지 영역에서 벗어나게 만들 수 있기 떄문에 잘 쓰지 않는다.
- `continue` : 반복문 내에서 해당 반복 회차를 중간에 멈추고 다음 회차(조건식을 거쳐서)로 넘어가게 해준다.

