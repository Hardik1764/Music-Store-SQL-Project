# Music_Store_SQL_Project_MYSQL 
in Q 5  and if you are using this query {SELECT c.customer_id, c.first_name, c.last_name, SUM(i.total) FROM customer AS c
JOIN invoice AS i
ON c.customer_id = i.customer_id
GROUP BY c.customer_id
ORDER BY SUM(i.total) DESC
LIMIT 1;} you are facing error cause due to group by function The error message you received, "Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column...", is indicating that there's a problem with how MySQL is processing your query.

In simple terms, MySQL has a mode called only_full_group_by, which requires that every column in the SELECT list that is not an aggregate function (like SUM(), COUNT(), etc.) must also be included in the GROUP BY clause. This mode is designed to ensure that the query results are deterministic and predictable.

To fix this error, you have two options:

Include c.first_name and c.last_name in the GROUP BY clause along with c.customer_id. This way, MySQL knows how to group the data properly.
Use aggregate functions (like MAX(), MIN(), etc.) for c.first_name and c.last_name if you intend to include them in the SELECT list without grouping by them.
Ans (SELECT c.customer_id, c.first_name, c.last_name, SUM(i.total) FROM customer AS c
JOIN invoice AS i
ON c.customer_id = i.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name
ORDER BY SUM(i.total) DESC
LIMIT 1;) i use this query instead of this

add this c.first_name, c.last_name in GROUP BY Clause 

