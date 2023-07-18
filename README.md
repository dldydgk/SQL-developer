# SQL-developer
sqldeveloper의 사용자 추가와 테이블 생성

### 사용자를 추가한다
``` java
create user classmanger
IDENTIFIED BY classmanger
DEFAULT TABLESPACE users
TEMPORARY  TABLESPACE temp;
```
### 새로 생성한 유저 classmanger에 권한을 부여한다
```java
GRANT COMMIT to classmanger;
GRANT RESOURCE to classmanger;
GRANT dba to classmanger;
```

### 새로 만든 classmanger에 성적DB를 만들어서 연결한다  
![image](https://github.com/dldydgk/SQL-developer/assets/126844590/dbc3ac40-c6cb-496e-8909-2cd375cb2b5b)

### 이제 새로 만든 성적DB라는 테이블에다가 자신이 원하는 데이터를 추가한다
``` java
create table grade_table(
idx NUMBER(10) not null,
num NUMBER(5) not null,
name VARCHAR2(20) not null,
sub1 VARCHAR2(20) not null,
score1 NUMBER(3) not null,
sub2 VARCHAR2(20) not null,
score2 NUMBER(3) not null,
sub3 VARCHAR2(20) not null,
score3 NUMBER(3) not null,
total NUMBER(3) not null,
avg NUMBER(3) not null
);
DROP table grade_table;

alter table grade_table add(
CONSTRAINT grade_idx_pk PRIMARY key(idx));

create SEQUENCE grade_idx_pk start with 1;

insert into grade_table(idx, num, name, sub1,score1,sub2,score2,sub3,score3,total,avg)
VALUES (grade_idx_pk.nextval, 21116, '이용하', '국어', 65, '한국사', 54, '영어', 77, 196, round((196/3)));
```
