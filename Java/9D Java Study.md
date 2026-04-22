>- S. O. L. I. D 원칙
>- getter 와 setter
>- ArrayList와 Array
>- HashSet 이란?
>- HashMap 이란?
>- 제너릭

### SOLID 원칙 ( Principle )
- SRP( Single Responsibility )
  - 각 클래스 ( 객체 ) 는 단 하나의 기능만 담당
- OCP( Open-Closed )
  - 확장은 개방하고 수정은 폐쇠
- LSP( Liskov Substitution )
  - 서브 ( 자식 ) 타입은 언제나 기반 ( 부모 ) 타입으로 교체 가능해야 함
- ISP( Interface Segregation )
  - 사용에 맞는 인터페이스 잘게 분리
- DIP( Dependency Inversion )
  - 대상의 상위 요소 ( 추상 클래스 또는 인터페이스 ) 로 참조해야 함

### Getter 와 Setter
**프로그램 실행 중**
- setter: private 접근 제한자의 필드의 값을 외부에서 변경 가능한 함수
- getter: private 접근 제한자의 필드의 값을 읽을 수 있게 하는 함수


### ArrayList 와 Array
- Array는 배열로 객체생성시 고정된 길이를 할당(정적라벨링)
- ArrayList는 객체생성시 배열리스트로 정해지지않는  ( 동적인 ) 길이를 갖는다, 값을 삭제, 추가를 하면 다음 값이 밀리거나 앞으로 넘어온다.( 자동라벨링 )
```java
int [] num = new int[]; // Array 배열객체 생성

for(int num : num){ // for each
	
	System.out.println(num);
    
} // 배열에 저장한 값 num배열의 길이만큼 반복해서 출력

ArrayList<Integer> numList = new ArrayList<>(); // 배열리스트 객체 생성

numList.add(10); // ArrayList에 값을 추가하려면 numList객체에 접근해서 add()로 값을 넣는다.
numList.add(20);
numList.remove(10); // ArrayList에 값을 제거하려면 numList객체에 접근해서 remove()로 값을 제거한다.

for (int i = 0; i < nameList.size(); i++) { // 길이가 아닌 사이즈 크기를 가짐
      System.out.println(nameList.get(i)); // 값을 받아올 때는 객체이름으로 접근해서 get()로  가져옴
```

### HashSet
- 순서, 중복을 허용하지 않는 데이터 집합
```java
HashSet<Integer> Hash = new HashSet<>(); // HashSet int형 Hash이름의 새로운! 객체 생성

```

### HashMap
- 키와 값을 쌍으로 저장하는 map
- index번호로 그대로 저장을 한다, 값을 삭제하거나 추가를 해도 빈공간으로 남는다 ( 수동라벨링 )
```java
HashMap<Integer, String> map = new HashMap<>(); // int형(키값), String형(데이터값) 쌍으로 hash map으로 map이름으로 객체 생성

```

### 제너릭



