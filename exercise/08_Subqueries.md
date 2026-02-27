# Chapter 8. Subqueries - Practice Problems

Dear students! After completing Chapter 8, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

8장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 8, you should understand the following:

- Concept and necessity of subqueries (서브쿼리의 개념과 필요성)
- Scalar subquery in SELECT clause (SELECT 절의 서브쿼리)
- Inline view in FROM clause (FROM 절의 서브쿼리)
- Correlated subquery in WHERE clause (WHERE 절의 서브쿼리)
- IN and EXISTS operators (IN, EXISTS 연산자)
- Subquery vs JOIN comparison (서브쿼리 vs JOIN)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is the basic definition of subquery? (서브쿼리의 기본 정의는?)

- ① Query executed before main query (주요 쿼리를 실행하기 전에 먼저 실행하는 쿼리)
- ② Query contained within another query (다른 쿼리 내에 포함된 쿼리)
- ③ Query joining multiple tables (여러 테이블을 JOIN하는 쿼리)
- ④ Query using GROUP BY (GROUP BY를 사용하는 쿼리)

---

**Question 2** Where is scalar subquery used? (다음 중 스칼라 서브쿼리는 어디에 사용되는가?)

- ① In SELECT clause returning single value (SELECT 절에서 단일 값 반환)
- ② In FROM clause as table (FROM 절에서 테이블처럼 사용)
- ③ In WHERE clause for condition (WHERE 절에서 조건 비교)
- ④ In ORDER BY clause for sorting (ORDER BY 절에서 정렬)

---

**Question 3** Which result form is invalid for subquery? (서브쿼리가 반환할 수 있는 결과 형태로 옳지 않은 것은?)

- ① Single row, single column (scalar value) (단일 행, 단일 열)
- ② Single row, multiple columns (단일 행, 여러 열)
- ③ Multiple rows, single column (list) (여러 행, 단일 열)
- ④ Multiple rows, multiple columns (여러 행, 여러 열)

---

**Question 4** What is the purpose of IN operator? (IN 연산자의 용도는?)

- ① Search when subquery returns multiple rows (서브쿼리가 여러 행의 결과를 반환할 때 검색)
- ② Check NULL values (NULL 값 확인)
- ③ Range search (범위 검색)
- ④ Pattern matching (패턴 매칭)

---

**Question 5** What is the characteristic of EXISTS operator? (EXISTS 연산자의 특징은?)

- ① Check if subquery result exists (서브쿼리 결과가 존재하는지 확인)
- ② Check number of rows in subquery result (서브쿼리 결과의 행 개수 확인)
- ③ Compare subquery result values (서브쿼리 결과값 비교)
- ④ Sort subquery result (서브쿼리 결과 정렬)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which uses subquery correctly? (다음 중 서브쿼리가 올바르게 사용된 것은?)

```sql
① SELECT name, (SELECT MAX(salary) FROM employees) AS max_salary
   FROM employees;

② SELECT name, salary
   FROM employees
   WHERE salary > (SELECT AVG(salary) FROM employees);

③ SELECT e.name
   FROM employees e
   WHERE e.dept_id IN (SELECT dept_id FROM departments);
```

- ① Correct (SELECT clause scalar subquery) (올바름 - SELECT 절 스칼라 서브쿼리)
- ② Correct (WHERE clause subquery) (올바름 - WHERE 절 서브쿼리)
- ③ Correct (WHERE clause IN subquery) (올바름 - WHERE 절 IN 서브쿼리)
- ④ All ①②③ are correct (①②③ 모두 올바름)

---

**Question 7** Why use subquery in FROM clause (inline view)? (FROM 절의 서브쿼리를 사용하는 이유는?)

- ① Perform complex calculation first, then query from result (복잡한 계산을 먼저 수행 후 결과에서 다시 조회)
- ② Improve performance (성능 향상)
- ③ Simplify code (코드 간결화)
- ④ Need multi-table join (다중 테이블 조인 필요)

---

**Question 8** What is the characteristic of correlated subquery? (상관 서브쿼리의 특징은?)

- ① Reference outer query values (외부 쿼리의 값을 참조)
- ② Execute subquery for each row (각 행마다 서브쿼리 실행)
- ③ Can be converted to JOIN (JOIN으로 변환 가능)
- ④ All correct (모두 맞음)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** What is the performance difference between these two queries? (다음 두 쿼리의 성능 차이는?)

```
Query A: Using Subquery
SELECT name FROM employees
WHERE dept_id IN (SELECT dept_id FROM departments);

Query B: Using JOIN
SELECT DISTINCT e.name FROM employees e
JOIN departments d ON e.dept_id = d.dept_id;
```

- ① Query A always faster (쿼리 A가 항상 더 빠름)
- ② Query B always faster (쿼리 B가 항상 더 빠름)
- ③ Depends on situation (data volume, indexes, etc.) (상황에 따라 다름)
- ④ Performance identical (성능이 완전히 같음)

---

**Question 10** When to choose subquery over JOIN? (서브쿼리와 JOIN 중 언제 서브쿼리를 선택하는가?)

- ① When referencing same table multiple times (같은 테이블을 여러 번 참조할 때)
- ② When needing only simple values from other table (조인할 다른 테이블에서 단순 값만 필요할 때)
- ③ When using aggregate results as condition (집계 결과를 조건으로 사용할 때)
- ④ Cases ② and ③ (②③의 경우)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Define subquery and explain its necessity. (서브쿼리의 정의와 필요성을 설명하시오.)

---

**Question 12** Explain 3 places where subquery can be used and describe characteristics of each. (서브쿼리가 들어갈 수 있는 위치 3가지를 설명하고, 각각의 특징을 설명하시오.)

---

**Question 13** Explain difference between IN and EXISTS, and provide examples of when to use each. (IN과 EXISTS의 차이를 설명하고, 각각 언제 사용하는지 예시하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain correlated subquery concept, operation method, and difference from regular subquery. (상관 서브쿼리의 개념을 설명하고, 동작 방식과 일반 서브쿼리와의 차이를 설명하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain cases where subquery can be solved with JOIN and vice versa, and analyze advantages/disadvantages of each. (서브쿼리로 해결할 수 있는 문제를 JOIN으로 해결할 수 있는 경우와 그 반대의 경우를 설명하고, 각각의 장단점을 분석하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch8_subquery CHARACTER SET utf8mb4;
USE ch8_subquery;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    salary INT,
    dept_id INT
);

-- Create departments table (부서 테이블 생성)
CREATE TABLE departments (
    dept_id INT PRIMARY KEY AUTO_INCREMENT,
    dept_name VARCHAR(30)
);

-- Insert employee data (직원 데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 5000000, 1),
(2, 'Sarah Lee', 4000000, 1),
(3, 'David Park', 4500000, 2),
(4, 'Emily Choi', 3500000, 2),
(5, 'Michael Kang', 4200000, 3);

-- Insert department data (부서 데이터 입력)
INSERT INTO departments VALUES
(1, 'Sales'),
(2, 'Technology'),
(3, 'HR');

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
SELECT * FROM departments;
```

Submission: Screenshot showing employees and departments tables (제출: employees와 departments 테이블이 모두 보이는 스크린샷)

---

**Question 17** Perform the following on employees table and verify results. (employees 테이블에서 다음을 수행하고 결과를 확인하시오.)

```sql
-- 1. Employees with salary above average (전체 평균 급여보다 높은 직원)
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- 2. Average salary (평균 급여)
SELECT AVG(salary) AS avg_salary FROM employees;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Use subquery to perform the following queries. (서브쿼리를 사용하여 다음을 조회하시오.)

```sql
-- 1. IN subquery (IN을 사용한 서브쿼리)
SELECT name FROM employees
WHERE dept_id IN (SELECT dept_id FROM departments WHERE dept_name IN ('Sales', 'Technology'));

-- 2. FROM clause subquery (FROM 절 서브쿼리 - 인라인 뷰)
SELECT * FROM (
    SELECT name, salary, dept_id
    FROM employees
    WHERE salary >= 4000000
) AS high_earners;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

**Question 19** Use correlated subquery to perform the following queries. (상관 서브쿼리를 사용하여 다음을 조회하시오.)

```sql
-- 1. Employees above department average salary (각 부서의 평균 급여보다 높은 직원)
SELECT e.name, e.salary, e.dept_id
FROM employees e
WHERE e.salary > (
    SELECT AVG(salary) FROM employees
    WHERE dept_id = e.dept_id
);

-- 2. EXISTS correlated subquery (EXISTS를 사용한 상관 서브쿼리)
SELECT d.dept_name
FROM departments d
WHERE EXISTS (
    SELECT 1 FROM employees e
    WHERE e.dept_id = d.dept_id
);
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex subqueries. (다음의 복잡한 서브쿼리를 작성하고 실행하시오.)

```
Requirements:

1. Calculate department average salary, then compare each employee
   Find employees and their department average salary

2. Multiple nested subqueries
   Apply multiple levels of conditions with nested subqueries

3. Subquery vs JOIN comparison
   - Write same logic using subquery and JOIN
   - Compare query performance

4. 2 or more creative subquery queries:
   - Aggregate function + subquery
   - Multiple level nested subquery
   - IN and EXISTS combination

Submission:
   - SQL code for each query
   - Execution result screenshot for each query

요구사항:

1. 각 부서의 평균 급여를 구한 후, 그 결과를 이용해 
   각 직원과 부서 평균 급여 비교

2. 여러 개의 서브쿼리를 중첩하여
   특정 조건 만족하는 데이터 조회

3. 서브쿼리 vs JOIN 비교
   - 같은 결과를 얻기 위해 서브쿼리와 JOIN으로 각각 작성
   - 쿼리 성능 비교

4. 자유로운 서브쿼리 쿼리 2개 이상:
   - 집계함수 + 서브쿼리
   - 여러 층 중첩 서브쿼리
   - IN, EXISTS 조합

제출:
   - 각 쿼리의 SQL 코드
   - 각 쿼리의 실행 결과 스크린샷
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                             |
| :------: | :----: | :-------------------------------------------------------------------------------------- |
|    1    |   ②   | Subquery is query contained in another query (다른 쿼리 내에 포함된 쿼리)               |
|    2    |   ①   | Scalar subquery used in SELECT clause returns single value (SELECT 절에서 단일 값 반환) |
|    3    |   ④   | Multiple rows and columns not possible (행이나 열 둘 중 하나는 단수)                    |
|    4    |   ①   | IN used for multiple row results (여러 행 결과 검색)                                    |
|    5    |   ①   | EXISTS checks if subquery result exists (서브쿼리 결과 존재 여부 확인)                  |
|    6    |   ④   | All ①②③ use subquery correctly (①②③ 모두 올바른 서브쿼리 사용)                    |
|    7    |   ①   | FROM subquery performs complex calculation then requery (복잡한 계산 후 재조회)         |
|    8    |   ④   | All correct (correlated subquery characteristics) (모두 맞음)                           |
|    9    |   ③   | Performance depends on situation (상황에 따라 성능이 다름)                              |
|    10    |   ④   | Choose subquery in cases ② and ③ (②③ 경우 서브쿼리 선택)                            |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Subquery Definition and Necessity

**Model Answer (모범 답안):**

```
Definition:
- Query contained within another query
- Also called sub-query or inner query
- Works with main query

Necessity:
1. Simplify complex conditions
2. Use aggregate results as condition
3. Reuse intermediate results
4. Facilitate complex data retrieval

Example: "Query employees with salary above average"
- First calculate average (subquery)
- Then compare with result (main query)
```

---

### Question 12: Subquery Locations

**Model Answer (모범 답안):**

```
1. SELECT clause - Scalar Subquery
   - Returns single row, single column
   - Executes subquery for each row
   SELECT name, (SELECT MAX(salary) ...) FROM ...

2. FROM clause - Inline View
   - Use subquery result as table
   - Perform complex calculation then requery
   FROM (SELECT ... WHERE ...) AS subquery

3. WHERE clause - Condition Subquery
   - Use in condition comparison
   - Use with IN, EXISTS, etc.
   WHERE salary > (SELECT AVG(salary) ...)
```

---

### Question 13: IN vs EXISTS

**Model Answer (모범 답안):**

```
IN:
- Subquery returns multiple values
- Match one of returned values
- Example: WHERE dept_id IN (1, 2, 3)

EXISTS:
- Check only if subquery result exists
- Return TRUE/FALSE
- Ignore NULL

When to use:

IN usage:
SELECT name FROM employees
WHERE dept_id IN (SELECT dept_id FROM departments);

EXISTS usage:
SELECT d.name FROM departments d
WHERE EXISTS (SELECT 1 FROM employees e WHERE e.dept_id = d.id);

Performance: EXISTS can be faster (checks existence only)
```

---

### Question 14: Correlated Subquery

**Model Answer (모범 답안):**

```
Definition:
- Subquery references values from outer query
- Executes subquery for each row

Operation:
1. Select row from outer query
2. Pass row values to subquery
3. Execute subquery
4. Return result
5. Repeat for next row

Example:
SELECT e.name FROM employees e
WHERE e.salary > (
    SELECT AVG(salary) FROM employees
    WHERE dept_id = e.dept_id  -- Outer query reference
);

Difference from regular subquery:
- Regular: Execute subquery once
- Correlated: Execute per row (performance impact)
```

---

### Question 15: Subquery vs JOIN

**Model Answer (모범 답안):**

```
Subquery only:
- Use aggregate function result as condition
- Example: WHERE salary > (SELECT AVG(...))
- Some correlated subqueries

JOIN only:
- Self Join (same table with itself)
- Example: Employee and manager
- Combine multiple tables

Both possible:
SELECT e.name FROM employees e
WHERE dept_id IN (1, 2, 3);  -- Subquery

SELECT DISTINCT e.name FROM employees e
WHERE e.dept_id IN (
    SELECT dept_id FROM departments...
);  -- Can use JOIN

Advantages/Disadvantages:

Subquery:
- Pro: More readable in some cases
- Con: May have performance issues (executes per row)

JOIN:
- Pro: Generally better performance
- Con: Can be complex
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Table Creation

**Completion Criteria (완료 기준):**

✅ ch8_subquery database created
✅ employees 5 employees inserted
✅ departments 3 departments inserted

---

### Question 17: SELECT Clause Subquery

**Expected Result (예상 결과):**

```
1. Average salary: 4,240,000
2. Employees above average:
   - Alex Kim 5,000,000
   - David Park 4,500,000
```

---

### Question 18: IN and FROM Subquery

**Completion Criteria (완료 기준):**

✅ IN subquery: Query Sales and Technology employees
✅ FROM subquery: Requery high-earning employees

---

### Question 19: Correlated Subquery

**Model Answer (모범 답안):**

```sql
-- 1. Above department average
Result:
Alex Kim 5000000 1 (Sales avg 4,500,000 - above)
David Park 4500000 2 (Technology avg 4,000,000 - above)

-- 2. EXISTS with departments
Result:
Sales
Technology
HR
```

---

### Question 20: Complex Subqueries

**Model Answer (모범 답안):**

```sql
-- 1. Department average comparison
SELECT e.name, e.salary,
       (SELECT AVG(salary) FROM employees 
        WHERE dept_id = e.dept_id) AS dept_avg
FROM employees e;

-- 2. Nested subquery
SELECT name FROM employees
WHERE salary > (
    SELECT AVG(salary) FROM employees
    WHERE dept_id IN (
        SELECT dept_id FROM departments
        WHERE dept_name IN ('Sales', 'Technology')
    )
);

-- 3. Subquery approach
SELECT DISTINCT e.name FROM employees e
WHERE e.dept_id IN (
    SELECT dept_id FROM departments
    WHERE dept_name IN ('Sales', 'Technology')
);

-- 3. JOIN approach
SELECT DISTINCT e.name FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
WHERE d.dept_name IN ('Sales', 'Technology');

-- 4. Aggregate + Subquery
SELECT dept_id, COUNT(*) AS cnt
FROM employees
WHERE salary > (
    SELECT AVG(salary) FROM employees
)
GROUP BY dept_id;

-- 5. Multiple conditions subquery
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees)
AND dept_id IN (
    SELECT dept_id FROM departments
    WHERE dept_name NOT IN ('HR')
);
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
