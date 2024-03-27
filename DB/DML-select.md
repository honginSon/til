# DML(Data Manipulation Language)

“DB에 저장된 자료들을 입력, 조회, 수정, 삭제하는 언어”

## 명령어

---

| 유형 | 동작 | 설명 |
| --- | --- | --- |
| SELECT | 조회 | 테이블 내 칼럼에 저장된 데이터를 조회 |
| INSERT | 삽입 | 데이터 추가 |
| UPDATE | 갱신 | 데이터 수정 |
| DELETE | 삭제 | 데이터 삭제 |

### SELECT 명령어

```sql
SELECT [ALL | DISTINCT] 속성명1, 속성명2...
FROM 테이블명1, ...
[WHERE 조건]
[GROUP BY 속성명1, ...]
[HAVING 그룹조건]
[ORDER BY 속성 [ASC | DESC] ];
```

- select 절

예제로 보자

[성적 테이블]

| 이름 | 과목 | 학점 |
| --- | --- | --- |
| 김철수 | C언어 | A |
| 한유리 | 자료구조 | A |
| 신짱구 | 자료구조 | A |
| 이훈이 | 알고리즘 | B |

```sql
SELECT 과목
FROM 성적;
```

| 과목 |
| --- |
| C언어 |
| 자료구조 |
| 자료구조 |
| 알고리즘 |

```sql
SELECT DISTINCT 과목
FROM 성적;
```

| 과목 |
| --- |
| C언어 |
| 자료구조 |
| 알고리즘 |

```sql
SELECT 과목
FROM 성적
WHERE 학점 = 'A';
```

| 과목 |
| --- |
| C언어 |
| 자료구조 |
| 자료구조 |
- where 절

```sql
SELECT *
FROM PRODUCT
WHERE PRICE BETWEEN 50000 AND 80000;
```

→ PRODUCT 테이블에서 PRICE가 50000보다 크거나 같고 80000보다 작거나 같은 튜플을 조회

```sql
SELECT *
FROM PRODUCT 
WHERE PRICE IN (40000, 50000, 60000);
```

→ 40000 또는 50000 또는 60000인 튜플을 조회

```sql
SELECT *
FROM PRODUCT
WHERE NAME LIKE '정보%';
```

→ NAME이 ‘정보’로 시작되는 튜플을 조회

```sql
SELECT *
FROM PRODUCT
WHERE NAME LIKE '[ABCD]%';
```

→ NAME의 첫 번째 문자가 ‘A’또는 ‘B’,’C’,’D’인 튜플을 조회

```sql
SELECT *
FROM PRODUCT
WHERE PRICE IS NULL;
```

→ PRICE가 NULL 값인 튜플을 조회