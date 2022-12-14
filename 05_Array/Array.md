## 배열
- 같은 자료형의 변수들을 하나의 묶음으로서 다룰 수 있다.
- 연속된 메모리 공간에 값을 저장하고 사용할 수 있다.
- 반복문을 이용한 처리가 가능하다. 
- 배열도 하나의 객체라고 볼 수 있다. 따라서 데이터와 메소드를 갖는다. 

### 배열 선언
- 배열 선언시 Stack에 배열의 주소를 보관할 수 있는 공간을 만든다.
- 선언시 사용한 변수는 주소 값을 보관할 수 있는 레퍼런스 변수가 된다. 

### 배열 할당
- heap 영역에 실제 값들을 할당한다.
- 반환 값으로는 해당 heap 영역의 시작 주소 값을 반환해준다. 

### 배열 초기화 
- for문을 활용하여 초기화한다.
- 초기화하지 않으면 자료형의 기본값을 담게 된다.(String의 경우 자체가 참조형이기 때문에 null로 초기화 된다.)

### Heap 영역의 구조
- Eden -> Survive -> Survive2 -> Old
- 참조연산자가 덮어 씌워진, 즉, 더이상 참조할 수 없는 Heap 영역의 값은 위의 순서로 Heap 영역내에서 이동하게 되고,
Old에 가게되면 GC(Garbage Collector)에 의해 삭제된다. 
- 예를 들어, 배열 값을 가지고 있던 참조형 변수 arr에 null 값을 넣게되면, 덮어 씌워진 배열은 위의 순서로 삭제된다.

### 2차원 배열
- 자료형이 같은 1차원 배열들의 묶음을 의미한다.
- 할당된 공간마다 인덱스를 2개씩 부여한다.(행, 열)
- 길이가 서로 같은 배열들의 모임을 정변 배열이라 하고, 그렇지 않은 배열을 가변 배열이라고 한다.
- 2차원 배열의 초기화는 이중 for문을 활영하여 수행할 수 있다.

### 배열 복사
#### 1. 얕은 복사
- 객체의 `주소 값만 가져와` 참조형 변수에 저장하고, 이를 공유해서 참조할 수 있다.
- 결국 같은 주소를 갖은 참조형 변수가 2개가 되는 것이기 때문에, 한 쪽에서 수정하면 다른 쪽에서도 변경된 결과 값을 받게 된다.
- 활용 : 메소드의 전달인자로 주소 값을 전해주면, 이를 매개변수로 활용해 해당 주소에 접근할 수 있고, 이를 통해 배열에 변화를 줄 수 있다.

#### 2. 깊은 복사
- 새로운 배열을 Heap 영역에 할당해서 그 값들을 새로운 배열로 담아내는 것
- 즉, `새로운 배열 객체`를 생성하여 기존 배열의 데이터를 복사한다.
- 깊은 복사한 참조형 변수는 서로 다른 주소 값을 가지고 있다.
- 깊은 복사의 방법 : 
  - for 문을 활용하여 인덱스의 값을 복사한다.
  - Object의 clone() 메서드를 이용하여 복사한다.
  - System.arraycopy() 메서드를 활용하여 복사한다.
  - Arrays.copyOf() 메서드를 활용하여 복사한다. 
    - ```java
      int[] copyArr4 = Arrays.copyOf(originArr, 7);
      ```
---
#### 향상된 for문
```java
for(int i : arr2){
    system.out.println(i);
} // 배열 arr2에 저장된 값들을 i에 하나씩 꺼내와서 출력
```
- 깊은 복사를 활용

#### 변수의 값 교환
```java
int num1 = 1;
int num2 = 2;
int temp = num1;
num1 = num2;
num2 = temp;
``` 
- 임시 변수를 활용하여 num1과 num2의 값 교환

#### 정렬
- 여러 가지 정렬 방법이 존재
- 순차정렬 : 배열의 처음과 끝을 탐색하며 순서대로 값을 교환하는 알고리즘
```java
public static void main(String[] args) {
    int[] arr = {5,2,1,4,3,7,6};
    int temp;
    
    for(int i = 0; i < arr.length; i++) {
        for(int j = 0; j < i; j++) {
            if(arr[j] > arr[i]) {
                temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp; 
            }
        }
    }
    for (int i = 0; i < arr.length; i++) {
        System.out.println(arr[i]);
    }
}
```