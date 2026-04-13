### 12Day Java

>- 객체 간 관계
>- substring()

### 객체 간 관계
- 사용(Use-a / Dependency)
한 객체의 함수가 다른 객체를 인자로 받거나 생성하여 기능을 사용하는 경우
- 포함(Has-a / Association, Composition)
한 객체가 다른 객체를 소유하거나 포함하는 관계
- 집합(Aggregation)
객체들이 약하게 연결되어, 한 객체가 사라져도 다른 객체는 독힙적으로 존재할 수 있는 경우
- 합성(Composition)
객체 간 생애주기가 같아 전체 객체가 사라지면 부분 객체도 함께 사라지는 강한 관계
- 상속(Is-a / Inheritance)
부모 클래스의 기능을 자식 클래스가 재사용하거나 확장하는 관계
객체간의 공통점을 추상화하여 구현하는 경우

**특징 요약**
- 동적인 성격 : 생성과 소멸에 따라 동적으로 관계 변화
- 상호작용 : 두 객체는 직접적인 수정보다 메시지 교환을 통해 서로 통신
- 독립성 : 집합인 경우 객체 재사용이 용이

### substring ( )
- java.lang.String 클래스의 함수, 문자열의 특정 부분을 잘라내고 그 이후 부분을 추출하는 역할
```java

String substring(int index) // index부터 끝까지 문자열 반환

String substring(int Index, int endIndex) // index포함 endIndex-1까지 문자열을 반환

```

