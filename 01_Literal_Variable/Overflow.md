### Overflow 
- 데이터 오버플로우 : 변수의 자료형별로 허용된 양의 범위를 넘게되는 것.

#### 오버플로우가 발생하면 자바에서는 어떻게 처리할까?
- 발생한 carry(올림)를 버림처리하고 sign bit를 반전시켜 최소값으로 순환시킴
```java
byte num1 = 127;
num1++;
System.out.pringln(num1); 
// -128
```

### Underflow 
- 데이터 언더플로우 : 변수의 자료형별로 허용된 음의 범위를 넘게되는 것

#### 언더플로우가 발생하면 자바에서는 어떻게 처리할까?
- sign bit를 반전시켜 최대값으로 순환시킨다.
````java
byte num1 = -128;
num1--;
System.out.println(num1);
//127
````

- 예제 코드
```java
int firstNum = 100000;
int secondNum = 70000;

int multi = firstNum * secondNum;

System.out.println(multi);
// -798989...
// 오버플로우가 발생했구나!를 알고 있으면 됨.
```

#### 해결방안
- 오버플로우/언더플로우 상황을 예측하고 보다 더 큰 자료형을 사용해준다.
```java
long result = (long) firstNum * secondNum;
//큰 값에 맞춰서 연산을 하기 때문에 가능.
```

