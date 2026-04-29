오후 4:50 2026-04-29

select first_name, last_name, salary , salary * 1.1 as '인상된 봉급', round(salary * 0.9) as '감축된 봉급' from employees;
select 칼럼명 사칙연산 정수 from 테이블 명 : 사칙연산을 수행한 후 조회 출력

-- null이 아닌 값을 'Y', null인 값을 'N'
select if(manager_id is not null, 'Y', 'N') from employees;


-- nullif : 2개의 값이 같으면 null로 조회, nullif(칼럼명, 칼럼명), 두 값이 같으면 null, 다르면 첫번째 값이 나옴
-- 조회열에서 값이 100이면 null, 아니면 원래값 조회
select nullif(manager_id, 100), manager_id from employees;

-- case문, 특정 조건에 따라 원하는 값으로 조회할때 사용, if문하고 비슷, when ~ then ~ else ~ end, 구조) select 조회할 칼럼 case when 조건1 then 결과 ... else 모든 조건에 맞지 않을 경우 결과 end from 테이블명;

select manager_id, case when manager_id = 100 then '100입니다.' else '100이 아닙니다.' end as 결과 from employees;

select department_id, case when department_id = 60 then 'IT부서' when department_id = 100 then '회계부서' else '기타부서' end as 결과 from employees where department_id in(60, 100) order by department_id desc;
