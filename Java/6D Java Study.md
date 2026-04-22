>- .nextInt() 주의할 점 🧠
>- static
>- return



### 객체명.nextInt() 입력예외처리
- 객체명.nextInt(); 는 개행 이후 입력을 받을 때 줄바꿈이 먹히지 않아서 InputMismatchException오류
1. Integer.parseInt(객체명.nextLine());을 이용해서 해결


### static
- 정적맴버키워드, 모든 메로리가 참조 가능, 객체를 생성하지 않고 선언한 클래스의 함수를 사용한다면 함수명 앞에 static키워드를 넣는다.
```java
// main class
	car.alram();
// user define class
class car{
	static void alram(){
    	System.out.println("경적이 울립니다.");
    	}
    }
```

### return
- 함수의 void 를 제외하고 기본자료형 타입으로 함수를 생성을 할 때 return 값이 필요하다.
```java
//main class..
System.out.println(계산기.plus(4,6)); // 10 출력
// user define class
class 계산기{
	static int plus(int a, int b){ // a, b는 함수를 사용할 때 값을 받는 인자값 위치
    		return a + b; // int형으로 함수를 선언을 하면 int 형으로 return(타입 일치)
    }
}
```

