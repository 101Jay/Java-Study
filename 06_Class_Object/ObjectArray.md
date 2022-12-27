### 객체 배열
- 레퍼런스 변수에 대한 배열
- `동일한` 타입의 인스턴스 변수를 관리할 수 있는 배열

```java
// Car라는 클래스가 있다고 가정
public class Application {

    public static void main(String[] args) {

        Car[] arrayCar = new Car[5];
        arrayCar[0] = new Car("테슬라", 100);
        arrayCar[1] = new Car("아반떼", 200);
        arrayCar[2] = new Car("소나타", 150);
        arrayCar[3] = new Car("람보르기니", 200);
        arrayCar[4] = new Car("페라리", 400);

        for(int i = 0; i < arrayCar.length; i++) {
            arrayCar[i].driveMaxSpeed();
        } // for문을 활용해 객체 배열 각 원소들의 메소드 사용

        // 선언과 동시에 객체 배열을 할당시키는 방법.
        Car[] carArray = {
                new Car("테슬라", 100)
                , new Car("아반떼", 200)
                , new Car("소나타", 150)
        };

        for(Car c : carArray) {
            c.driveMaxSpeed();
        }
    }
}
``` 
- 객체 배열 사용시에는 각각 원소마다 새롭게 객체를 할당해 줄 필요가 있다.