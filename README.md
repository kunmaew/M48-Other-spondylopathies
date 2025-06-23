# M48-Other-spondylopathies
โรคกระดูกสันหลังอื่น ๆ


```
select 
t1.fiscalyear, 
t1.sex,	
t1.age,
t1.diagcode,
count(distinct t1.cid) as total
from 
(
SELECT 
fiscalyear,	hospcode,	pid,	cid,	sex,	age,	MIN(date_serv) as date_serv, diagcode
FROM ak_raw_m48_opd
GROUP BY fiscalyear,	hospcode,	pid,	cid,	sex,	age, diagcode
) t1
group by 
t1.fiscalyear, 
t1.sex,	
t1.age,
t1.diagcode
order by 
t1.fiscalyear desc , total desc
```
