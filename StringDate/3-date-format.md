# 코딩테스트 연습 > STRING, DATE > DATETIME에서 DATE로 형 변환

**문제 설명**

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다.   
`ANIMAL_INS` 테이블 구조는 다음과 같으며,   
`ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는  
각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

NAME	| TYPE | NULLABLE
--- | --- | ---
ANIMAL_ID |	VARCHAR(N) |	FALSE
ANIMAL_TYPE |	VARCHAR(N) |	FALSE
DATETIME |	DATETIME |	FALSE
INTAKE_CONDITION |	VARCHAR(N) |	FALSE
NAME |	VARCHAR(N) |	TRUE
SEX_UPON_INTAKE |	VARCHAR(N) |	FALSE


💡 **ANIMAL_INS 테이블에 등록된 모든 레코드에 대해,   
각 동물의 아이디와 이름, `들어온 날짜`를 조회하는 SQL문을 작성해주세요.     
이때 결과는 아이디 순으로 조회해야 합니다.**  

- 들어온 날짜 : 시각(시-분-초)을 제외한 날짜(년-월-일)만 보이기

> SQL을 실행하면 다음과 같이 출력되어야 합니다.

예를 들어 ANIMAL_INS 테이블이 다음과 같다면

ANIMAL_ID |	ANIMAL_TYPE |	DATETIME | INTAKE_CONDITION |	NAME | SEX_UPON_INTAKE
--- | --- | --- | --- | --- | --- |
A349996 |	Cat |	2018-01-22 14:32:00 |	Normal |	Sugar |	Neutered Male
A350276 |	Cat |	2017-08-13 13:50:00 |	Normal |	Jewel |	Spayed Female
A350375 |	Cat |	2017-03-06 15:01:00 |	Normal |	Meo |	Neutered Male
A352555 |	Dog |	2014-08-08 04:20:00 |	Normal |	Harley |	Spayed Female
A352713 |	Cat |	2017-04-13 16:29:00 |	Normal |	Gia |	Spayed Female

SQL문을 실행하면 다음과 같이 나와야 합니다.

ANIMAL_ID |	NAME |	날짜
--- | --- | --- |
A349996 |	Sugar |	2018-01-22
A350276 |	Jewel |	2017-08-13
A350375 |	Meo |	2017-03-06
A352555 |	Harley |	2014-08-08
A352713 |	Gia |	2017-04-13

---

```sql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME,'%Y-%m-%d') AS 날짜
FROM ANIMAL_INS
ORDER BY ANIMAL_ID; 
```

---

#### 참고

FORAMT |  설명 
--- | ---
 %M | 월(Janeary, December, ...)
 %W | 요일(Sunday, Monday, ...)
 %D | 월(1st, 2dn, 3rd, ...)
 %Y | 연도(1987, 2000, 2013)
 %y | 연도(87, 00, 13) 
 %X | 연도(1987, 2000) %V와 같이 쓰임.
 %x | 연도(1987, 2000) %v와 같이 쓰임.
 %a | 요일(Sun, Tue, ...)
 %d | 일(00, 01, 02, ...)  
 %e | 일(0, 1, 2, ...) 
 %c | 월(1, 2, ..., 12)  
 %b | 월(Jan, Dec, ...) 
 %j | 몇번째 일(120, 365) 
 %H | 시(00, 01, 02, 13, 24) 
 %h | 시(01, 02, 12)
 %I(대문자 아이) |  시(01, 02, 12)
 %l(소문자 엘) | 시(1, 2, 12) 
 %i | 분(00, 01, 30) 
 %r | "hh:mm:ss AM|PM" 
 %T | "hh:mm:ss" 
 %S | 초 
 %s | 초 
 %p | AM, PM 
 %w | 요일(0, 1, 2) 0:일요일 
 %U | 주(시작:일요일) 
 %u | 주(시작:월요일) 
 %V | 주(시작:일요일) 
 %v | 주(시작:월요일) 
