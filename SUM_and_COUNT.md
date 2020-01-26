**SUM and COUNT**

1) Show the total population of the world.
```
SELECT SUM(population)
FROM world;
```
2) List all the continents - just once each.
```
Select DISTINCT(Continent) FROM world;
```
3) Give the total GDP of Africa
```
Select SUM(gdp) FROM world WHERE Continent='Africa';
```
4) How many countries have an area of at least 1000000
```
Select COUNT(name) FROM world WHERE area >= 1000000;
```
5) What is the total population of ('Estonia', 'Latvia', 'Lithuania')
```
Select SUM(population) FROM world WHERE name in ('Estonia','Latvia','Lithuania');
```
6) For each continent show the continent and number of countries.
```
Select continent,COUNT(name) FROM world GROUP BY (continent);
```
7) For each continent show the continent and number of countries with populations of at least 10 million.
```
Select continent,COUNT(name) FROM world WHERE population >= 10000000 GROUP BY (continent);
```
8) List the continents that have a total population of at least 100 million.
```
Select continent FROM world GROUP BY continent HAVING SUM(population) >= 100000000;
```
