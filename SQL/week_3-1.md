문제1번) 매출을 가장 많이 올린 dvd 고객 이름은? (subquery 활용)

```sql
select first_name, last_name 
from customer c
where customer_id in (
select customer_id 
from payment p 
group by customer_id
order by sum(amount) desc
limit 1)
```
```sql
select  first_name , last_name
from customer c
where  customer_id in (
select customer_id
from payment p
group by customer_id
order by sum(amount) desc
limit 1
)
```
</br>
 

문제2번) 대여가 한번도이라도 된 영화 카테 고리 이름을 알려주세요. (쿼리는, Exists조건을 이용하여 풀어봅시다)

```sql
select c."name" 
from category c 
where exists 
(select r.rental_date , i.film_id , fc.category_id 
from rental r 
join inventory i on r.inventory_id = i.inventory_id 
join film_category fc on i.film_id = fc.film_id )
```

```sql
select c.name
from category as c
where exists (
	select fc.category_id
	from rental as r
	join inventory as i on r.inventory_id = i.inventory_id
	join film_category as fc on i.film_id = fc.film_id
	where fc.category_id = c.category_id
)
```
</br>
 
문제3번) 대여가 한번도이라도 된 영화 카테 고리 이름을 알려주세요. (쿼리는, Any 조건을 이용하여 풀어봅시다)

```sql
select distinct "name"
from category c
join film_category fc on c.category_id = fc.category_id
join inventory i on fc.film_id = i.film_id 
where i.inventory_id = any(
select inventory_id 
from rental r 
where rental_date is not null)
```
```sql
select c.name
from category as c
where category_id = any (
select fc.category_id
from rental as r
join inventory as i on r.inventory_id = i.inventory_id
join film_category as fc on i.film_id = fc.film_id)

)
```
</br>
 
문제4번) 대여가 가장 많이 진행된 카테고리는 무엇인가요? (Any, All 조건 중 하나를 사용하여 풀어봅시다)

```sql
```
</br>
 
문제5번) dvd 대여를 제일 많이한 고객 이름은? (subquery 활용)

```sql
```
</br>
 
문제6번) 영화 카테고리값이 존재하지 않는 영화가 있나요?

```sql
```
</br>
 
