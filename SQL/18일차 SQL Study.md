오전 9:21 2026-04-20

> - SQL 주요 키워드 문법
> - NULL 처리 방법
> - 열 위치 변경 조건 키워드
> - SQL 함수
> - SQL의 DML문 실행 순서


### SQL 주요 키워드 문법

> DDL(Data Define Language)
테이블과 같은 데이터 구조를 정의하는데 사용되는 명령어들로(CRUD + 이름변경) 데이터 구조와 관련된 명령어

**CREATE**(테이블 생성) : DB 또는 테이블 같은 오브젝트 생성
```sql
CREATE TABLE 테이블 명(
	ID 자료형 제약조건,
	NAME 자료형 (크기),
	EMAIL 자료형 (크기)
);
```

**ALTER**(테이블 수정) : 기존에 만든 오브젝트의 구조 변경
```SQL
ALTER TABLE 테이블명 ADD(MODIFY, DROP) (COLUMN) 컬럼명 데이터타입(자료형)(크기)(제약조건);
```

**DROP**(테이블 삭제) : 오브젝트 완전히 삭제(구조 + 데이터)
```SQL
DROP TABLE 테이블명;
DROP DATABASE 이름;
```

**RENAME**(테이블 이름변경) : 
```SQL
RENAME TABLE 기존이름 TO 새로운 이름;
ALTER TABLE 기존이름 RENAME TO 새로운 이름;
```

**TRUNCATE**(초기화) : 모든 데이터를 삭제하고 구조는 남김(테이블 공간 자체를 초기화, ROLLBACK불가, 속도는 빠름, 번호 초기화)
😰WHERE 절 사용 불가
```SQL
TRUNCATE TABLE 이름;
```

---

> DCL(Data Controll Language)
데이터베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 명령어

**GRANT**(권한 부여) :  
```SQL
GRANT 권한_종류 ON 대상_오브젝트 TO 사용자_계정 [WITH GRANT OPTION];
```

**REVOKE**(권한 부여 철회) : 
```SQL
REVOKE 권한_종류 ON 대상_오브젝트 FROM 사용자_계정;
```

**COMMIT(트렌잭션의 작업을 저장)** : 

**ROLLBACK(트랜잭션의 작업을 취소 후 원래대로 복구)**

---

> DML(Data Management Language)
데이터베이스에 들어 있는 데이터를 조회하거나 검색하기 위한 명령어 + 데이터 베이스의 테이블에 들어 있는 데이터에 변형을 가하는 종류의 명령어

**SELECT**(데이터 선택) : 데이터베이스에 들어 있는 데이터를 조회하거나 검색하기 위한 명령어
```SQL
SELECT 컬럼1, 컬럼2 FROM 테이블명 WHERE 조건;
```

**INSERT**(데이터 삽입) : 
```SQL
INSERT INTO 테이블명 (컬럼1, 컬럼2, ...) VALUES (값1, 값2, ...);
```

**UPDATE**(데이터 수정) : 
```SQL
UPDATE 테이블명 SET 컬럼1 = 값1, 컬럼2 = 값2 WHERE 조건;
```

**DELETE**(데이터 삭제) : 
```SQL
DELETE FROM 테이블명 WHERE 조건;
```

### NULL 처리 방법
SQL은 테이블 생성할 때 지정하고 IS NULL, NOT NULL
```sql
create table a1(
	id int not null
);
```

### 열 위치 변경 조건 키워드
first(맨앞으로), after(지정한 열 다음 순서로), limit(열 개수 제한) ...


### SQL 함수
데이터베이스에서 데이터를 조회, 조작, 분석하기 위해 미리 정의된 명령문 세트
> 내장함수(문자열, 숫자, 날짜, 형변환, 집계) + 그룹함수(단일행, 다중행) + 사용자 정의 함수 세트

- 문자열 함수
upper(str)/lower(str) : 대소문자 변환
length(str)/ len(str) : 문자열 길이 반환
substr(str, start, len)/ substring : 문자열 일부 추출 
concat(str1, str2) : 문자열 연결
trim(str) : 공백 제거

- 숫자함수
round(num, dec) : 소수점 반올림
trunc(num, dec) / truncate : 특정 자리에서 버림
abs(num) : 절댓값
mod(num1, num2) : 나머지 계산

- 날짜 및 시간 함수
now() / sysdate() / getdate() : 현재 날짜 및 시간 변환
date_add(date, interval) : 날짜 더하기
datediff(date1, date2) : 날짜 간격 계산

-  형 변환 함수
cast(value as type) : 특정 데이터 형식으로 변환
to_char(date, format) / to_date : 날짜/문자열 형식 변환

- 집계함수
sum(col) : 합계
avg(col) : 평균
count(col) : 행 수
max(col) / min(col) : 최대/최솟값

- null처리 및 조건 함수
ifnull() / nvl() : null 값을 다른 값으로 대체
case when...then...else...end : sql에서 if-else논리

- 사용자 정의 함수
...

### SQL의 DML문 실행 순서

**from -> where -> group by -> having -> select -> order by**

설명) 
1. 테이블 선택
2. 테이블의 행에서 조건을 만족하는 행만 선택
3. 선택된 행을 그룹핑
4. 그룹핑된 행에 그룹함수를 사용해서 행을 제한
5. 그룹핑된 행에 그룹함수를 적용
6. 정렬

