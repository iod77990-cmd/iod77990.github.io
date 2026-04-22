오전 9:32 2026-04-22

> - change와 rename 차이
> - 문제풀이

### change와 rename 차이

- CHANGE

**이름, 타입, 제약조건을 변경할 때 사용**

```sql
alter table name change oldCol newCol type [constraints];
```

- RENAME

**컬럼의 이름이나 테이블의 이름을 바꿀 때 사용**

```sql
alter table name rename oldColumn to newColumn;

rename table oldName to newName;
```

문제)

```sql
# a5 데이터베이스 삭제/생성/선택
CREATE DATABASE a5;
DROP DATABASE a5;
USE a5;

# 부서(dept) 테이블 생성 및 홍보부서 기획부서 추가
CREATE TABLE dept (
    Did INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    dname VARCHAR(100)
);

INSERT INTO dept SET dname = '홍보부서';
INSERT INTO dept SET dname = '기획부서';

DROP TABLE dept;

# 사원(emp) 테이블 생성 및 홍길동사원(홍보부서), 홍길순사원(홍보부서), 임꺽정사원(기획부서) 추가
CREATE TABLE emp(
    Eid INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    ename VARCHAR(100),
    deptno INT
);

DROP TABLE emp;

INSERT INTO emp SET ename = '홍길동', deptno = 1;
INSERT INTO emp SET ename = '임꺽정', deptno = 2;

SELECT * FROM emp;
SELECT * FROM dept;

# 홍보를 마케팅으로 변경
UPDATE dept SET dname = '마케팅 부서' WHERE dname = '홍보부서';


# 마케팅을 홍보로 변경
UPDATE dept SET dname = '마케팅 부서' WHERE dname = '홍보 부서';

## 구조를 변경하기로 결정(사원 테이블에서, 이제는 부서를 이름이 아닌 번호로 기억)
ALTER TABLE emp ADD deptno INT;

# 사장님께 드릴 인명록을 생성
SELECT * FROM emp;
SELECT * FROM dept;

# 사장님께서 부서번호가 아니라 부서명을 알고 싶어하신다.
SELECT d.dname, e.ename FROM dept d, emp e WHERE d.Did = e.deptno;

# 사장님께 드릴 인명록을 생성(v2, 부서명 포함, ON 없이)
SELECT d.dname, e.ename FROM dept d, emp e WHERE d.Did = e.deptno;

# 사장님께 드릴 인명록을 생성(v3, 부서명 포함, 올바른 조인 룰(ON) 적용)
SELECT d.dname, e.ename FROM dept d INNER JOIN emp e ON d.Did = e.deptno;

# 사장님께 드릴 인명록을 생성(v4, 사장님께서 보시기에 편한 칼럼명(AS))
SELECT d.dname AS '부서명', e.ename AS '사원명' FROM dept d INNER JOIN emp e ON d.Did = e.deptno;

# 사장님께 드릴 인명록을 생성(v5, 테이블 AS 적용)
SELECT d.dname AS '부서명', e.ename AS '사원명', d.Did AS '부서번호' FROM dept d INNER JOIN emp e ON d.Did = e.deptno;
```


