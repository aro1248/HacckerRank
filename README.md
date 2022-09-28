# HackerRank
Thanks for checking out my Hacker Rank Challenges. Below is a table that shows each challenge, a link to see the details of the challenge and a summary of the skills and functions used. 

| Challenge Name | Skills & Functions Used |
|-----|-------|
| [🌍 Average Population on Each Continent](#average-population-on-each-continent)| FlOOR, AVG, JOIN, GROUP BY |
|[Employee Information](#employee-information) | ORDER BY, Using multiple conditions in WHERE Clause| 
|[The PADS](#the-pads) | CONCAT, SUBSTR, GROUP BY, ORDER BY |

-------
### Average Population on Each Continent
The CITY and COUNTRY tables are described as follows:
  *Note: CITY.CountryCode and COUNTRY.Code are matching key columns.*
 
| CITY | COUNTRY|
|---| ----|
|![image](https://user-images.githubusercontent.com/113147940/192869144-e4a97af8-0ed3-40bc-b7e2-9f8066ad1a85.png) | ![image](https://user-images.githubusercontent.com/113147940/192869196-7d282c96-91d2-4c86-923e-117ed6f72f9c.png) |

#### Question 1: 
Given the CITY and COUNTRY tables, query the names of all the continents and their respective average city populations rounded down to the nearest integer.

```sql
SELECT COUNTRY.Continent,
       FLOOR(AVG(City.Population))
FROM CITY 
JOIN COUNTRY ON CITY.Countrycode=COUNTRY.code
Group BY COUNTRY.Continent; 
```
-------
### Employee Information
The Employee table containing employee data for a company is described as follows:

![image](https://user-images.githubusercontent.com/113147940/192875379-30d4e773-7125-41a4-b324-30dad6b111c4.png)


#### Question 1: 
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

```sql 
SELECT Name
FROM Employee
ORDER BY Name
```


#### Question 2: 
Write a query that prints a list of employee names for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

```sql 
SELECT Name
FROM Employee
WHERE Salary > 2000 AND
      Months < 10 
ORDER BY Employee_id ASC
```
------
### The PADS 
The OCCUPATIONS Table is described as Follows: 

 ![image](https://user-images.githubusercontent.com/113147940/192884230-3f545df9-1a95-44cc-b22d-2f89837f66d6.png)
- *Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.*

#### Generate the following two result sets: 
1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
``` There are a total of [occupation_count] [occupation]s. ```
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

```sql
SELECT CONCAT(Name, "(", SUBSTR(Occupation, 1, 1), ")")
FROM OCCUPATIONS
Order BY Name;

SELECT CONCAT("There are a total of", " ", COUNT(Occupation), " ", LOWER(Occupation), "s.") 
FROM Occupations
GROUP BY Occupation
ORDER BY Count(Occupation);
```
#### Result: 
```
Aamina(D) 
Ashley(P) 
Belvet(P) 
Britney(P) 
Christeen(S) 
Eve(A) 
Jane(S) 
Jennifer(A) 
Jenny(S) 
Julia(D) 
Ketty(A) 
Kristeen(S) 
Maria(P) 
Meera(P) 
Naomi(P) 
Priya(D) 
Priyanka(P) 
Samantha(A) 
There are a total of 3 doctors. 
There are a total of 4 actors. 
There are a total of 4 singers. 
There are a total of 7 professors.
```
