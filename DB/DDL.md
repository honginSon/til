## DDL(Data Definition Language)

“데이터를 담는 그릇을 정의하는 언어”

### 대상

---

도메인

- 하나의 속성이 가질 수 있는 원자값들의 집합

스키마

- DB의 구조, 제약조건 등의 정보를 담고 있는 기본적인 구조(틀)

- 외부 스키마 - 사용자나 개발자의 관점에서 필요로 하는 DB의 논리적 구조

- 개념 스키마 - DB의 전체적인 논리적 구조, 전체적인 뷰, 개체 간의 관계, 제약조건, 접근 권한, 무결성, 보안에 대해 정의

- 내부 스키마 - 물리적 저장 장치의 관점에서 보는 DB 구조, 실제로 DB에 저장될 레코드의 형식 정의

테이블 : 데이터 저장 공간

뷰 : 하나 이상의 물리 테이블에서 유도되는 가상의 테이블

인덱스 : 검색을 빠르게 하기 위한 데이터 구조

### 명령어

---

- CREATE

DB 오브젝트 생성

- ALTER

DB 오브젝트 변경

- DROP

DB 오브젝트 삭제

- TRUNCATE

DB 오브젝트 내용 삭제

### TABLE 관련 DDL

---

1. CREATE TABLE

```sql
CREATE TABLE 테이블명
(
	컬럼명 데이터타입 [제약조건],
	...
);
```

사원 테이블 작성 예시

```sql
CREATE TABLE 사원
(
	사번 VARCHAR(10) PRIMARY KEY, -- 기본키 설정
	업무 VARCHAR(20) FOREIGN KEY REFERENCES 참조테이블(기본키), -- 외래키 설정
	이름 VARCHAR(10) UNIQUE, -- 유일한 값,
	생년월일 CHAR(8) NOT NULL,
	성별 CHAR(1) CHECK (성별 = 'M' OR 성별 = 'F'), -- 개발자 정의 제약조건
	입사일 DATE DEFAULT SYSDATE -- 기본값 설정
);
```

1. ALTER TABLE
- 컬럼 추가

```sql
ALTER TABLE 테이블명 ADD 컬럼명 데이터타입 [제약조건];
```

- 컬럼 수정

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입 [제약조건];
```

- 컬럼 삭제

```sql
ALTER TABLE 테이블명 DROP COLUMN 컬럼명;
```

1. DROP TABLE

```sql
DROP TABLE 테이블명 [CASCADE | RESTRICT];
```

- CASCADE

참조하는 테이블까지 연쇄적으로 제거

- RESTRICT

다른 테이블이 삭제할 테이블을 참조 중이면 제거 X

1. TRUNCATE TABLE
- 테이블 내의 데이터들을 삭제하는 명령

```sql
TRUNCATE TABLE 테이블명;
```

### VIEW 관련 DDL

---

1. CREATE VIEW

```sql
CREATE VIEW 뷰이름 AS
조회쿼리;
```

1. CREATE OR REPLACE VIEW
- 뷰를 교체하는 명령

```sql
CREATE OR REPLACE VIEW 뷰이름 AS
조회쿼리;
```

1. DROP VIEW

```sql
DROP VIEW 뷰이름;
```

### INDEX 관련 DDL

---

1. CREATE INDEX
- 사원 테이블의 사번 컬럼에 대해 사번인덱스라는 인덱스 명으로 인덱스 생성

```sql
CREATE INDEX 사번인덱스 ON 사원(사번);
```

1. ALTER INDEX
- 기존 인덱스를 삭제하고 신규 인덱스를 생성하는 방식으로 사용을 권고

1. DROP INDEX

```sql
DROP INDEX 사번인덱스;
```