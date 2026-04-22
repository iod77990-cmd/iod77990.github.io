>- 상속
>- 형 변환
>- 오버로딩

### 상속 ( Inheritance )
* 부모클래스를 바탕으로 extends 키워드를 사용해서 자식클래스가 상속을 받음
```java
// main
mom child = new child();

child.밥 먹어라();

class mom{

void 밥 먹어라(){

		System.out.println("밥 먹어라");
	}
}

class child extends mom{

void 밥 먹어라(){ // overriding, 같은 함수명으로 다른 기능을 출력
		System.out.println("지금 소화가 안되서 나중에 먹을게요.");
        
	}
}
```

### 형 변환 ( Type Casting )
- 자동 형변환(up casting)과 수동 형변환(down casting)
   - 강제 형변환..(자료형)
```java
double a = 8; // 실수형 a변수에 int형 8 대입하면 오류가 뜨지 않으며, 자동 형변환이 일어난다.
System.out.println(" a는 뭘까?.. " + a); // 8.0 출력

// main 클래스
커피 c = new 카페라떼(); // 부모 클래스로 자식클래스 생성 ( 업 캐스팅 )
        카페라떼 latte = (카페라떼) c; // 자식클래스로 부모클래스로 변환 ( 다운 캐스팅 )
        latte.우유추가(); // 자식 기능 사용

class 커피 {
    void 원두() {
        System.out.println("커피입니다");
    }
}
class 카페라떼 extends 커피 {
    void 우유추가() {
        System.out.println("우유가 들어간 라떼입니다");
     }
}
```

### 오버로딩 ( Overloading )
- 상속받은 자식클래스의 함수에 매개변수(타입, 개수, 순서)를 서로 다르게 부여해서 구현하는 방식
   - 아메리카노에 거품우유를 넣으면 카페라떼, 헤이즐넛 시럽을 넣으면 헤이즐넛 커피
```java
// main클래스
System.out.println("뭐 마실래?");
아메리카노 커피 = new 아메리카노();
커피.커피(String 스팀우유);
System.out.println("나는 카페라떼 먹을게 ");

class 아메리카노{
    void 커피 () {
    	System.out.println("나는 따뜻한 커피입니다.^^");
    	}
	}
    class 카페라떼{
    	void 커피(String 스팀우유) {
        	System.out.println("나는 따뜻한 카페라떼입니다.");
        }
    }
    class 헤이즐넛 커피{
    	void 커피(String 헤이즐넛 시럽) {
        	System.out.println("아메리카노에 헤이즐넛 시럽이 들어간 달달한 커피");
        }
    }
```
