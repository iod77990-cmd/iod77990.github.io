오전 9:55 2026-04-23

- 가변인자

### 가변인자
함수의 매개변수 개수를 고정하지 않고 호출할 때마다 동적으로 인수를 전달받을 수 있도록 하는 기능

특징) 
1. 가변인자는 항상 마지막에 선언 : 함수에 다른 매개변수가 있으면 가변인자는 반드시 매개변수 목록의 가장 끝에 위치

2. 함수당 하나만 사용 : 함수 하나 안에 2개 이상의 가변인자를 선언할 수 없다.

사용하는 이유 ) 
1. 코드 중복 감소
동일한 기능을 처리하는데 오버로딩 메서드를 만들 필요가 없다.

2. 가독성 향상
몇 개의 데이터가 들어올지 모르는 상황에서 코드를 깔끔하게 유지할 수 있다.

주의)
가변인자 함수는 호출될 때마다 배열을 생성하므로 반복문 내부에서 남용하지 않는 것이 좋음

방법) 
타입... 변수명 형태로 선언
함수 안에서는 일반적인 배열처럼 생성됨
호출할 때 , 로 구분해서 넣기만 하면 배열로 묶여서 들어옴

- 쇼핑몰 장바구니 합계 구하기
```java
public class Shop {
    public static void main(String[] args) {
        int total = calculateTotal(15000, 2000, 5000); 
        System.out.println("총 결제 금액: " + total + "원");
    }

    public static int calculateTotal(int... prices) {
        int sum = 0;
        for (int price : prices) {
            sum += price;
        }
        return sum;
    }
}
```

- 반 이름과 학생들(고정 매개변수와 함께 쓰기)

```java
public class School {
    public static void main(String[] args) {
        printClassStudents("1반", "사과", "배", "포도");
    }

    // String className은 고정, 그 뒤는 가변
    public static void printClassStudents(String className, String... students) {
        System.out.print(className + " 명단: ");
        for (String student : students) {
            System.out.print(student + " ");
        }
    }
}
```

