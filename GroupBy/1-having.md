# 코딩테스트 연습 > SELECT > 동명 동물 수 찾기

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


💡 **동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요.  
이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.**

> SQL을 실행하면 다음과 같이 출력되어야 합니다.

예를 들어 ANIMAL_INS 테이블이 다음과 같다면

ANIMAL_ID |	ANIMAL_TYPE |	DATETIME | INTAKE_CONDITION |	NAME | SEX_UPON_INTAKE
--- | --- | --- | --- | --- | --- |
A396810 |	Dog |	2016-08-22 16:13:00 |	Injured |	Raven |	Spayed Female
A377750 |	Dog |	2017-10-25 17:17:00 |	Normal |	Lucy |	Spayed Female
A355688 |	Dog |	2014-01-26 13:48:00 |	Normal |	Shadow |	Neutered Male
A399421 |	Dog |	2015-08-25 14:08:00 |	Normal |	Lucy |	Spayed Female
A400680 |	Dog |	2017-06-17 13:29:00 |	Normal |	Lucy |	Spayed Female
A410668 |	Cat |	2015-11-19 13:41:00 |	Normal |	Raven |	Spayed Female

Raven 이름은 2번 쓰였습니다.   
Lucy 이름은 3번 쓰였습니다  
Shadow 이름은 1번 쓰였습니다.  

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

NAME |	COUNT
--- | ---
Lucy |	3
Raven |	2
---

```sql
SELECT NAME, COUNT(NAME) FROM ANIMAL_INS GROUP BY NAME HAVING COUNT(NAME) > 1;
```
