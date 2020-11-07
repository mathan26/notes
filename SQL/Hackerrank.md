#HackerRank

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

`SELECT * FROM city WHERE countrycode='USA' and population > 100000;`

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
    
    `SELECT name FROM city WHERE countrycode='USA' and population > 120000;`
    
Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

`select DISTINCT (city) from station where (id%2)=0;`

Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

`select (count(city)- count(DISTINCT city)) from station;`

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

`SELECT CITY, LENGTH(CITY) FROM STATION
ORDER BY LENGTH(CITY), CITY
LIMIT 1;`

`SELECT CITY, LENGTH(CITY) FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY
LIMIT 1;`


Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

`SELECT DISTINCT CITY FROM STATION
WHERE CITY REGEXP '^[aeiou]';`

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

`SELECT DISTINCT city from STATION where city REGEXP '[aeiou]$';`

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

Input Format

`SELECT city FROM station WHERE city REGEXP '^[aeiou].*[aeiou]$';`

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

`SELECT DISTINCT city  FROM station WHERE city REGEXP '^[^aeiou]';`

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

`SELECT DISTINCT city FROM station where city REGEXP '[^aeiou]$'`
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

`SELECT DISTINCT city FROM station WHERE city REGEXP '^[^aeiou]|[^aeiou]$'`

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

Input Format

`SELECT DISTINCT city FROM station WHERE city REGEXP '^[^aeiou].*[^aeiou]$';`

Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

`SELECT name FROM students where marks > 75 ORDER By RIGHT(name,3),ID;`

Query the average population for all cities in CITY, rounded down to the nearest integer.

`SELECT  ROUND(AVG(population)) from city;`

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

`SELECT SUM(population) FROM CITY WHERE countrycode = 'JPN';`

Query the difference between the maximum and minimum populations in CITY.

 `SELECT MAX(population)  - MIN(population) FROM CITY;`
 
 Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeroes removed), and the actual average salary.
 
 Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.
 
` SELECT CEIL(AVG(salary) - AVG(REPLACE(salary,0,''))) FROM EMPLOYEES;`

We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

`SELECT salary * months as earnings,count(*) FROM employee GROUP BY earnings ORDER BY earnings DESC LIMIT 1 ;`

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of  decimal places.
The sum of all values in LONG_W rounded to a scale of  decimal places.

`SELECT ROUND(SUM(lat_n),2) as lat ,ROUND(SUM(long_w),2) as lon FROM station;`


Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than  and less than . Truncate your answer to  decimal places.

`SELECT TRUNCATE(SUM(lat_n),4) FROM station lat_n BETWEEN 38.7880 and 137.2345;`

Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than . Truncate your answer to  decimal places.

`SELECT TRUNCATE(MAX(lat_n),4) FROM station WHERE lat_n < 137.2345;`

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.

`SELECT ROUND(long_w,4) FROM station WHERE lat_n < 137.2345 ORDER BY lat_n DESC LIMIT 1 ;`


Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places.


`SELECT ROUND(MIN(lat_n),4) FROM station WHERE lat_n > 38.7780;`

Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than . Round your answer to  decimal places.

`SELECT ROUND(long_w,4) FROM station WHERE lat_n > 38.7780 ORDER BY lat_n LIMIT 1;`
