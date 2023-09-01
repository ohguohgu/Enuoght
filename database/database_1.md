# 자동차 평균 대여 기간 구하기

<h3>문제 설명</h3>
다음은 어느 자동차 대여 회사의 자동차 대여 기록 정보를 담은 CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블입니다. CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블은 아래와 같은 구조로 되어있으며, HISTORY_ID, CAR_ID, START_DATE, END_DATE 는 각각 자동차 대여 기록 ID, 자동차 ID, 대여 시작일, 대여 종료일을 나타냅니다.
<br><br>
<h3>문제</h3>
CAR_RENTAL_COMPANY_RENTAL_HISTORY 테이블에서 평균 대여 기간이 7일 이상인 자동차들의 자동차 ID와 평균 대여 기간(컬럼명: AVERAGE_DURATION) 리스트를 출력하는 SQL문을 작성해주세요. 평균 대여 기간은 소수점 두번째 자리에서 반올림하고, 결과는 평균 대여 기간을 기준으로 내림차순 정렬해주시고, 평균 대여 기간이 같으면 자동차 ID를 기준으로 내림차순 정렬해주세요.
<br><br>
<h3>답안</h3>
```sql   
SELECT
    car_id, round(avg(datediff(end_date,start_date))+1,1) as average_duration
FROM
    CAR_RENTAL_COMPANY_RENTAL_HISTORY
GROUP by 
    car_id
HAVING(round(avg(datediff(end_date,start_date)+1),1))>=7
ORDER BY
    2 desc,1 desc
```

`datediff()` 함수는 mysql 기반의 DBMS에서 사용가능한 함수로 두 날짜 차이를 일단위로 리턴하는 함수다.  
사용법은 `datediff(기준일, 빼는일)`로 기준일에서 빼야 할 일을 빼주는 식으로 처리되어 반환된다.  
그러나 기준일 당일자는 처리되지 않기 때문에 `+1`을 해줬다.  
문제 조건중 <b>평균대여 일자가 7일 이상인 것</b>을 처리할 땐 WHERE 조건절이 아닌 `HAVING`절 에서 처리했다.  
정렬 부분은 이미 가공된 데이터를 통해 정렬해야 옳은 답이 나오기 때문에 출력되는 컬럼 순서로 `ORDER BY` 지정했다.