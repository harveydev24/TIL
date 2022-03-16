# SQL

- 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어



## 명령어 종류

- 데이터 정의 언어(DDL: Data Definition Language)
  - 각 릴레이션을 정의하기 위해 사용하는 언어
  - CREATE, ALTER, DROP 등
- 데이터 조작 언어(DML: Data Manipulation Language)
  - 데이터를 조회/추가/수정/삭제하기 위한 언어
  - SELECT, INSERT, UPDATE 등
- 데이터 제어 언어(DCL: Data Control Language)
  - 사용자 관리 및 사용자별로 릴레이션 또는 데이터를 관리하고 접근하는 권한을 다루기 위한 언어
  - GRANT, REVOKE 등



## SQL의 언어적 특성

- 일반적으로 SQL은 대소문자를 가리지 않음
- SQL 명령은 반드시 세미콜론으로 끝남
- 고유의 값은 따옴표로 감싸줌



## 명령어

- SELECT

  ```mysql
  SELECT * FROM 테이블명 WHERE 컬럼1='조건1' AND 컬럼2='조건2'
  
  SELECT 컬럼1, 컬럼2, 컬럼3 FROM 테이블명
  
  SELECT 컬럼1, 컬럼2, 컬럼3 FROM 테이블명 ORDER BY 컬럼1 ASC
  SELECT 컬럼1, 컬럼2, 컬럼3 FROM 테이블명 ORDER BY 컬럼1 DESC
  
  # 중복 제거
  SELECT DISTINCT 컬럼1 FROM 테이블명
  
  # 컬럼2가 00부터 00사이
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 BETWEEN 00 AND 00
  
  # 컬럼2가 IN 다음 집합에 속하면
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 IN (00, 00, 00, 00)
  
  # 문자열 매칭
  # %는 그 자리에 문자가 있든 없든 상관 X
  # _는 그 자리에 반드시 문자가 존재해야함
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 LIKE '%단어%'
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 LIKE '%단어%'
  
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 IS NULL
  SELECT 컬럼1 FROM 테이블 WHERE 컬럼2 IS NOT NULL
  ```



- UPDATE

  ```mysql
  UPDATE 테이블명 SET 컬럼1='값1', 컬럼2='값2', 컬럼3='값' WHERE 필드 LIKE '조건'
  ```



- INSERT

  ```mysql
  INSERT INTO 테이블명(컬럼1, 컬럼2) VALUES ('값1', '값2')
  ```



- DROP

  ```mysql
  DROP TABLE 테이블명
  ```

  

- CREATE

  ```mysql
  CREATE TABLE 테이블명(
  	컬럼명 타입 조건,
    ID VARCHAR(15) PRIMARY KEY,
    PASSWORD VARCHAR(15) NOT NULL,
    NUMBER INTEGER(5)
  )
  ```

  

- GROUP BY

  ```mysql
  SELECT 컬럼1 FROM 테이블명 GROUP BY 컬럼1
  
  SELECT 컬럼1 FROM 테이블명 WHERE 조건 GROUP BY 컬럼1 HAVING SUM(컬럼2) >= 30
  ```



- JOIN

  ```mysql
  SELECT 컬럼 FROM 테이블1 INNER JOIN 테이블2 ON 컬럼=컬럼
  
  SELECT 컬럼 FROM 테이블1 LEFT OUTER JOIN 테이블2 ON 컬럼=컬럼
  ```

  

- ALTER

  ```mysql
  # 컬럼 추가
  ALTER TABLE 테이블명 ADD 새컬럼 VARCHAR(10) NULL
  
  # 컬럼 변경
  ALTER TABLE 테이블명 ALTER COLUMN 컬럼 VARCHAR(10) NULL
  
  # 컬럼 삭제
  ALTER TABLE 테이블명 DROP COLUMN 컬럼
  ```



- UNION

  ```mysql
  # 두 개의 쿼리 결과를 합침. 컬럼과 자료형의 순서가 맞아야하며 중복데이터는 제거됨
  SELECT 컬럼1, 컬럼2 FROM 테이블1 UNION SELECT 컬럼1, 컬럼2 FROM 테이블2
  ```



