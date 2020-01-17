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
