> - Break
> - Continue
> - do while 문
> - 서식지정자
> - 배열
> - oop

---
### Break 
- 중단
```java
int i = 1; // i 변수 1 초기화
while(true){ // 무한반복
System.out.println(i);
	if(i == 10){ // 변수 i 가 10이면
    	break; // 중단
    }
    i++; // 1씩 증가
}
```
---
### Continue 
- 이후 문단 건너뜀
```java
for(int i = 1; i <= 10; i++){ // 변수 i 1 초기화, i가 10보다 작거나 같을때까지, i는 1씩 증가
            if(i == 5){ // i가 5일 때
                i += 2; // i는 2씩 증가
                continue; // 현재 반복 종료
            }
            System.out.println(i); // i 출력
            if(i == 8){ // i 가 8 일때
                break; // 중단
            }
        }
```
---
### Do { 출력문 } While ( 조건식 );
- 한번은 실행하고 while 반복문

```java
int i = 0; // 변수 i 를 0으로 초기화
do { // 한번 실행 해보기
    System.out.println(i); // 변수 i 출력
    i++; // 1증가
} while(i <= 20); // 변수 i가 20보다 작거나 같으면, 조건이 false가 될때까지 반복
```
---
### 서식지정자 ( format )
- System.out.printf

**특수문자**
- \n 줄 바꿈
- \t tab

**서식문자**
- %d 10진수 정수
  - %?d:?만큼 왼쪽부터 공백으로 채워 출력
  - %.nf: 소수점 아래 n번째 자리까지 출력(반올림)
- %o 8진수 정수
- %x 16진수 정수
- %f 실수
- %c 단일문자
- %s 문자열
---
### 배열 ( Array )
- 자바 배열 객체 생성
```java
자료형 배열명 [] = new 자료형 [배열의 크기(정수)];
int [] arr = new int [10]; // arr이름으로 10개 int형 배열
```
- 배열 인덱스는 0번 부터 
```java
arr[0] = 100;
arr[1] = 200;
arr[2] = 300;
System.out.println(arr[0]); // 100
System.out.println(arr[1]); // 200
System.out.println(arr[2]); // 300
```
---
### oop ( Object Oriented Programming )
- 객체 지향 프로그래밍
  - 객체의 관점에서 프로그래밍하는 것
  - 객체 기준으로 코드를 나눔 ( 클래스: 데이터 속성 + 메소드(함수) )
  
- 특징
  > 1. 정보은닉 ( Informaion Hiding )
       - 캡슐화 ( Encapsulation )
       - Hiding
       - 디자인 패턴
  > 2. 추상화 ( Abstraction )
  > 3. 다형성 ( Polymorphism )
        - OverRiding
        - OverLoading
  > 4. 상속 ( Inheritance )

1. 
   - 클래스로 객체를 만들어 객체 내에서 일어나는 행위 은닉
   - {접근지정자(public, private, protected, default): 외부 클래스가 참조 클래스 범위를 지정 }
ex) 개발자는 알지만 사용자 기준 리모컨과 누르는 버튼 + 작동만 하면 됨


2. 
   - 객체들의 공통된 속성과 기능을 추출하여 핵심만 표현하고, 세부 구현은 숨기는 것 ( 추상 클래스 abstract, interface 로 추상화 ) 
   

3. 
   - 형태는 같지만 다른 기능을 하는 특징
   
 **오버라이딩**
 부모 클래스에서 만든 메소드(함수)를 자식클래스가 재정의( 기존 부모 클래스를 바탕으로 자식클래스에서 이름, 매개변수, 반환타입으로 클래스 재정의 ) ex) implements
  
 
 **오버로딩**
 메소드(함수)의 명은 같지만 메게변수, 데이터 타입이 다르면 오버로딩 사용됨 
 
4. 
   - 기존(부모 )클래스를 바탕으로 새로운( 자식 )클래스에 새로운 기능 추가할 수 있음 ( extends ) + 3번 