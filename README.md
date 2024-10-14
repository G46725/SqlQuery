# SqlQuery

input table:-
name	city
Sachin	Mumbai
Virat	Delhi
Rahul	Bangalore
Rohit	Mumbai
Mayank	Bangalore

output table:-
Bangalore	Mumbai	Delhi
Mayank	Rohit	Virat
Rahul	Sachin	NULL
.................................................................................
select max(case when city='Bangalore' then name end) 'Bangalore'
,max(case when city = 'Mumbai' then name end) 'Mumbai'
,max(case when city = 'Delhi' then name end) 'Delhi'
from
(select *
,row_number() over(partition by city order by name) rn 
from players_location)t
group by rn
order by rn
...................................................................................


