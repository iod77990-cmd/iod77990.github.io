> - 기본 구조
> - 출력 문법(서식문자)
> - 데이터 타입(문자형, 숫자형)
> - 변수
> - 연산자 개념 & 우선순위

### 기본 구조
```java
public class Main { // class 명
	public static void main(String[] args){ // main 메서드 시작
    
    
    System.out.println("Hello world"); // 출력문 //sout(tap) 단축
    
    
    }
}
```
```java
int a = 3;
System.out.println("hello"); //출력 후 개행
System.out.print("hello"); // 한줄에 모두 출력 개행 안함
System.out.printf("hello %d번 \n", a); //서식문자처리 할 수 있는 printf, %d(정수 서식문자, a의 값이 들어감 1:1매치), \n(개행 서식문자), souf (tap) 단축

```

### 데이터 타입
 - 기본 타입
   * 문자, 문자열 (char, String)
   * 정수, 실수 (byte, int, float, double)
   * boolean (true 또는 false)
 - 참조타입
 

```java
System.out.println("안녕"); //문자열
System.out.println(123); // 정수
```
** 서로 다른 타입 연산 **
```java
System.out.println("안" + "녕"); // 안녕
System.out.println("20" + "26"); // 2026

System.out.println("안녕" + 20 + 26); // 안녕2026, 문자열 출력 후 뒤에 있는 연산은 문자열 취급해서 출력
System.out.println(20 + 26 + "안녕"); // 46안녕, 정수형 연산 후 문자열 연산해서 출력

System.out.println("안녕" + (20 + 26)); // 안녕46
System.out.println("안녕" + 10 * 2); // 안녕20, *는 먼저 계산을 하므로 정수 계산 후 문자열 연산
```
### 변수
* 특
	1. 선언, 정의 후 사용가능
	2. 변수명 앞에 타입 명시 (자료형 변수이름; 또는 자료형 변수이름 = ?;)
    3. 타입에 맞는 값만 할당 (자료형에 맞는 값)
    4. 변수명은 숫자, 특수문자(언더바 제외)로 시작할 수 없음
    5. 단일 문법명, 단일 자료형을 변수명으로 사용 못함
    6. 한글, 영문, 대소문자구분 가능
    
### 연산자 & 우선순위
* 연산자
```java
a / a 같은 타입이면 몫만 출력, 다른 쪽이 실수면 실수 출력
a % a 나머지 출력
비교연산 => 결과는 true 아니면 false
== : 같다
!= : 다르다
> : 크다(초과)
< : 작다(미만)
>= : 크거나 같다(이상)
<= : 작거나 같다(이하)
&& (AND, 그리고) 하나라도 틀리면 바로 false
|| (OR, 또는)둘 중 하나만 맞으면 true
! 반전
```
* 우선순위
![](https://velog.velcdn.com/images/ios77990/post/57231a99-136d-4764-83c3-b3bbd92fea99/image.png)
- - -
