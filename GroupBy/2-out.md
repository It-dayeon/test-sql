# 코딩테스트 연습 > GROUP BY > 입양 시각 구하기 (1)

**문제 설명**

`ANIMAL_OUTS` 테이블은 동물 보호소에 입양 보낸 동물의 정보를 담은 테이블입니다.   
`ANIMAL_OUTS` 테이블 구조는 다음과 같으며,   
`ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `NAME`, `SEX_UPON_INTAKE`는  
각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

NAME	| TYPE | NULLABLE
--- | --- | ---
ANIMAL_ID |	VARCHAR(N) |	FALSE
ANIMAL_TYPE |	VARCHAR(N) |	FALSE
DATETIME |	DATETIME |	FALSE
NAME |	VARCHAR(N) |	TRUE
SEX_UPON_INTAKE |	VARCHAR(N) |	FALSE


💡 **보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다.    
9시부터 19시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요.    
이때 결과는 시간대 순으로 정렬해야 합니다.**

> SQL을 실행하면 다음과 같이 출력되어야 합니다.

HOUR |	COUNT
--- | ---
9	|1
10 |	2
11 |	13
12 |	10
13 |	14
14 |	9
15 |	7
16 |	10
17 |	12
18 |	16
19 |	2

---

```sql
SELECT HOUR(DATETIME) AS 'HOUR', COUNT(HOUR(DATETIME)) AS 'COUNT' 
FROM ANIMAL_OUTS 
GROUP BY HOUR
HAVING HOUR BETWEEN 9 AND 19;
```

---

**HOUR 함수**

- HOUR(time) : 시간을 알려주는 함수 (00~23)
- 예시 : SELECT HOUR('10:05:03'); => 10

---

### 참고 사항

[MySQL에서 제공하는 날자 관련 함수]

- DAYOFMONTH(date) : 날짜만 리턴해주는 함수. (1-31) 한달을 단위로.
- DAYOFYEAR(date) : 이역시 날짜만 리턴. (1-366) 1년을 단위로.
- TO_DAYS(date) : 연도와 달을 모두 날짜화 시켜서 리턴해줍니다.
                            (1999-01-01 = (1999 * 365) + (01 * 31) + 1)
- MONTH(date) : 달을 리턴해주는 함수.
- DAYNAME(date) : 요일을 문자로 리턴. (ex :'Thursday')
- MONTHNAME(date) : 달을 문자로 리턴. (ex :'February')
- WEEK(date) : 해당 연도에 몇번째 주인지를 리턴 (0-52)
- YEAR(date) : 연도를 리턴 (1000-9999)
- HOUR(time) : 시간 리턴 
- MINUTE(time) : 분 리턴
- SECOND(time) : 초 리턴

- DATE_FORMAT(date,format)

     `%W'    Weekday name (`Sunday'..`Saturday')
     `%D'    Day of the month with english suffix (`1st', `2nd', `3rd',
             etc.)
     `%Y'    Year, numeric, 4 digits
     `%y'    Year, numeric, 2 digits
     `%a'    Abbreviated weekday name (`Sun'..`Sat')
     `%d'    Day of the month, numeric (`00'..`31')
     `%e'    Day of the month, numeric (`0'..`31')
     `%m'    Month, numeric (`01'..`12')
     `%c'    Month, numeric (`1'..`12')
     `%b'    Abbreviated month name (`Jan'..`Dec')
     `%j'    Day of year (`001'..`366')
     `%H'    Hour (`00'..`23')
     `%k'    Hour (`0'..`23')
     `%h'    Hour (`01'..`12')
     `%I'    Hour (`01'..`12')
     `%l'    Hour (`1'..`12')
     `%i'    Minutes, numeric (`00'..`59')
     `%r'    Time, 12-hour (`hh:mm:ss [AP]M')
     `%T'    Time, 24-hour (`hh:mm:ss')
     `%S'    Seconds (`00'..`59')
     `%s'    Seconds (`00'..`59')
     `%p'    `AM' or `PM'
     `%w'    Day of the week (`0'=Sunday..`6'=Saturday)
     `%U'    Week (`0'..`52'), Sunday is the first day of the week.
     `%u'    Week (`0'..`52'), Monday is the first day of the week.
     `%%'    Single `%' characters are ignored.  Use `%%' to produce a
             literal `%' (for future extensions).



출처: https://jang8584.tistory.com/7 [개발자의 길]
