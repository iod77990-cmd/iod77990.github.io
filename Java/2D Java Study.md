
> - 조건문 ( if ( ) { } else if ( ) { } else { } )
> - 증감 연산 ( + + i, i - - ... )
> - 반복문 ( while, for )


### 조건문
``` java
if ( 조건문 ) // 조건문에 하나의 조건만 들어감
	{ 출력문 } // 조건문이 참일 때 출력문 출력 	
else if ( 조건문 || ( or ) && ( and ) 조건문 ) // 논리연산자를 사용한 2개 이상 단일 조건문 비교 가능
	{ 출력문 } 
else
	{ 출력문 } // 위 조건문 통과하고 참이 없었다면 else { 출력문 } 출력
```
- - -
* 조건문 안에 논리연산자를 사용하지 않은 2항 이상 조건문은 실행 오류 ❌
* if ( 조건 ) { 출력 } else if ( 조건 ) { 출력 } 에 조건문에 참이면
	이후 else if ( 조건문 ) { 출력문 }, else { 출력문 } 실행 안함 ❌
```java
🎃 int age = 20;

if ( age <= 19 ){
        System.out.println("할인 대상 입니다.");
      }
      else if (20 < age < 60){ // 연속 작성된 조건문 실행 오류 ❌ ?) 20 < age 가 boolean(true or false)으로 변환되고 boolean < 60 은 타입 불일치
          System.out.println("할인 대상이 아닙니다.");
      } // 20 < age 가 false < 60 타입이 달라 오류
      else {
          System.out.println("할인 대상 입니다.");
      }
```
```java
🎃 int age = 20;

if ( age <= 19 ){ // 조건문 거짓, 출력문 실행 안함
        System.out.println("할인 대상 입니다.");
      }
      else if ( 19 < age ){ // 출력문 실행
          System.out.println("할인 대상이 아닙니다.");
      }
      else if ( age < 60 ){ // 실행 안하고 종료 ❌
          System.out.println("할인 대상이 아닙니다.");
      }
      else { // 실행 안하고 종료 ❌
          System.out.println("할인 대상 입니다.");
      }
```
- - -

### 증감 연산
```java
int i = 0;
int a = 2;

++i; // i + 1 출력
i++ // i 출력 후 i + 1
i += a; // i = i + a 연산 후 값 저장, i == 2
```

### while
```java
int r = 0; // 정수형 r 변수 0 으로 초기화
while (r <= 20 (종료 조건)){
	System.out.println(r);
	r ++ ; 증감연산 // 변수 r을 종료 조건을 만족시키기 위한 제어
}
```
* Java는 절차지향언어로 문단 순서에 따라 진행하므로 증감 연산의 문단 순서가 달라지면 출력문이 달라진다.
* while문 조건식은 false가 될 때까지 증감식을 수행하므로 증감연산 이후 출력하면 종료조건 + 1

### for
```java
for ( 초기값; 단일조건; 증감연산 ){ 출력문 }
```
* if, else if ,else , while, for 출력문에 문법 중첩 가능


