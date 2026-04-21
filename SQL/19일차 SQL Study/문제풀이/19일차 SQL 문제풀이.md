오후 12:11 2026-04-21

#### 전제 DB 자료 및 정보

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

끝
---

문제)

#### 1. 손흥민의 주문 개수는? ???
SELECT COUNT(*) FROM t_order LEFT JOIN t_user ON t_user.id = t_order.userNo WHERE t_user.userName = '손흥민';


#### 2. 손흥민이 산 상품은? ???
SELECT t_product.pname FROM t_product LEFT JOIN t_user ON t_user.id = t_product.id WHERE t_user.userName = '손흥민';


#### 3. 스커트를 산 사람은? ???
SELECT t_user.userName FROM t_user JOIN t_product ON t_user.id = t_product.id WHERE t_product.pname = '스커트';


#### 4. 가장 많이 주문한 사람의 아이디와 이름, 주문개수는? ???
SELECT t_user.id, t_user.userName, COUNT(t_user.userName) FROM t_order LEFT JOIN t_user ON t_order.userNo = t_user.id GROUP BY t_user.userName ORDER BY COUNT(*) DESC LIMIT 1;


#### 5. 소지섭이 사용한 총 금액은? ???
SELECT SUM(t_product.price) FROM t_product JOIN t_order ON t_product.id = t_order.userNo WHERE t_order.userNo = 5;

---

전재 DB 자료 및 정보 조건

DROP DATABASE IF EXISTS scott;

CREATE DATABASE scott;

USE scott;

CREATE TABLE DEPT (
    DEPTNO DECIMAL(2),
    DNAME VARCHAR(14),
    LOC VARCHAR(13),
    CONSTRAINT PK_DEPT PRIMARY KEY (DEPTNO) 
);

CREATE TABLE EMP (
    EMPNO DECIMAL(4),
    ENAME VARCHAR(10),
    JOB VARCHAR(9),
    MGR DECIMAL(4),
    HIREDATE DATE,
    SAL DECIMAL(7,2),
    COMM DECIMAL(7,2),
    DEPTNO DECIMAL(2),
    CONSTRAINT PK_EMP PRIMARY KEY (EMPNO),
    CONSTRAINT FK_DEPTNO FOREIGN KEY (DEPTNO) REFERENCES DEPT(DEPTNO)
);

CREATE TABLE SALGRADE ( 
    GRADE TINYINT,
    LOSAL SMALLINT,
    HISAL SMALLINT 
);

INSERT INTO DEPT VALUES (10,'ACCOUNTING','NEW YORK');

INSERT INTO DEPT VALUES (20,'RESEARCH','DALLAS');

INSERT INTO DEPT VALUES (30,'SALES','CHICAGO');

INSERT INTO DEPT VALUES (40,'OPERATIONS','BOSTON');

INSERT INTO EMP VALUES (7369,'SMITH','CLERK',7902,STR_TO_DATE('17-12-1980','%d-%m-%Y'),800,NULL,20);

INSERT INTO EMP VALUES (7499,'ALLEN','SALESMAN',7698,STR_TO_DATE('20-2-1981','%d-%m-%Y'),1600,300,30);

INSERT INTO EMP VALUES (7521,'WARD','SALESMAN',7698,STR_TO_DATE('22-2-1981','%d-%m-%Y'),1250,500,30);

INSERT INTO EMP VALUES (7566,'JONES','MANAGER',7839,STR_TO_DATE('2-4-1981','%d-%m-%Y'),2975,NULL,20);

INSERT INTO EMP VALUES (7654,'MARTIN','SALESMAN',7698,STR_TO_DATE('28-9-1981','%d-%m-%Y'),1250,1400,30);

INSERT INTO EMP VALUES (7698,'BLAKE','MANAGER',7839,STR_TO_DATE('1-5-1981','%d-%m-%Y'),2850,NULL,30);

INSERT INTO EMP VALUES (7782,'CLARK','MANAGER',7839,STR_TO_DATE('9-6-1981','%d-%m-%Y'),2450,NULL,10);

INSERT INTO EMP VALUES (7788,'SCOTT','ANALYST',7566,STR_TO_DATE('13-7-1987','%d-%m-%Y')-85,3000,NULL,20);

INSERT INTO EMP VALUES (7839,'KING','PRESIDENT',NULL,STR_TO_DATE('17-11-1981','%d-%m-%Y'),5000,NULL,10);

INSERT INTO EMP VALUES (7844,'TURNER','SALESMAN',7698,STR_TO_DATE('8-9-1981','%d-%m-%Y'),1500,0,30);

INSERT INTO EMP VALUES (7876,'ADAMS','CLERK',7788,STR_TO_DATE('13-7-1987', '%d-%m-%Y'),1100,NULL,20);

INSERT INTO EMP VALUES (7900,'JAMES','CLERK',7698,STR_TO_DATE('3-12-1981','%d-%m-%Y'),950,NULL,30);

INSERT INTO EMP VALUES (7902,'FORD','ANALYST',7566,STR_TO_DATE('3-12-1981','%d-%m-%Y'),3000,NULL,20);

INSERT INTO EMP VALUES (7934,'MILLER','CLERK',7782,STR_TO_DATE('23-1-1982','%d-%m-%Y'),1300,NULL,10);

INSERT INTO SALGRADE VALUES (1,700,1200);

INSERT INTO SALGRADE VALUES (2,1201,1400);

INSERT INTO SALGRADE VALUES (3,1401,2000);

INSERT INTO SALGRADE VALUES (4,2001,3000);

INSERT INTO SALGRADE VALUES (5,3001,9999);

끝
--- 

문제)

#1. 사원 테이블의 모든 레코드를 조회하시오.
SELECT * FROM emp;

#2. 사원명과 입사일을 조회하시오.
SELECT ename, hiredate FROM emp;

#3. 사원번호와 이름을 조회하시오.
SELECT empno, ename FROM emp;

#4. 사원테이블에 있는 직책의 목록을 조회하시오. (hint : distinct, group by)
SELECT DISTINCT job FROM emp GROUP BY job;

#5. 총 사원수를 구하시오. (hint : count)
SELECT COUNT(*) FROM emp;

#6. 부서번호가 10인 사원을 조회하시오.
SELECT ename FROM emp WHERE deptno = 10;

#7. 월급여가 2500이상 되는 사원을 조회하시오.
SELECT ename FROM emp WHERE sal >= 2500;

#8. 이름이 'KING'인 사원을 조회하시오.
SELECT ename FROM emp WHERE ename LIKE "KING";

#9. 사원들 중 이름이 S로 시작하는 사원의 사원번호와 이름을 조회하시오. (hint : like)
SELECT empno, ename FROM emp WHERE ename LIKE "S%";

#10. 사원 이름에 T가 포함된 사원의 사원번호와 이름을 조회하시오. (hint : like)
SELECT empno, ename FROM emp WHERE ename LIKE "%T%";

#11. 커미션이 300, 500, 1400 인 사원의 사번,이름,커미션을 조회하시오. (hint : OR, in )
SELECT empno, ename, comm FROM emp WHERE comm IN(300, 500, 1400);

#12. 월급여가 1200 에서 3500 사이의 사원의 사번,이름,월급여를 조회하시오. (hint : AND, between)
SELECT empno, ename, sal FROM emp WHERE sal BETWEEN 1200 AND 3500;

#13. 직급이 매니저이고 부서번호가 30번인 사원의 이름,사번,직급,부서번호를 조회하시오. 
SELECT ename, empno, job, deptno FROM emp WHERE job = 'MANAGER' AND deptno = 30;

#14. 부서번호가 30인 아닌 사원의 사번,이름,부서번호를 조회하시오. (not)
SELECT empno, ename, deptno FROM emp WHERE NOT(deptno = 30);

#15. 커미션이 300, 500, 1400 이 모두 아닌 사원의 사번,이름,커미션을 조회하시오. (hint : not in)
SELECT empno, ename, comm FROM emp WHERE comm NOT IN(300, 500, 1400);

#16. 이름에 S가 포함되지 않는 사원의 사번,이름을 조회하시오. (hint : not like)
SELECT empno, ename FROM emp WHERE ename NOT LIKE '%S%';

#17. 급여가 1200보다 미만이거나 3700 초과하는 사원의 사번,이름,월급여를 조회하시오. (hint : not, between)
SELECT empno, ename, sal FROM emp WHERE NOT(sal BETWEEN 1200 AND 3700);

#18. 직속상사가 NULL 인 사원의 이름과 직급을 조회하시오. (hint : is null, is not null)
SELECT ename, job FROM emp WHERE mgr IS NULL;

#19. 부서별 평균월급여를 구하는 쿼리 (hint : group by, avg())
SELECT AVG(sal) FROM emp GROUP BY deptno;

#20. 부서별 전체 사원수와 커미션을 받는 사원들의 수를 구하는 쿼리 (hint : group by, count())
SELECT * FROM dept;
SELECT * FROM emp;

SELECT deptno ,COUNT(ename) AS '부서별 전체 사원수' FROM emp GROUP BY deptno;
SELECT dept.deptno, COUNT(*) AS '부서별 전체 사원수'FROM emp, dept WHERE emp.deptno = dept.deptno GROUP BY emp.deptno;

SELECT COUNT(*) AS "커미션을 받는 사원들의 수" FROM emp WHERE comm IS NOT NULL;

#21. 부서별 최대 급여와 최소 급여를 구하는 쿼리 (hint : group by, min(), max())
SELECT deptno, MAX(sal) AS "최대급여", MIN(sal) AS "최소급여" FROM emp GROUP BY deptno;

#22. 부서별로 급여 평균 (단, 부서별 급여 평균이 2000 이상만) (hint : group by, having)
SELECT deptno, AVG(sal) AS "급여 평균" FROM emp GROUP BY deptno HAVING AVG(sal) >= 2000;

#23. 월급여가 1000 이상인 사원만을 대상으로 부서별로 월급여 평균을 구하라. 단, 평균값이 2000 이상인 레코드만 구하라. (hint : group by, having)
SELECT deptno , AVG(sal) AS '월급여 평균' FROM emp GROUP BY deptno HAVING AVG(sal) >= 2000;

#24. 사원명과 부서명을 조회하시오. (hint : inner join)
SELECT e.ename, d.dname FROM emp e, dept d WHERE e.deptno = d.deptno 

#25. 이름,월급여,월급여등급을 조회하시오. (hint : inner join, between)
SELECT * FROM salgrade;

SELECT * FROM emp;

SELECT e.ename, e.sal, s.grade FROM salgrade s, emp e WHERE e.sal BETWEEN s.losal AND s.hisal;

#26. 이름,부서명,월급여등급을 조회하시오. 
SELECT e.ename, d.dname, s.grade FROM emp e, dept d, salgrade s WHERE e.deptno = d.deptno AND e.sal BETWEEN s.losal AND s.hisal;

#27. 이름,직속상사이름을 조회하시오. (hint : self join
SELECT e.ename, e2.ename AS '직속상사이름' FROM emp e LEFT JOIN emp e2 ON e.mgr = e2.empno;

#28. 이름,직속상사이름을 조회하시오.(단 직속 상사가 없는 사람도 직속상사 결과가 null값으로 나와야 함) (hint : outer join)
###외부OUTER 조인. A LEFT JOIN B는 조인 조건에 만족하지 못하더라도 왼쪽 테이블 A의 행을 나타내고 싶을 때 사용한다. 반대로 A RIGHT JOIN B는 조인 조건에 만족하지 못하더라도 오른쪽 테이블 B의 행을 나타내고 싶을 때
SELECT e.ENAME AS "사원명", m.ENAME AS "상사명" FROM EMP e LEFT OUTER JOIN EMP m ON e.MGR = m.EMPNO;

