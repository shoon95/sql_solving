# Contest Leaderboard

### [🏸문제](https://www.hackerrank.com/challenges/contest-leaderboard/problem) 

<hr>



### 💊풀이

> JOIN을 활용하며 여러개의 column을 동시에 GROUP BY

1. 주어진 두 테이블을 JOIN
1. 합쳐진 테이블을 여러가지 컬럼을 동시에 활용하여 GROUP BY

<hr>

### 📌코드

```mysql
SELECT A.hacker_id, A.name, SUM(A.score)
FROM 
(SELECT Hackers.hacker_id AS hacker_id, Submissions.challenge_id AS challenge_id, Hackers.name AS name, MAX(score) AS score
FROM Hackers
INNER JOIN Submissions
ON Hackers.hacker_id = Submissions.hacker_id
GROUP BY Hackers.hacker_id, Hackers.name, Submissions.challenge_id) AS A
GROUP BY A.hacker_id, A.name
HAVING SUM(A.score) > 0
ORDER BY SUM(A.score) DESC, A.hacker_id;
```

<hr>





### 🛀결과

![image-20230414014720084](C:\Users\sjhty\AppData\Roaming\Typora\typora-user-images\image-20230414014720084.png)

처음에 테이블을 합치고 그룹을 묶어줄 때 여러컬럼을 동시에 group by 해줘야된다는 것을 몰랐다. 때문에 하나 컬럼으로만 데이터를 묶고 총합 또는 평균을 구하려고 하니 에러가 났었다. 이때는 똑같이 묶일 수 있는 여러 컬럼을 동시에 GROUP BY를 사용하여 묶어주어야 한다.
