# MySQL

# 7-1.intro

### 데이터베이스
- 데이터의 집합
- 응용프로그램들의 통합된 정보들을 저장하여 운영할 수 있는 공용 데이터의 집합
- 효율적으로 저장,검색,갱신할 수 있도록 데이터 집합들끼리 연관시키고 조직화되어야함

### 데이터베이스 특성
- 실시간 접근성 : 사용자의 요구를 즉시 처리가능
- 계속적인 변화 : 정확한 값을 유지하려고 삽입,삭제,수정 작업 등을 이용하여 데이터를 지속적으로 갱신가능
- 동시 공유성 : 사용자마다 서로 다른 목적으로 사용하므로 동시에 여러 사람이 동일한 데이터에 접근,이용 가능
- 내용 참조 : 저장한 데이터 레코드의 위치나 주소가 아닌 사용자가 요구하는 데이터의 내용(데이터값)에 따라 참조가능

### DBMS 
- 데이터베이스를 관리하는 소프트웨어
- 여러 응용프로그램 또는 시스템이 동시에 DB에 접근하여 사용가능
- 필수 3기능
  - 정의 기능 : DB의 논리적,물리적 구조를 정의
  - 조작기능 : 데이터를 검색,삭제,갱신,삽입,삭제 기능
  - 제어기능 : DB의 내용 정확성과 안전성을 유지하도록 제어하는 기능
  
### DBMS 장단점
- 장점
  - 데이터 중복 최소화
  - 데이터의 일관성,무결성 유지
  - 데이터 보안 보장

- 단점
  - 운영비가 비싸다
  - 백업 및 복구에 대한 관리가 복잡
  - 부분적 DB 손실이 전체 시스템을 정지

