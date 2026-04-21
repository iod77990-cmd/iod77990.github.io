오후 12:11 2026-04-21

DROP DATABASE mall;

CREATE DATABASE mall;

USE mall;

CREATE TABLE t_order(
id INT(5) PRIMARY KEY AUTO_INCREMENT,
userNo INT(5) NOT NULL,
productNo INT(5) NOT NULL
);

CREATE TABLE t_user(
id INT(5) PRIMARY KEY AUTO_INCREMENT,
userId CHAR(200) NOT NULL,
userPw CHAR(200) NOT NULL,
userName CHAR(50) NOT NULL,
addr CHAR(200) NOT NULL
);

CREATE TABLE t_product(
id INT(5) PRIMARY KEY AUTO_INCREMENT,
pname CHAR(100) NOT NULL,
price INT(10) NOT NULL
);

---

INSERT INTO t_product
SET pname = '운동화',
price = 1000000;

INSERT INTO t_product
SET pname = '코트',
price = 100000;

INSERT INTO t_product
SET pname = '반바지',
price = 30000;

INSERT INTO t_product
SET pname = '스커트',
price = 15000;

INSERT INTO t_product
SET pname = '코트',
price = 100000;

INSERT INTO t_product
SET pname = '티셔츠',
price = 9000;

INSERT INTO t_product
SET pname = '운동화',
price = 200000;

INSERT INTO t_product
SET pname = '모자',
price = 30000;


INSERT INTO t_user
SET userId = 'user1',
userPw = 'pass1',
userName = '손흥민',
addr = '런던';

INSERT INTO t_user
SET userId = 'user2',
userPw = 'pass2',
userName = '설현',
addr = '서울';

INSERT INTO t_user
SET userId = 'user3',
userPw = 'pass3',
userName = '원빈',
addr = '대전';

INSERT INTO t_user
SET userId = 'user4',
userPw = 'pass4',
userName = '송혜교',
addr = '대구';

INSERT INTO t_user
SET userId = 'user5',
userPw = 'pass5',
userName = '소지섭',
addr = '부산';

INSERT INTO t_user
SET userId = 'user6',
userPw = 'pass6',
userName = '김지원',
addr = '울산';


INSERT INTO t_order
SET userNo = 1,
productNo = 1;

INSERT INTO t_order
SET userNo = 2,
productNo = 2;

INSERT INTO t_order
SET userNo = 3,
productNo = 3;

INSERT INTO t_order
SET userNo = 4,
productNo = 4;

INSERT INTO t_order
SET userNo = 5,
productNo = 5;

INSERT INTO t_order
SET userNo = 6,
productNo = 6;

INSERT INTO t_order
SET userNo = 6,
productNo = 7;

INSERT INTO t_order
SET userNo = 1,
productNo = 5;

INSERT INTO t_order
SET userNo = 4,
productNo = 4;

INSERT INTO t_order
SET userNo = 1,
productNo = 1;

INSERT INTO t_order
SET userNo = 5,
productNo = 8;

SELECT * FROM t_order;
SELECT * FROM t_product;
SELECT * FROM t_user;

---

# 1. 손흥민의 주문 개수는? ???
SELECT COUNT(*) FROM t_order LEFT JOIN t_user ON t_user.id = t_order.userNo WHERE t_user.userName = '손흥민';


# 2. 손흥민이 산 상품은? ???
SELECT t_product.pname FROM t_product LEFT JOIN t_user ON t_user.id = t_product.id WHERE t_user.userName = '손흥민';


# 3. 스커트를 산 사람은? ???
SELECT t_user.userName FROM t_user JOIN t_product ON t_user.id = t_product.id WHERE t_product.pname = '스커트';


# 4. 가장 많이 주문한 사람의 아이디와 이름, 주문개수는? ???
SELECT t_user.id, t_user.userName, COUNT(t_user.userName) FROM t_order LEFT JOIN t_user ON t_order.userNo = t_user.id GROUP BY t_user.userName ORDER BY COUNT(*) DESC LIMIT 1;


# 5. 소지섭이 사용한 총 금액은? ???
SELECT SUM(t_product.price) FROM t_product JOIN t_order ON t_product.id = t_order.userNo WHERE t_order.userNo = 5;


