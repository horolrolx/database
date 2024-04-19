# 1. 데이터 정의 언어(Data-definition language : DDL)
- DDL은 릴레이션 스키마를 정의하고, 릴레이션을 삭제하고, 릴레이션 스키마를 수정하는 명령어를 제공
- create table , alter table r add A D, drop table, alter table r drop A

        - ex) drop table student;        : 테이블과 그 내용 다 삭제
        - ex) delete from student;       : 테이블의 내용들은 다 삭제되지만 테이블은 유지
        - ex) alter table r add A D;     : r 테이블에다가 A라는 이름으로 속성, D라는 속성의 도메인 추가
        - ex) alter table r drop A;      : r 테이블의 attribute를 삭제


  
- select distinct dept_name from instructor;에서 'distinct'는 중복 제거

- select all dept_name from instructor;에서 'all'은 중복 포함

- SQL에서 where절에 and, or, not 사용 가능, <, >, <=, >=, <> 등 비교연산자도 사용 가능


  
- select 절은 질의의 결과 속성들을 나열하는데 사용
- from 절은 질의를 수행하기 위해 접근해야하는 릴레이션들을 나열한다, 여러 개의 릴레이션이 나열된다면 Cartesian Product과 같다.
- where 절은 from 절에 있는 릴레이션의 속성들을 포함하는 조건이다.



  
- SQL은 relation과 attributes를 as 구문을 이용해서 이름을 재정의할 수 있다. (ex) old-name as new-name, 단, as생략 가능)

        - ex) select distinct T.name
        from instructor as T, instructor as S
        where T.salary > S.salary and S.dept_name = 'Comp.Sci.`

        - select name, title
        from instructor natral join teaches, course
        where teaches.course_id = course.course_id;

        - select name, title
        from (instructor natural join teaches) join course using (course_id);


  
- select name
from instructor
where name like '%dar%'; -> dar이 포함된 모든 문자열을 찾는 쿼리

- select name
from instructor
where name like '__dar'; -> xxdar을 찾는 쿼리

- select name
from instructor
where name like '___%'; -> 3자 이상의 문자열을 찾는 쿼리

- name like '100\%' escape '\' -> 100%를 찾고 싶다면 escape문자인 /(슬래쉬) 사용



  
- Set Operations (집합 연산)
        union ( 합집합 )
        (select course_id from section where sem='Fall' and year = 2017)
        union
        (select course_id from section where sem='Spring' and year = 2018);
        //
        FALL 2017과 SPRING 2018 학기에 열린 모든 강의들의 학수 번호

        intersect (교집합)
        (select course_id from section where sem='Fall' and year = 2017)
        intersect
        (select course_id from section where sem='Spring' and year = 2018);
        //
        FALL 2017 또는 SPRING 2018 학기에 열린 모든 강의들의 학수 번호

        except (차집합)
        (select course_id from section where sem='Fall' and year = 2017)
        except
        (select course_id from section where sem='Spring' and year = 2018);
        //
        FALL 2017에 열리고 SPRING 2018 학기에 안 열린 모든 강의들의 학수 번호

- 기본적으로 set operation들은 중복을 없앤다.
- union all, intersect all, except all 처럼 all을 붙이면 중복을 보존한다.

- 