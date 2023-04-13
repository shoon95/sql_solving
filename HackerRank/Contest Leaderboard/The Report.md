# The Report

### [🏸문제](https://www.hackerrank.com/challenges/the-report/problem) 

<hr>



### 💊풀이

> SELECT 문에 조건절을 사용하자

1. select 문에 조건절 사용
1. 점수에 따른 grade를 문제에 표기된 대로 주기 위해 나머지 연산(MOD)과 몫(DIV)을 찾아내는 규칙을 활용

<hr>

### 📌코드

```mysql
SELECT IF( Marks >= 70, name, NULL) AS NAME, IF (MARKS=100, 10, (MARKS DIV 10) + 1) AS Grade, Marks
FROM Students
ORDER BY Grade DESC, NAME, Marks;
```

<hr>





### 🛀결과

![image-20230414014035641](C:\Users\sjhty\AppData\Roaming\Typora\typora-user-images\image-20230414014035641.png)

나머지와 몫을 활용하여 위 문제를 해결하였다. 다른 풀이를 살펴보니 FROM 절에 기존 테이블 두 개를 합쳐서 새로운 테이블을 만들어 사용하는 풀이가 좋아 보였다. 이때 조건절 (WHERE)에 between 문법을 사용하여 min값과 max 값 사이에 현재 점수가 존재하는지를 확인하여 grade를 받아올 수 있다는 사실을 알게 되었다.
