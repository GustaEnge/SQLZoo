**JOIN and UEFA EURO 2012**

1)The first example shows the goal scored by a player with the last name 'Bender'. The * says to list all the columns in the table - a shorter way of saying matchid, teamid, player, gtime.
Modify it to show the matchid and player name for all goals scored by Germany. To identify German players, check for: teamid = 'GER'
```
SELECT matchid,player FROM goal WHERE teamid = 'GER';
```
2) From the previous query you can see that Lars Bender's scored a goal in game 1012. Now we want to know what teams were playing in that match.

Notice in the that the column matchid in the goal table corresponds to the id column in the game table. We can look up information about game 1012 by finding that row in the game table.

Show id, stadium, team1, team2 for just game 1012
```
SELECT id,stadium,team1,team2
  FROM game WHERE id = 1012;
```
3) 
```
SELECT g.player,g.teamid,stadium,mdate
  FROM  goal g
INNER JOIN game ga 
ON g.matchid = ga.id
WHERE g.teamid = 'GER';
```
4) 
```
SELECT ga.team1,ga.team2,go.player
FROM game ga
INNER JOIN goal go
ON ga.id = go.matchid
WHERE player LIKE 'Mario%';
```
5) 
```
SELECT go.player, go.teamid, e.coach, go.gtime
  FROM goal go 
  INNER JOIN eteam e
  ON go.teamid = e.id
  WHERE gtime<=10;
```
6) 
```
SELECT ga.mdate,e.teamname
FROM game ga
INNER JOIN eteam e
ON ga.team1 = e.id
WHERE e.coach = 'Fernando Santos';
```
7) 
```
SELECT go.player
FROM goal go
INNER JOIN game ga
ON go.matchid = ga.id
WHERE ga.stadium = 'National Stadium, Warsaw';
```
8) 
```
SELECT DISTINCT(go.player)
FROM goal go
INNER JOIN game ga
ON ga.id = go.matchid
WHERE go.teamid <> 'GER' AND (ga.team1 ='GER' XOR ga.team2 ='GER');
```
