### 집합 연산자

---

- UNION
- UNION ALL
- INTERSECT
- MINUS

[EMP 테이블]

| EMPNO | ENAME | JOB | SAL |
| --- | --- | --- | --- |
| 1001 | 홍길동 | 대리 | 1000 |
| 1002 | 임꺽정 | 과장 | 1500 |
| 1003 | 장길산 | 차장 | 2000 |
| 1004 | 강은미 | 부장 | 2500 |
- UNION

```sql
SELECT ENAME
FROM EMP
WHERE SAL <= 2000
UNION
SELECT ENAME
FROM EMP
WHERE SAL >= 1500;
```

| ENAME |
| --- |
| 홍길동 |
| 임꺽정 |
| 장길산 |
| 강은미 |

→ 중복을 제거한 합집합

- UNION ALL

```sql
SELECT ENAME
FROM EMP
WHERE SAL <= 2000
UNION ALL
SELECT ENAME
FROM EMP
WHERE SAL >= 1500;
```

| ENAME |
| --- |
| 홍길동 |
| 임꺽정 |
| 장길산 |
| 임꺽정 |
| 장길산 |
| 강은미 |

→ 중복을 제거하지 않는 합집합

- INTERSECT

```sql
SELECT ENAME
FROM EMP
WHERE SAL <= 2000
INTERSECT
SELECT ENAME
FROM EMP
WHERE SAL >= 1500;
```

| ENAME |
| --- |
| 임꺽정 |
| 장길산 |

→ 교집합

- MINUS

```sql
SELECT ENAME 
FROM EMP
WHERE SAL <= 2000
MINUS
SELECT ENAME
FROM EMP
WHERE SAL >= 1500;
```

| ENAME |
| --- |
| 홍길동 |

→ 차집합