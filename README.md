# SQL-CodeHub

## *Total number of signup in Every week*
```sql
SELECT
  DATE_FORMAT(
    FROM_DAYS(
      TO_DAYS(created_date) - MOD(TO_DAYS(created_date) -2, 7)
    ),
    '%M %D'
  ) AS week_signup,
  COUNT(DISTINCT user_id) AS total_signup,
  COUNT(resume_upload_date) AS resume_uploaded
FROM
  turing_node.developer_detail
GROUP BY
  FROM_DAYS(
    TO_DAYS(created_date) - MOD(TO_DAYS(created_date) -2, 7)
  )
ORDER BY
  FROM_DAYS(
    TO_DAYS(created_date) - MOD(TO_DAYS(created_date) -2, 7)
  ) DESC;
 ```
> output:

 |id  | week_signup  | total_signup  | resume_uploaded |
 |----|:-----:|:-----:|:-----:|
 | 1	|June 13th |	16484	| 7423 |
|2	|June 6th	| 25701|	11356 |
|3	| May 30th	| 27620	| 12376 |
| 4	| May 23rd |	28769	| 13978|

### Notes:
`FROM_DAYS()` function: This function is used to return the date from a specified numeric date value. Here specified date value is divided by 365 and accordingly years, months, and days are returned. This function is used only with dates within the Gregorian calendar.

Syntax:
``` 
FROM_DAYS(number)
```
` TO_DAYS()` function: returns a number of days between a given date and year 0. This function is the opposite of the FROM_DAYS() function.

Syntax:
```
TO_DAYS(date)
```
`DATE_FORMAT()`: DATE_FORMAT() function in MySQL is used to format a specified date as given format value i.e., a date will be given and this function will format that date as specified format parameters.

Syntax:
```
DATE_FORMAT(date, format)
```
`MOD()`: SQL MOD() function is used to get the remainder from a division. The SQL DISTINCT command along with the SQL MOD() function is used to retrieve only unique records depending on the specified column or expression.

Syntax:
```
MOD( dividend, divider )
```
* -2 means week starts from **Monday** 
* 7 days interval
***
