
> - System.in, Scanner 객체생성
> - nextLine( )
> - nextInt( )
> - Integer.parseInt( )
> - Integer.toString( )
> - trim ( ) 
> - split ( ) 
> - Math.random( ) 
> - close( )
> - 운영체제(os)
> - Java's 원시타입과 참조타입
> - 변수의 적용 범위
 
### Scanner 객체 생성 ⌨
- 키보드로 사용자의 임의의 값 입력받기 위해 생성
```java
Scanner 객체명 = new Scanner(System.in);
Scanner sc = new Scanner(System.in); // 문자열 형으로 입력받기

```

### nextLine ( )
- 한 줄 줄 바꿈 전까지 입력 받음
``` java
String str11 = sc.nextLine(); // 한 줄 입력 받기
```

### nextInt ( )
- 공백, 줄바꿈 전까지 입력받음
```java
String str10 = sc.nextInt(); // 공백, 줄바꿈 전까지 입력받기
```

### Integer.parseInt ( )
- 문자열 String형을 정수형 Int형으로 변환
```java
int r = Integer.parseInt(str10);
```

### Integer.toString ( )
- 정수형 Int형을 문자열 String 형으로 변환
```java
String v = Integer.toString(r);
```
### trim ( )
- 문자열의 양 끝 공백 제거
```java
String str99 = " I 9 ";
String str98 = str99.trim(); // "I 9"
```

### split ( )
- ( ) 의 기준으로 나눠 저장
```java
Scanner sc = new Scanner(System.in);
String str98 = sc.nextLine();
String[] str97 = str98.split("");
for (int i = 0; i < str97.length; i++) {
     System.out.print(str97[i]);
 }// hello? 로 입력했다면 hello? 출력
```

### Math.random ( )
- 실수형 0.0 ~ 1.0 미만 생성
```java
int a = (int)(Math.random ( ) * 100 + 1);//1.0 ~ 100.99 사이 실수형 랜덤 값 생성 후 int형으로 형변환 후 a변수에 저장
```

### close ( ) 🧊
- 객체가 사용하는 메모리 반납
```java
sc.close();
```
### OS (운영체제)
~~사용자가 컴퓨터의 자원을 활용하고 사용하기 위한 편의 소프트웨어~~
- 윈도우 ( Windows )
- 리눅스 ( Linux )
- 유닉스 ( Unix )
...

- CLI 명령어 기반 인터페이스
- GUI 그래픽 기반 인터페이스

### Java's 기본타입과 참조타입
- **기본 ( 원시 ) 타입**
  - byte	
    - 1 byte
  - short	
    - 2 byte
  - int	(Integer)	
    - 4 byte
  - long 	
    - 8 byte
  - float 	
    - 4 byte
  - double 	
    - 8 byte
  - boolean 
    - 2 byte
  - char (Character)	
    - 2 byte

- **참조타입**
  - 클래스 ( class )
  - 인터페이스 ( Interface )
  - 배열 ( Array )
  - 열거형 ( Enum )

### 변수의 적용 범위
- 전역변수
모든 지역에서 사용 가능한 변수
📌자바에서는 Main클래스 안에서 코딩을 하므로 전역변수 없음
클래스변수(static)로 대체


- 맴버변수
클래스 안, 함수 밖에서 선언된 변수
초기화하지 않으면 기본값이 들어감

- 지역변수
함수 안에서 선언된 변수
초기화를 하지 않으면 사용할 수 없음