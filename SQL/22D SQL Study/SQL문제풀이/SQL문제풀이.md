오후 12:27 2026-04-24

> - SQL 문제풀이

---

```sql
/*
1. 테이블 생성 (CREATE)
다음 조건에 맞는 Books 테이블과 Authors 테이블을 생성하세요.
Authors 테이블
author_id: 정수형, 기본 키(Primary Key), 자동 증가
name: 문자열(50자), 필수 입력(Not Null)
country: 문자열(50자)
Books 테이블
book_id: 정수형, 기본 키, 자동 증가
title: 문자열(100자), 필수 입력
author_id: 정수형, 외래 키(Foreign Key) - Authors 테이블의 author_id 참조
published_date: 날짜형
price: 실수형, 기본값 0
*/
CREATE TABLE Author (
    author_id INT PRIMARY KEY AUTO_INCREMENT,
    `name` TEXT(50) NOT NULL,
    country TEXT(50)
);
CREATE TABLE Books (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    a_id INT,
    published_date DATE ,
    price DOUBLE DEFAULT 0,
    
    CONSTRAINT fk_author FOREIGN KEY (a_id)
    REFERENCES Author(author_id)
);
/*
2. 테이블 수정 (ALTER)
생성한 테이블에 다음 변경 사항을 반영하세요.
Books 테이블에 stock_count (재고 수, 정수형) 컬럼을 추가하세요.
Books 테이블의 title 컬럼 크기를 150자로 확장하세요.
Authors 테이블에서 country 컬럼을 삭제하세요.
*/

ALTER TABLE Books ADD sock_count INT NOT NULL;
ALTER TABLE Books MODIFY title VARCHAR(150) NOT NULL;
ALTER TABLE Author DROP country;

/*
3. 제약 조건 추가 (CONSTRAINT)
Books 테이블의 price 컬럼에 '0보다 커야 한다'는 체크(CHECK) 제약 조건을 추가하세요.
*/

ALTER TABLE Books ADD CONSTRAINT price CHECK( price > 0 );

/*
4. 삭제 및 초기화 (DROP & TRUNCATE)
Books 테이블의 모든 데이터를 삭제하되 테이블 구조는 남겨두는 쿼리를 작성하세요.

최종적으로 Books 테이블과 Authors 테이블을 완전히 삭제하는 쿼리를 작성하세요.
*/

DELETE FROM Books; # Books 테이블의 데이터 삭제

SET FOREIGN_KEY_CHECKS = 0;
TRUNCATE TABLE Books;
TRUNCATE TABLE Author; # error 150 해결
# 오답 : TRUNCATE TABLE Author CASCADE CONSTRAINTS; 
SET FOREIGN_KEY_CHECKS = 1;
DROP TABLE Books;
DROP TABLE Author;

```

- error 150 
외래 키 제약 조건을 생성하거나 수정할 때, 
부모 테이블과 자식 테이블 간의 데이터 타입 불일치, 
인덱스 누락 또는 엔진 불일치로 발생

-> 	SET FOREIGN_KEY_CHECKS = 0; # 체크 해제
	자식 테이블 삭제
	부모 테이블 삭제
	SET FOREIGN_KEY_CHECKS = 1; # 다시 설정

- 외래키 설정

부모)
CREATE TABLE Authors (
    author_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL
);

자식)
모든 칼럼 다 적고 맨 마지막에 제약 조건 따로 선언

```sql
CREATE TABLE Books (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    a_id INT,
    
    CONSTRAINT fk_a_id 
    FOREIGN KEY (a_id) REFERENCES Author(author_id)
);
```
또는

칼럼 이름과 타입 바로 뒤에 제약 조건을 붙이는 방식

CREATE TABLE Books (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    # 컬럼 정의와 동시에 외래 키를 지정 (인라인)
    author_id INT REFERENCES Author(author_id), 
    price DOUBLE DEFAULT 0
);
