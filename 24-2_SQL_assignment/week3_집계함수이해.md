# 데이터 탐색 - 조건, 추출, 요약 연습문제(1)
#### 1. 포켓몬 중에 type2가 없는 포켓몬 수를 알 수 있는 쿼리
- ~가 없다 : `칼럼 IS NULL`
    - NULL은 =연산자를 안 씀 -> IS 연산자를 씀
![alt text](SQL_imagefile/week3_연습문제1.png)

#### 2. type2가 없는 포켓몬의 type1과 type1의 포켓몬 수를 알려주는 쿼리. 단, type1이 포켓몬 수가 큰 순으로 정렬
![alt text](SQL_imagefile/week3_연습문제2.png)

#### 3. type2에 상관없이 type1의 포켓몬 수를 알 수 있는 쿼리
![alt text](SQL_imagefile/week3_연습문제3.png)

#### 4. 전설 여부에 따른 포켓몬 수를 알 수 있는 쿼리
- GROUP BY 1 : SELECT의 첫 칼럼을 의미!
![alt text](SQL_imagefile/week3_연습문제4.png)

#### 5. 동명이인이 있는 이름은 무엇일까?
- 서브쿼리를 사용하면 HAVING을 사용하지 않고 실행가능
![alt text](SQL_imagefile/week3_연습문제5.png)

#### 6. trainer 테이블에서 "Iris" 트레이너의 정보를 알 수 있는 쿼리
![alt text](SQL_imagefile/week3_연습문제6.png)

#### 7. trainer 테이블에서 "Iris", "Whitney", "Cynthia" 트레이너의 정보를 알 수 있는 쿼리

```sql
WHERE
  name in ("Iris", "Whitney", "Cynthia")
```
```sql
WHERE
  (name = "Iris")
  OR (name = "Whitney")
  OR (name = "Cynthia")
```
![alt text](SQL_imagefile/week3_연습문제7.png)

#### 8. 전체 포켓몬 수는 얼마나 되나?
![alt text](SQL_imagefile/week3_연습문제8.png)

#### 9. 세대(generation) 별로 포켓몬 수가 얼마나 되는지 알 수 있는 쿼리
![alt text](SQL_imagefile/week3_연습문제9.png)

#### 10. type2가 존재하는 포켓몬 수?
![alt text](SQL_imagefile/week3_연습문제10.png)

#### 11. type2가 있는 포켓몬 중에 제일 많은 type1은 무엇인가?
![alt text](SQL_imagefile/week3_연습문제11.png)

#### 12. 단일(하나의 타입만 있는) 타입 포켓몬 중 많은 type1은 무엇인가?
![alt text](SQL_imagefile/week3_연습문제12.png)

#### 13. 포켓몬 이름에 "파"가 들어가는 포켓몬은?
- `칼럼 LIKE "파%"` : "파"로 시작하는 단어
- `칼럼 LIKE "%파"` : "파"로 끝나는 단어
- `칼럼 LIKE "%파%"` : "파"가 들어간 단어
![alt text](SQL_imagefile/week3_연습문제13.png)

#### 14. 뱃지가 6개 이상인 트레이너는 몇 명이 있나요?
![alt text](SQL_imagefile/week3_연습문제14.png)

#### 15. 트레이너가 보유한 포켓몬(trainer_pokemon)이 제일 많은 트레이너는 누구?
![alt text](SQL_imagefile/week3_연습문제15.png)

#### 16. 포켓몬을 많이 풀어준 트레이너는 누구?
![alt text](SQL_imagefile/week3_연습문제16.png)

#### 17. 트레이너 별로 풀어준 포켓몬의 비율이 20%가 넘는 포켓몬 트레이너는 누구?, 풀어준 포켓몬의비율=(풀어준 포켓몬 수/전체 포켓몬 수)
- COUNTIF(조건)
![alt text](SQL_imagefile/week3_연습문제17.png)

<br> <br>

# 데이터 탐색 - 조건/추출/요약 `정리`
![alt text](SQL_imagefile/week3_데이터탐색정리.png)

<br>

# 2-8. 새로운 집계함수 (GROUP BY ALL)

<br> <br>

# 3-1 Intro : SQL 쿼리 잘 작성하기

<br> <br>

# 3-2. SQL 쿼리 작성하는 흐름
- `지표`에 대한 고민 : 어떤 문제를 해결하기 위해 데이터가 필요한가?
- `지표 구체화` : 추상적이지 않고 구체적인 지표 명시(분자, 분모 표시)
- `지표 탐색` : 유사한 문제를 해결한 케이스 서칭 (해당 쿼리 리뷰)
- 유사한 케이스가 없을 경우 -> 쿼리 작성
    - 데이터가 있는 테이블 찾기
        - 1개
        - 2개 이상 -> 데이터셋 연결 방법 고민 (JOIN)
- 데이터 정합성 확인 : 예상한 결과와 동일한지 확인
- 쿼리 가독성 : 나중을 위해서 깔끔하게 쿼리 작성
- 쿼리 저장 : 쿼리는 재사용되므로 문서로 저장

<br>

# 3-3. 쿼리 작성 템플릿과 생산성 도구
```sql
# 쿼리를 작성하는 목표, 확인할 지표 :
# 쿼리 계산 방법 :
# 데이터의 기간 :
# Join KEY :
# 데이터 특징 :

SELECT

FROM
WHERE
```
이렇게 글로 템플릿을 만들어두면 쿼리 작성이 더 수월함

### 생산성 도구 : 템플릿 쉽게 사용하기
팀플릿 사용하자! 라고 제시하면 생기는 일  
템플릿 사용하는 것을 까먹음 -> 습관 형성이 안 됨  
이 부분을 개선하기 위해 **생산성 도구**를 활용

### 생산성 도구 - Espanso
- 윈도우, 맥, 리눅스 모두 사용 가능
- 특징 : 특정 단어 입력하면 원하는 문장(템플릿)으로 변경

