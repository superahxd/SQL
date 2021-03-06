문제1번)  각 제품 가격을 5 % 줄이려면 어떻게 해야 할까요?

```sql
select productname, retailprice , retailprice*0.95 as discount 
from products p 

```

```sql

```
</br>
문제2번)  고객이 주문한 목록을 주문 일자로 내림차순 정렬해서 보여주세요.

```sql
select *
from orders
order by orderdate desc
```
</br>
문제3번)  employees 테이블을 이용하여, 705 아이디를 가진 직원의 , 이름, 성과  해당 직원의  태어난 해를 확인해주세요.

```sql
select empfirstname , emplastname , extract(year from empbirthdate) as birth_year
from employees e 
where employeeid = 705
```
#### EXTRACT(A FROM B)

A (Field 값) : year, month, day 와 같은 추출할 날짜/시간

|A (Field 값)|의미|
|----------:|:----------|
CENTURY |	세기(21세기, 20세기)
DAY	|1~31에 해당하는 해당 월의 일
DOW	|일요일(0) ~ 토요일(6)까지 반환하는 값
DOY	|1~366 까지 해당하는 연중일수
EPOCH	|1970년 1월 1일 00:00:00 UTC 부터 현재까지의 초 (unixtime)
HOUR|	0 ~ 23 에 해당하는 시간정보
MILLISECONDS	|1/1000에 해당하는 밀리초
MINUTE|	0 ~ 59에 해당하는 분 정보
MONTH|	1 ~ 12에 해당하는 월 정보
QUARTER	|1(1-3월), 2(4-6월), 3(7-9월), 4(10-12월) 분기로 나뉘어지는 정보
SECOND|	0 ~ 59에 해당하는 초 정보
WEEK	|주 정보 (1월 1일 : 1, 12월 31일: 52-53)
YEAR	|연도 정보.

</br>
문제4번)  customers 테이블을 이용하여,  고객의 이름과 성을 하나의 컬럼으로 전체 이름을 보여주세요 (이름, 성 의 형태로  full_name 이라는 이름으로 보여주세요)

```sql
select custfirstname ||' '||custlastname as full_name
from customers c 
```

</br>
문제5번) orders 테이블을 활용하여, 고객번호가 1001 에 해당하는 사람이 employeeid 가 707인 직원으로부터  산 주문의 id 와 주문 날짜를 알려주세요.
* 주문일자 빠른순으로 정렬하여, 보여주세요.

```sql
select ordernumber ,orderdate
from orders o
where customerid = 1001
and employeeid = 707
order by orderdate asc
```
</br>
문제6번)  vendors 테이블을 이용하여, 벤더가 위치한 state 주가 어떻게 되는지, 확인해보세요.  중복된 주가 있다면, 중복제거 후에 알려주세요.

```sql
select distinct vendstate
from vendors v 
```
</br>
문제7번) 주문일자가  2017-09-02~ 09-03일 사이에 해당하는 주문 번호를 알려주세요.

```sql
select ordernumber 
from orders o 
where orderdate between '2017-09-02' and '2017-09-03'
```

```sql

```
</br>
문제8번) products 테이블을 활용하여, productdescription에 상품 상세 설명 값이 없는  상품 데이터를 모두 알려주세요.

```sql
select *
from products
where productdescription is null
```

```sql

```
</br>
문제9 번) vendors 테이블을 이용하여, vendor의 State 지역이 NY 또는 WA 인 업체의 이름을 알려주세요.

```sql
select vendname 
from vendors v
where vendstate in ('NY', 'WA')
```
</br>
문제10번)  customers 테이블을 이용하여, 고객의 id 별로,  custstate 지역 중 WA 지역에 사는 사람과  WA 가 아닌 지역에 사는 사람을 구분해서  보여주세요.

- customerid 와, newstate_flag 컬럼으로 구성해주세요 .
- newstate_flag 컬럼은 WA 와 OTHERS 로 노출해주시면 됩니다.

```sql
select customerid , 
case when custstate = 'WA' then 'WA' else 'OTHERS' end as newstate_flag
from customers c 
```

```sql

```
</br>
