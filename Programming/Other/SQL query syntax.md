## Case... Then...
##### Update multiple rows
``` PostgreSQL
UPDATE table_name 
SET col_2 = CASE 
	WHEN col_1 = 1 THEN 'value_1' 
	WHEN col_1 = 2 THEN 'value_2' 
	WHEN col_1 = 3 THEN 'value_3' 
	ELSE col_2 -- preserve the value if not in the array, can be any thing else
END 
WHERE col_1 IN (1, 2, 3);
```

##### Transform data
``` PostgreSQL
SELECT 
	column_name, 
	CASE column_name 
		WHEN value1 THEN result1 
		WHEN value2 THEN result2 
		ELSE default_result 
	END AS alias_name 
FROM table_name;
```

##### Group
``` PostgreSQL
SELECT 
	CASE 
		WHEN condition1 THEN group1 
		WHEN condition2 THEN group2 
		ELSE group3 
	END AS group_name, 
	COUNT(*) AS group_count 
FROM table_name 
GROUP BY 
	CASE 
		WHEN condition1 THEN group1 
		WHEN condition2 THEN group2 
		ELSE group3 
	END;
```

- It can be used in **Select**, **Order by**, **Where**, **Set**, **Having**, **Group by**

## Common table expression
``` PostgreSQL
WITH CTE_Name AS ( 
	SELECT column1, column2 
	FROM table_name 
	WHERE condition 
) 
SELECT column1, column2 FROM CTE_Name;
```


## Analytic functions:
``` PostgreSQL
SELECT 
	column1, 
	column2, 
	ROW_NUMBER() OVER (PARTITION BY column2 ORDER BY column1) AS row_num 
FROM table_name;
```

- Perform calculations across a set of table rows that are related to the current row. Unlike aggregate functions (which group rows), window functions operate on a row-by-row basis, but they allow you to calculate things like **row numbers**, **running totals**, **moving averages**, and **rankings**.

``` PostgreSQL
SELECT 
	employee_id, 
	salary, 
	RANK() OVER (ORDER BY salary DESC) AS rank 
FROM employees;
```

## Insert... On Conflict...
``` PostgreSQL
INSERT INTO table_name (column1, column2) 
VALUES (value1, value2) 
ON CONFLICT (column1) 
DO UPDATE SET column2 = excluded.column2;
```

- Mostly used when insert action make duplicate key conflict, then make an update instead.