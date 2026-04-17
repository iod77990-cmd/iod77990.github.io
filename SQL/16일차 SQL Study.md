## 오후 12:42 2026-04-16

> - DB
> - SQL(mysql) 


### DB 
** DB (DataBase)**
- 공유되어 사용될 목적으로 저장, 관리되는 데이터
- 검색, 수정, 삭제, 생성 등 효율적으로 하기 위한 구조화된 데이터
- 테이블 : 사물이나 개념의 본질적인 속성을 모아 표 형식으로 만든 것

**테이블**
- 사물이나 개념의 본질적인 속성을 모아서 표로 만든 것(단위)

**DBMS(DB Management System)**
- DB를 체계적으로 관리할 수 있도록 기능을 제공하는 푸로그램
ex) oracle, mysql, mssql, redis, ...

**SQL(Structured Query Language)**
- DBMS를 다루기 위한 표준화된 언어

### SQL (SQLyog)

- "#" 주석
- `고유명사` 
- SHOW DATABASES; # 데이터 베이스 목록화
- CREATE DATABASE `site1`; # 데이터 베이스 a1 생성
- DROP DATABASE `a1`; # 데이터 베이스 a1 삭제
- 테이블 만들기
```sql
CREATE TABLE article(
    title CHAR(100),
    `body` CHAR(100)
);
```
- 데이터 베이스 사용 지정
USE 데이터베이스 이름;

- 지정된 데이터 베이스의 테이블 목록화 출력
SHOW TABLES ;

- 데이터 삽입 insert는 set을 사용하기도 하고 (mysql, mariaDB) values가 표준
INSERT INTO article 
SET title = '제목1',
`body` = '내용1';

# 데이터 확인
SELECT * FROM article;

- `db` 테이블의 구조 확인
```sql
DESC mysql.db;
```
- 기존에 `board` 데이터베이스가 존재 한다면 삭제
```sql
DROP DATABASE IF EXISTS board;
```

# 제목은 '제목1', 내용은 '내용1'인 데이터 하나 추가 
INSERT INTO article
SET title = '제목1',
`body` = '내용1'; 
# 제목 조회
SELECT title FROM article;
# 내용 조회
SELECT `body` FROM article;
# 제목, 내용 칼럼 데이터 조회
SELECT title, `body` FROM article;
# 내용, 제목 칼럼 데이터 조회
SELECT `body`, title FROM article;

# 제목 데이터 aaa로 수정(모두 수정됨..)
UPDATE article 
SET title = 'aaa';
# `body`가 내용2인 것만 조회
SELECT `body` FROM article WHERE `body` LIKE '내용2';
# 내용2만 새로운내용2 로 수정
UPDATE article 
SET `body` = '새로운 내용2' WHERE `body` LIKE '내용2';

# 데이터 삭제 (모든 데이터가 삭제...)
DROP TABLE article;
