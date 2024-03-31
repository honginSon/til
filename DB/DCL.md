# DCL

### 데이터 제어어(Data Control Language)

---

*DB 관리자(DBA)가 데이터 보안, 무결성 유지, 병행 제어, 회복을 위해 사용하는 제어용 언어*

| 유형 | 동작 | 설명 |
| --- | --- | --- |
| GRANT | 사용 권한 부여 | DBA가 사용자에게 DB에 대한 권한을 부여하는 명령어 |
| REVOKE | 사용 권한 취소 | DBA가 사용자에게 부여했던 권한을 회수하기 위한 명령어 |
- GRANT

```sql
GRANT 권한 ON 테이블 TO 사용자;
```

→ 관리자가 사용자에게 테이블에 대한 권한을 부여

```sql
GRANT UPDATE ON 학생 TO 장길산;
```

→ 관리자가 사용자 장길산에게 ‘학생’ 테이블에 대해 UPDATE 할 수 있는 권한 부여

- REVOKE

```sql
REVOKE 권한 ON 테이블 FROM 사용자;
```

→ 관리자가 사용자에게 부여했던 테이블에 대한 권한을 회수

```sql
REVOKE UPDATE ON 학생 FROM 장길산;
```

→ 관리자가 사용자 장길산에게 ‘학생’ 테이블에 대해 UPDATE 할 수 있는 권한을 회수