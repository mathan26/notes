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

Consider  and  to be two points on a 2D plane.

 happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
 happens to equal the minimum value in Western Longitude (LONG_W in STATION).
 happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
 happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points  and  and round it to a scale of  decimal places.

`SELECT
    ROUND(ABS(MAX(LAT_N)  - MIN(LAT_N))
        + ABS(MAX(LONG_W) - MIN(LONG_W)), 4)
FROM 
    STATION;`
    
    
Consider  and  to be two points on a 2D plane where  are the respective minimum and maximum values of Northern Latitude (LAT_N) and  are the respective minimum and maximum values of Western Longitude (LONG_W) in

`SELECT
    ROUND(SQRT(
        POWER(MAX(LAT_N)  - MIN(LAT_N),  2)
      + POWER(MAX(LONG_W) - MIN(LONG_W), 2)
    ), 4)
FROM 
    STATION;`
    
    
## Advanced Select

Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy:

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

Note:

The tables may contain duplicate records.
The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

`SELECT c.company_code, c.founder, 
       COUNT(DISTINCT l.lead_manager_code), COUNT(DISTINCT s.senior_manager_code),
       COUNT(DISTINCT m.manager_code), COUNT(DISTINCT e.employee_code)
FROM Company c JOIN Lead_Manager l ON c.company_code = l.company_code JOIN
     Senior_Manager s ON l.lead_manager_code = s.lead_manager_code JOIN
     Manager m ON s.senior_manager_code = m.senior_manager_code JOIN
     Employee e ON m.manager_code = e.manager_code   
GROUP BY c.company_code, c.founder ORDER BY c.company_code;`

`SELECT COMPANY_CODE, FOUNDER,
(SELECT COUNT(DISTINCT LEAD_MANAGER_CODE) FROM LEAD_MANAGER WHERE COMPANY_CODE = C.COMPANY_CODE),
(SELECT COUNT(DISTINCT SENIOR_MANAGER_CODE) FROM SENIOR_MANAGER WHERE COMPANY_CODE = C.COMPANY_CODE),
(SELECT COUNT(DISTINCT MANAGER_CODE) FROM MANAGER WHERE COMPANY_CODE = C.COMPANY_CODE),
(SELECT COUNT(DISTINCT EMPLOYEE_CODE) FROM EMPLOYEE WHERE COMPANY_CODE = C.COMPANY_CODE)
FROM COMPANY C
ORDER BY COMPANY_CODE;`


Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

`SELECT CASE 
WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle' 
WHEN A = B AND B = C THEN 'Equilateral' 
WHEN A = B OR B = C OR A = C THEN 'Isosceles' 
ELSE 'Scalene' 
END 
FROM TRIANGLES;`
    
Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.

`SELECT CONCAT(NAME,'(',SUBSTR(OCCUPATION,1,1),')') AS N
FROM OCCUPATIONS
ORDER BY N;
SELECT CONCAT('There are a total of ',COUNT(OCCUPATION),' ',LOWER(OCCUPATION),'s.')
FROM OCCUPATIONS
GROUP BY OCCUPATION
ORDER BY COUNT(OCCUPATION), OCCUPATION;
`