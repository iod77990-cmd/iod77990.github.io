오전 11:49 2026-04-20

> SQL

#### SQL 문제풀이
- 해당 Column의 값이 NULL을 반환할 경우 다른 값으로 출력하고 싶다면 INFULL함수를 사용하면 된다.
```sql
SELECT IFNULL(Column명, "Null일 경우 대체 값") FROM 테이블명;
```
- where절에서 and는 교집합을 찾음

- '%' : ~으로 시작하는 % 문자열 사이 공백포함

- 특정 소수점을 반올림을 하고 소수점 이하는 버리고 반환하는 함수 round(값, 자리수)

- 해당 칼럼의 행의 개수를 반환하는 count(칼럼명)함수

- 찾아 바꾸는 함수 replace(칼럼명, 기존문자, 바꿀문자)

- 중복제거 조회 distinct 키워드

```sql
### Products 테이블에서 가격(Price)으로 오름차순, 제품번호(ProductId)로 내림차순 정렬하기
SELECT Price, ProductId FROM Products ORDER BY Price ASC, ProductId DESC;

### Customers 테이블에서 CustomerId값이 10 이상이고 CustomerId값이 20 이하인 행만 조회
SELECT CustomerId FROM Customers WHERE CustomerId BETWEEN 10 AND 20; 

### Customers 테이블에서 CustomerId값이 20 이하인것 + CustomerId값이 80이상인 행을 모두 조회
SELECT * FROM Customers WHERE CustomerId <= 20 OR CustomerId >= 80; 

### Customers 테이블에서 CustomerId갑이 20 이하인 것 + CustomerId값이 80이상인 모든 컬럼 중에서 city가 'London'인 행을 조회
SELECT * FROM Customers WHERE (CustomerId <= 20 OR CustomerId >= 80) AND City LIKE 'London'; 

### Customers 테이블에서 CustomerId값이 10과 20 사이인 행을 조회
SELECT * FROM Customers WHERE CustomerId BETWEEN 10 AND 20; 

### Customers 테이블에서 city 값에 'London', 'Berlin', 'Madrid' 중 하나라도 포함하는 행을 모두 조회
SELECT * FROM Customers WHERE City IN ('London', 'Berlin', 'Madrid');

### Employees 테이블에서 LastName이 D로 시작하는 행만 조회
SELECT LastName FROM Employees WHERE LastName LIKE 'D%';

### Employees 테이블에서 LastName이 D로 시작하지 않는 행만 조회
SELECT LastName FROM Employees WHERE NOT(LastName LIKE 'D%'); 

### Products 테이블의 Price 컬럼값들을 반올림한다.
SELECT ROUND(Price) FROM Products; 

### Categories 테이블에서 CategoryName 컬럼의 모든 행의 개수를 구하기.
SELECT COUNT(CategoryName) FROM Caregories; 

### Customers 테이블의 city 컬럼의 값에서 B문자를 찾아 b로 바꾸기
SELECT REPLACE(City, 'B', 'b') FROM Customers; 

### Suppliers에서 Country를 중복제거해서 조회하기
SELECT DISTINCT Country FROM Suppliers; 
```
[문제 링크](https://codepen.io/gykim93/pen/rNbYBQp?editors=1000)

[테스트 주소 링크](https://www.w3schools.com/mysql/trymysql.asp?filename=trysql_select_all)




