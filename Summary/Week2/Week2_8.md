# SQL

# 8-1. SQL (Structured Query Language)
- 데이터를 보다 쉽게 검색,추가,삭제,수정 같은 조작을 할 수 있도록 고안된 언어
- 관계형 데이터베이스에서 데이터를 조작하고 쿼리하는 수단

### DML
- 데이터를 조작
- INSERT, UPDATE, DELETE, SELECT

### DDL
- 데이터베이스의 스키마를 정의하거나 조작하기 위해 사용함
- CREATE, DROP, ALTER

### DCL
- 데이터 제어,권한 관리,데이터 보안,무결성 정의
- GRANT, REVOKE

### DB 생성하기
```sql
mysql -uroot -p
create database DB명;
create database connectdb;
```

### 사용자 생성,권한 주기
```sql
grant all privileges on DB명,* to 계정이름@'%' identified by '암호';
//@'%' 어떤 클라이언트여도 접근 가능
grant all privileges on DB명,* to 계정이름@'localhost' identified by '암호';
//@'%'localhost' 현재 컴퓨터에서만 접근 가능

grant all privileges on connectdb.* to connectuser@'%' identified by 'connect123!@#';
flush privileges;

### DB 접속하기
```sql
mysql -h호스트명 -uDB계정명 -p 데이터베이스이름
mysql –h127.0.0.1 –uconnectuser –p connectdb 
```

### MySQL 연결 끊기
```sql
QUIT
exit
```

### MySQL 버전과 현재 날짜 구하기
```sql
SELECT VERSION(), CURRENT_DATE;
```

### 특징
- 키워드는 대소문자를 구별하지 않음
- 쿼리를 이용해서 계산식의 결과도 구할 수 있음
- 여러 문장을 한 줄에 연속으로 붙여서 실행가능함
- 하나의 SQL은 여러 줄로 입력가능함
- SQL을 입력하는 도중에 취소할 수 있음

### DBMS에 존재하는 데이터베이스 확인하기
```sql
show databases;
```

### 데이터베이스 전환하기
```sql
use mydb;
```

### 테이블 구성 요소
- 테이블 : DBMS의 기본적 저장구조, 한 개 이상의 column과 0개 이상의 row로 구성
- 열(column) : 테이블 상의 단일 종류의 데이터를 나타냄, 특정 데이터 타입 및 크기를 가짐
- 행(row) : column들의 값의 조합,레도르, 기본키에 의해 구분됨
- field : row와 colum의 교차점으로 field는 데이터를 포함할 수 있고 없을 때는 NULL값을 가지고있음

### 테이블 구조 확인
```sql
desc EMPLOYEE;
```

# 8-2. DML
- SELECT - 검색
- INSERT - 등록
- UPDATE - 수정
- DELETE - 삭제

### SELECT
```sql
SELECT(DISTINCT) 칼럼명(ALIAS) FROM 테이블명;
SELECT * FROM DEPARTMENT;
SELECT empno as 사번, name as 이름, job as 직업 FROM employee;  //ALIAS 지정
SELECT concat( empno, '-', deptno) AS '사번-부서번호' FROM employee;  //문자열 결합
SELECT distinct deptno FROM employee;  //중복행 제거
SELECT empno, name, job FROM employee order by name;  //정렬
```

### Where
```sql
WHERE title = "staff"
WHERE salary BETWEEN 1000 AND 2000
WHERE hiredate < '1981-01-01'

SELECT name, job FROM employee WHERE name like '%A%';   //이름이 A로 시작하는 사람, _이면 두번째
```

### 함수 사용
```sql
SELECT UPPER('SEoul'), UCASE('seOUL');
SELECT LOWER('SEoul'), LCASE('seOUL');
SELECT SUBSTRING('Happy Day',3,2);
SELECT LPAD('hi',5,'?'),LPAD('joe',7,'*');   //채워줌
SELECT LTRIM(' hello '), RTRIM(' hello ');   //공백제거
SELECT TRIM(' hi '),TRIM(BOTH 'x' FROM 'xxxhixxx');   //공백제거
SELECT ABS(2), ABS(-2);   //절대값 구함
SELECT MOD(234,10), 253 % 7, MOD(29,9);   //나머지 구함
```

### CAST 형변환
CAST (expression AS type)
CONVERT (expression,type)
CONVERT (expr USING transcoding_name)
![sql](https://user-images.githubusercontent.com/48993188/72698580-232d8c00-3b88-11ea-9e41-661da858bd92.png)
```sql
select cast(now() as date);
select cast(1-2 as unsigned);
```

### 그룹함수
```sql
SELECT AVG(salary) , SUM(salary)
FROM employee
WHERE deptno = 30;

SELECT deptno, AVG(salary) , SUM(salary)
FROM employee
group by deptno;
```

### INSERT
```sql
INSERT INTO 테이블명(필드1,필드2, ...) VALUES(필드1값, 필드2값, ...);
INSERT INTO 테이블명 VALUES (필드1값,필드2값, ...); //모든 필드값을 입력해야함
INSERT INTO ROLE (role_id, description) values ( 200, 'CEO');
```

### UPDATE
```sql
UPDATE 테이블명 SET 필드1 = 필드값,필드2 = 필드값 , ... WHERE 조건식
UPDATE ROLE SET description = 'CTO' WHERE role_id = 200;
```

### DELETE
```sql
DELETE FROM 테이블명 WHERE 조건식
DELETE FROM ROLE WHERE role_id = 200;
```

# 8-3. DDL (데이터 정의어)
![데이터타입1](https://user-images.githubusercontent.com/48993188/72702667-df8e4e80-3b96-11ea-8586-edef9087a7c5.png)
![데이터타입2](https://user-images.githubusercontent.com/48993188/72702694-f46ae200-3b96-11ea-9f23-71f15f054d7e.png)

### 테이블 생성
```sql
CREATE TABLE 테이블명(
  필드명1 타입[NULL | NOT NULL][DEFAULT][AUTO_INCREMENT],
  필드명2 타입[NULL | NOT NULL][DEFAULT][AUTO_INCREMENT],
  필드명3 타입[NULL | NOT NULL][DEFAULT][AUTO_INCREMENT],
  ...
  PRIMARY KEY(필드명)
  );
CREATE TABLE EMPLOYEE2(   
  empno      INTEGER NOT NULL PRIMARY KEY,  
  name       VARCHAR(10),   
  job        VARCHAR(9),   
  boss       INTEGER,   
  hiredate   VARCHAR(12),   
  salary     DECIMAL(7, 2),   
  comm       DECIMAL(7, 2),   
  deptno     INTEGER
  );
  ```
### 테이블 수정(추가/삭제)
```sql
alter table 테이블명
      add 필드명 타입 [NULL | NOT NULL][DEFAULT][AUTO_INCREMENT];
alter table 테이블명
      drop 필드명;
alter table 테이블명
      change 필드명 타입 [NULL | NOT NULL][DEFAULT][AUTO_INCREMENT];
alter table 테이블명 rename 변경할 이름;
drop table 테이블명;
```
 
