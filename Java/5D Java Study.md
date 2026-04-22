> - 메모리 구조
> - 클래스
> - 구구단 클래스
> - this

### 메모리 구조
> **스택 ( Stack )**
함수 ( method )가 실행이 되면 지역변수 저장, 함수가 끝나면 자동으로 스텍에 저장된 값은 삭제됨
- 자동으로 할당하고 자동으로 삭제됨
---
> **힙 ( Heap )**
new 키워드를 사용한 정의한 객체 저장, 사용자 정의 클래스 가 저장됨, 프로그램이 끝나면 값 삭제됨
- 수동적으로 할당하고 수동( 객체명.close ( ) )으로 삭제해야 실행 중인 프로그램 속도에 영향을 주지 않을 수 있음

### 클래스 ( Class )
- main 클래스는 없으면 오류, 제일 먼저 시작하는 클래스
- 데이터 속성, 함수로 클래스 정의를 할 수 있음
- 사용자 정의 클래스를 다른 클래스나 main클래스에 사용하려면 객체를 생성 후 객체명으로 함수, 변수를 사용할 수 있다.
```java
    public class Main {
    	public static void main(String[] args) {
    
    Person personA = new Person(); // Person 청사진으로 personA 객체 생성

        personA.age = 30;
        personA.name = "mong";
        personA.stage = "buttom";
        personA.married = false;
        System.out.printf("나이 %d, 이름 %s, 사는 곳 %s, 결혼여부 %b\n ", personA.age, personA.name, personA.stage, personA.married); // 나이 30, 이름 mong, 사는 곳 buttom, 결혼여부 false

        personA.selfPromote(); //personA객체의 selfPromote함수 호출
    
    }
}
class Person { //Person 청사진 class 정의

	int age; // int형 age변수
    String name; // String형 name 변수
    String stage; // String형 stage 변수
    boolean married; // boolean married 변수
    
    void selfPromote(){ // selfPromote 함수 정의
    	System.out.println("나이는 " + age + "이고 이름은 " + name + "입니다.");
    }
 }

```

### 구구단 클래스(세로, 가로)

```java
class 구구단출력기{

    // 세로 출력
    void 작동1(){
        for(int i = 2; i <= 9; i++){
            System.out.printf("== %d단 ==\n", i);
            for(int j = 1; j <= 9; j++ ){
                System.out.printf("%d * %d = %d\n", i, j, i * j);
            }
        }
        System.out.println();

    }

    // 가로 출력
    void 작동2(){
        for(int i = 1; i <= 9; i++){
            for(int j = 2; j <= 9; j++ ){
                System.out.printf("%d * %d = %d", j, i, j * i);
                System.out.printf("\t");
            }
            System.out.println();
        }
    }
}
```

### this
- 자신 객체를 가리키는 참조변수
🎃 정의된 클래스의 변수를 함수, main클래스, 다른 클래스에 사용하려면 사용할 변수를 할당을 하기 위해 this 키워드로 변수에 지정 할당을 해줘야 한다. 
🎃 this로 변수를 지정 않하면 클래스마다의 변수가 충돌을 일으켜 값이 의도대로 나오지 않는다.
``` java

 public class Main {
    public static void main(String[] args) {
    
    int age = 90;

	사람 행인 = new 사람();
   
    행인.setage();

    }
}

class 사람 {
	int age = 20;
    String name = "홍길동";
    
    void setage(){
    int age = this.age; // 사람 class의 변수를 setage함수 지역변수에 저장, 20출력
    
   // this.age = age; // 실행되는 현제class main 에서 age변수를 setage지역변수에 저장, 90출력
    
    System.out.println("내 나이는" + age + "이다.");
    
    }
}
```

