# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
SELECT * from matches WHERE season = 2017;


```

2) Find all the matches featuring Barcelona.

```sql
SELECT * from matches WHERE hometeam = 'Barcelona' OR awayteam = 'Barcelona';


```

3) What are the names of the Scottish divisions included?

```sql

SELECT name FROM divisions WHERE Country = 'Scotland';

```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables

```sql
SELECT code, name FROM divisions WHERE Name = 'Bundesliga';
D1

SELECT COUNT(*) FROM matches WHERE division_code = 'D1' AND (awayteam = 'Freiburg' OR hometeam = 'Freiburg');
374
```

5) Find the teams which include the word "City" in their name. (4 teams back)

```sql
SELECT hometeam FROM matches WHERE LOWER(hometeam) LIKE '%city%' GROUP BY hometeam;

Bath City, Man City, Edinburgh City, Bristol City
```

6) How many different teams have played in matches recorded in a French division?

```sql
SELECT * FROM divisions WHERE country ='France';
F1, F2
SELECT COUNT(Distinct hometeam) FROM matches WHERE division_code = 'F1' OR division_code = 'F2'

```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
SELECT COUNT(*) FROM matches WHERE (hometeam = 'Huddersfield' AND awayteam = 'Swansea') OR (awayteam = 'Huddersfield' AND hometeam = 'Swansea') ;
12


```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
SELECT * FROM divisions WHERE name='Eredivisie';
N1
SELECT COUNT(*) FROM matches WHERE division_code = 'N1' AND ftr = 'D' AND (season >= 2010 AND season<= 2015);


```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. When two matches have the same total the match with more home goals should come first.

```sql
SELECT *, (fthg + ftag) AS SUM FROM matches WHERE division_code = 'E0' ORDER BY sum DESC, fthg DESC;


```

10) In which division and which season were the most goals scored?

```sql
SELECT division_code, season, (fthg + ftag) AS GoalSum FROM matches ORDER BY goalSum DESC LIMIT 1;


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)