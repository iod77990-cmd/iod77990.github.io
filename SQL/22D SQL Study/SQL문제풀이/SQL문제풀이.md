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

```sql
CREATE TABLE Authors (
    author_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL
);
```

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
```sql
CREATE TABLE Books (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    # 컬럼 정의와 동시에 외래 키를 지정 (인라인)
    author_id INT REFERENCES Author(author_id), 
    price DOUBLE DEFAULT 0
);
```

```sql

CREATE DATABASE c1;
USE c1;

# 1)
CREATE TABLE `user` (
    `name` VARCHAR(50) NOT NULL,
    u_id VARCHAR(50) PRIMARY KEY NOT NULL,
    `password` VARCHAR(50) NOT NULL,
    nickname VARCHAR(50) NOT NULL UNIQUE,
    jDate TEXT
);

DROP TABLE `user`;

CREATE TABLE board(
    id INT,
    b_id INT NOT NULL,
    opifromuser VARCHAR(50),
    likefromuser VARCHAR(50),
    noti TEXT ,
    free TEXT ,
    qna TEXT ,
    opi VARCHAR(50) ,
    regDate TEXT
);

CREATE TABLE article (
    id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    b_id INT NOT NULL,
    a_id VARCHAR(50) NOT NULL,
    title VARCHAR(50),
    `body` TEXT,
    hit INT NOT NULL,
    regDate TEXT,
    `like` INT
);

# 2)
# 회원가입 4명
INSERT INTO `user` VALUES('홍길동', 'user1', '1234', '신출귀몰', '2023-01-01 00:00:00');
INSERT INTO `user` VALUES('이순신', 'user2', '4321', '구국의영웅', '2023-01-01 00:00:00');
INSERT INTO `user` VALUES('임꺽정', 'user3', '1423', '힘쎈장사', '2023-01-01 00:00:00');
INSERT INTO `user` VALUES('유관순', 'user4', '3131', '독립열사', '2023-01-01 00:00:00');

# 게시물 등록
# 홍길동이 자유게시판 3개
INSERT INTO article VALUES(1, 2, 'user1', '제목1', '내용1', 10, '2023년3월3일 12시30분',0);
INSERT INTO article VALUES(2, 2, 'user1', '제목2', '내용2', 23, '2024년4월5일 15시12분',0);
INSERT INTO article VALUES(3, 2, 'user1', '제목3', '내용3', 31, '2025년1월2일 19시08분',0);

#이순신이 자유게시판 2개
INSERT INTO article VALUES(4, 2, 'user2', '제목4', '내용4', 100, '2024년4월1일 08시30분',0);
INSERT INTO article VALUES(5, 2, 'user2', '제목5', '내용5', 13, '2024년5월7일 16시22분',0);

# 이순신이 공지게시판에 2개
INSERT INTO article VALUES(6, 1, 'user2', '제목6', '내용6', 112, '2023년3월3일 12시30분',0);
INSERT INTO article VALUES(7, 1, 'user2', '제목7', '내용7', 224, '2024년6월1일 17시12분',0);

# 임꺽정이 질문과 답 2개
INSERT INTO article VALUES(8, 3, 'user3', '제목8', '내용8', 87, '2023년7월1일 22시30분',0);
INSERT INTO article VALUES(9, 3, 'user3', '제목9', '내용9', 56, '2025년3월3일 23시12분',0);

# 이순신이 질문과 답 1개
INSERT INTO article VALUES(10, 3, 'user2', '제목10', '내용10', 3, '2025년4월1일 20시00분',0);

# 유관순이 질문과 답 1개
INSERT INTO article VALUES(11, 3, 'user4', '제목11', '내용11', 12, '2025년3월11일 20시00분',0);

#유관순이 자유게시판에 1개 
INSERT INTO article VALUES(12, 2, 'user4', '제목12', '내용12', 32, '2025년2월13일 20시00분',0);

# 임꺽정이 자유게시판 첫번째 게시물에 댓글 2개
INSERT INTO board SET b_id = 2, id = 1, opifromuser = 'user3', free =' 제목1' , opi = '댓글내용1', regDate = '2024년4월5일 15시12분';
INSERT INTO board SET b_id = 2, id = 1, opifromuser = 'user3', free =' 제목1' , opi = '댓글내용2', regDate = '2024년5월2일 19시08분';

# 임꺽정이 질문과 답 첫번째 두번째에 각각 댓글 2개씩 작성
INSERT INTO board SET b_id = 3, id = 8, opifromuser = 'user3', qna = '제목8', opi = '댓글내용9', regDate = '2023년7월5일 13시32분';
INSERT INTO board SET b_id = 3, id = 8, opifromuser = 'user3', qna = '제목8', opi = '댓글내용10', regDate = '2023년7월7일 11시15분';
INSERT INTO board SET b_id = 3, id = 9, opifromuser = 'user3', qna = '제목9', opi = '댓글내용11', regDate = '2025년6월5일 15시22분';
INSERT INTO board SET b_id = 3, id = 9, opifromuser = 'user3', qna = '제목9', opi = '댓글내용12', regDate = '2025년7월3일 17시14분';

# 이순신이 질문과 답 두번째 글에 댓글 3개 작성
INSERT INTO board SET b_id = 3, id = 9, opifromuser = 'user2', qna = '제목9', opi = '댓글내용13', regDate = '2025년3월5일 17시02분';
INSERT INTO board SET b_id = 3, id = 9, opifromuser = 'user2', qna = '제목9', opi = '댓글내용14', regDate = '2025년3월7일 12시32분';
INSERT INTO board SET b_id = 3, id = 9, opifromuser = 'user2', qna = '제목9', opi = '댓글내용15', regDate = '2025년3월7일 16시15분';

# 홍길동이 공지사항 첫번째, 두번째 게시물에 각각 댓글 3개씩 작성
INSERT INTO board SET b_id = 1, id = 6, opifromuser = 'user2', noti = '제목6', opi = '댓글내용3', regDate = '2023년3월3일 12시30분';
INSERT INTO board SET b_id = 1, id = 6, opifromuser = 'user2', noti = '제목6', opi = '댓글내용4', regDate = '2023년3월5일 15시12분';
INSERT INTO board SET b_id = 1, id = 6, opifromuser = 'user2', noti = '제목6', opi = '댓글내용5', regDate = '2023년3월12일 19시08분';

INSERT INTO board SET b_id = 1, id = 7, opifromuser = 'user2', noti = '제목7', opi = '댓글내용6', regDate = '2024년6월3일 12시30분';
INSERT INTO board SET b_id = 1, id = 7, opifromuser = 'user2', noti = '제목7', opi = '댓글내용7', regDate = '2024년6월5일 15시12분';
INSERT INTO board SET b_id = 1, id = 7, opifromuser = 'user2', noti = '제목7', opi = '댓글내용8', regDate = '2025년4월1일 19시08분';

# 좋아요

UPDATE article SET `like` = 4 WHERE title = '제목1';
UPDATE article SET `like` = 1 WHERE title = '제목4';
UPDATE article SET `like` = 2 WHERE title = '제목7';
UPDATE article SET `like` = 4 WHERE title = '제목10';
UPDATE article SET `like` = 1 WHERE title = '제목3';

SELECT * FROM `user`;
SELECT * FROM board;
SELECT * FROM article;
```