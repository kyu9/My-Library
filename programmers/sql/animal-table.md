---
description: MySQL version
---

# Animal Table - MySQL

## 모든 레코드 조회하기

### 문제

동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

### 풀이

sql문하면 빼놓을 수 없는 너무나도 간단한 문제이다.

select문 정도는 쉽게 했다.

```sql
SELECT * FROM ANIMAL_INS;
```

## 최대값 구하기

### 문제

가장 늦게 들어온 동물은 Anna이고, Anna는 2013-11-18 17:03:00에 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| 시간                  |
| ------------------- |
| 2013-11-18 17:03:00 |

※ 컬럼 이름(위 예제에서는 "시간")은 일치하지 않아도 됩니다.

```sql
SELECT MAX(DATETIME) AS '시간' FROM ANIMAL_INS;
```

자 MAX이라는 걸 처음 보는 것 같은데

최대값이나 최소값을 가져올 수 있는 함수가 존재한다.

일단 최대값이나 최소값이기 때문에 숫자형에만 사용할 수 있을 것 같지만 굳이 그런건 아니고 문자열에도 사용할 수 있다는 점..!

MAX(필드명), MIN(필드명) : 이렇게 뒤에 필드명을 붙혀야 한다

그리고 추가 옵션이였던 '시간'이라는 필드는 존재하지 않았지만 어떻게 해야 없는 필드명을 추가할 수 있을까?

AS는 SELECT에 별칭을 주는 방법이다.

SELECT은 필드명으로 하기 때문에 출력 또한 항상 필드명으로 출력이 되는데, 필요한 이름으로 필드명을 출력하기 위해서는 AS문을 사용할 필요가 있다.

SELECT \~\~\~ AS '원하는이름' : 이렇게 SELECT문 뒤에 ' ' 사이에 원하는 값을 넣어서 사용한다.

## 이름이 없는 동물의 아이디

### 문제

동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

이름이 없는 채로 들어온 동물의 ID는 A368930입니다. 따라서 SQL을 실행하면 다음과 같이 출력되어야 합니다.

| ANIMAL_ID |
| --------- |
| A368930   |

### 풀이

```sql
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME is null;
```

null값을 체크하는 어렵지 않은 문제였다!

## 역순 정렬하기

### 문제

동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

| NAME   | DATETIME            |
| ------ | ------------------- |
| Rocky  | 2016-06-07 09:17:00 |
| Shelly | 2015-01-29 15:01:00 |
| Benji  | 2016-04-19 13:28:00 |
| Jackie | 2016-01-03 16:25:00 |
| \*Sam  | 2016-03-13 11:17:00 |

..이하 생략

### 풀이

```sql
SELECT NAME, DATETIME FROM ANIMAL_INS order by ANIMAL_ID desc
```

## 이름이 있는 동물의 아이디

동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

```sql
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME is not null;
```

## 아픈 동물 찾기

동물 보호소에 들어온 동물 중 아픈 동물[1](https://programmers.co.kr/learn/courses/30/lessons/59036#fn1)의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION="Sick";
```

## 어린 동물 찾기

동물 보호소에 들어온 동물 중 젊은 동물[1](https://programmers.co.kr/learn/courses/30/lessons/59037#fn1)의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged'
```

## 동물의 아이디와 이름

동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
```

## 여러 기준으로 정렬하기

동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME, DATETIME desc

```

와 뭔가 두 번째의 정렬 방법은 그냥 정렬하는 다음에 같이 적어주는 것 이였는데 실제로 맞았다..!

\-> 여러 기준으로 정렬하기 위해서는 order by 뒤에다가 계속 작성합시다!

## 상위 n개 레코드

동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.

```sql
-- 코드를 입력하세요
SELECT NAME 
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```

아하 지정된 범위만큼 선택해서 출력하고 싶다면 사용하는 키워드는 LIMIT이다

추가적인 예시로

```sql
...
...
LIMIT 3, 7 
```

이렇게 작성하게 된다면 조회한 값들 중에서 3번째 부터 7번까지의 정보를 추출할 수 있다!
