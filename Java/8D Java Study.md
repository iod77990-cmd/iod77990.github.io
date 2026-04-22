
>- 추상클래스
>- 인터페이스
>- 생성자 ( super(), 오버로딩 )

### 추상클래스 ( Abstract class )
- abstract 키워드를 넣어서 공통된 부분만 넣고 이후 차이점만 자식클래스에 구현을 하기 위한 방식
```java
abstract class 커피 {
	abstract void 원두();
}
class 카페라떼 extends 커피{
	void 원두(){
    	System.out.println("스팀우유를 넣은 카페라떼");
    }
}
class 카페모카 extends 커피{
	void 원두(){
    	System.out.println("초코시럽 추가한 카페모카");
    }
}
class 카라멜마끼아뚜 extends 커피{
	void 원두(){
    	System.out.println("카라멜 시럽과 스팀우유 추가한 카라멜마끼아뚜");
    }
}
```

### 인터페이스 ( Interface )
- implements 키워드로 여러 부모들에게 자식클래스가 다중상속 가능, 상속받은 클래스는 오버라이딩을 필수로 해야 한다.
```java
interface 저금통{
	void 돈();
}
class 입금 implements 저금통{
	public void 돈(){
    	System.out.println("얼마?");
    }
}
class 금전확인 implements 저금통{
	public void 돈(){
    	System.out.println("저금통 들어 확인");
    }
}
class 출금 implements 저금통{
	public void 돈(){
    	System.out.println("돈 내놔");
    }
}

```

### 생성자
- new 키워드로 객체를 생성 후에 생성된 클래스로 제일 먼저 실행이 되는 함수(정의한 클래스 안에 존재함)
- 명시적 호출이 안되고 객체가 생성될 때 자동으로 호출
- 리턴타입이 없음, this() 함수는 생성자에서만 가능
```java
class 전사 {
    String 이름;
    int 나이;
    무기 a무기;

    전사 ( ) { // 기본 생산자 ( default )
        // 아무 기능 없음
    }
}
```
- 연쇄호출
  - super ( ); 자식클래스에서 부모클래스의 함수를 호출을 하는 함수
```java
main 클래스..
아메리카노 커피1 = new 아메리카노();
아메리카노 커피2 = new 아메리카노("홍길동", 4500); // 인수 있는 아메리카노 함수를 찾아서 실행 

class 아메리카노 {

void 재료추가(){

	System.out.println("넣을 재료 없음");
    
}
	
  void 아메리카노(){
	System.out.println("아메리카노 입니다.");
    }
    
  void 아메리카노(String name, int price){
  	System.out.printf("%s이 주문한 %d원짜리 커피가 나왔습니다.", name, price); 
    
    // 두 함수 중에서 하나는 주석처리하면 정상실행
    
  } // 생성자 오버로딩
}

class 라떼 extends 아메리카노{
	
    void 재료추가(){
    	super(); //  부모클래스의 함수가 실행이 됨
        
        System.out.println("스팀우유 추가해서 따뜻한 카페라떼 나옴");
    
    }
    
}

```
