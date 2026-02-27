# Chapter 7. Aggregate Functions and Grouping - Practice Problems

Dear students! After completing Chapter 7, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

7장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 7, you should understand the following:

- COUNT, SUM, AVG, MAX, MIN aggregate functions (집계함수)
- Data grouping using GROUP BY (GROUP BY를 사용한 데이터 그룹화)
- Group filtering with HAVING clause (HAVING 절로 그룹 필터링)
- Impact of NULL values on aggregate functions (NULL 값이 집계함수에 미치는 영향)
- Complex grouping by multiple columns (복합 그룹화)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is the biggest difference between COUNT(*) and COUNT(column)? (COUNT(*)와 COUNT(column)의 가장 큰 차이는?)

- ① COUNT(*) is faster (COUNT(*)는 더 빠름)
- ② COUNT(*) includes NULL, COUNT(column) excludes NULL (COUNT(*)는 NULL을 포함, COUNT(column)은 NULL 제외)
- ③ COUNT(column) removes duplicates, COUNT(*) doesn't (COUNT(column)은 중복 제거)
- ④ They function identically (기능이 완전히 같음)

---

**Question 2** What is the primary purpose of GROUP BY? (GROUP BY의 기본 목적은?)

- ① Sort data (데이터를 정렬함)
- ② Divide rows into groups and apply aggregate functions (행들을 그룹으로 나누어 각 그룹에 집계함수 적용)
- ③ Filter data (데이터를 필터링함)
- ④ Redefine table (테이블을 다시 정의함)

---

**Question 3** How are NULL values handled in aggregate functions? (다음 중 NULL 값이 집계함수에 어떻게 처리되는가?)

- ① NULL is calculated as 0 (NULL은 0으로 계산됨)
- ② NULL is excluded and ignored (NULL은 무시되고 제외됨)
- ③ Error occurs due to NULL (NULL로 인해 오류 발생)
- ④ Depends on function (함수에 따라 다름)

---

**Question 4** What is the role of HAVING clause? (HAVING 절의 역할은?)

- ① Filter individual rows (same as WHERE) (개별 행을 필터링 - WHERE와 같음)
- ② Filter groups created by GROUP BY result (GROUP BY 결과로 생성된 그룹을 필터링)
- ③ Sort data (데이터를 정렬)
- ④ Select columns (열을 선택)

---

**Question 5** What does COUNT(DISTINCT column) mean? (COUNT(DISTINCT column)의 의미는?)

- ① Count of all rows including duplicates (중복을 포함한 모든 행 개수)
- ② Count of unique values with duplicates removed (중복을 제거한 유일한 값의 개수)
- ③ Count of rows including NULL (NULL을 포함한 행 개수)
- ④ Count only specific values (특정 값만 개수를 셈)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which query correctly uses GROUP BY and aggregate functions? (GROUP BY와 집계함수를 올바르게 사용하는 쿼리는?)

```sql
① SELECT dept_id, salary, COUNT(*)
   FROM employees
   GROUP BY dept_id;

② SELECT dept_id, COUNT(*), AVG(salary)
   FROM employees
   GROUP BY dept_id;

③ SELECT dept_id, COUNT(*), salary
   FROM employees
   GROUP BY dept_id;
```

- ① Correct (올바름)
- ② Correct (올바름)
- ③ Error (salary not grouped) (오류 - salary가 그룹화되지 않음)
- ④ Both ① and ② are correct (①②가 올바름)

---

**Question 7** What is the difference between HAVING and WHERE clauses? (HAVING 절과 WHERE 절의 차이는?)

```sql
SELECT dept_id, AVG(salary)
FROM employees
WHERE salary > 5000000        -- ①
GROUP BY dept_id
HAVING AVG(salary) > 5500000; -- ②
```

- ① WHERE filters individual rows before grouping, HAVING filters groups after grouping (WHERE는 그룹화 전 개별 행 필터링, HAVING은 그룹화 후 그룹 필터링)
- ② WHERE and HAVING have same function (WHERE와 HAVING은 같은 기능)
- ③ Only HAVING can use aggregate functions (HAVING만 집계함수 사용 가능)
- ④ Both ① and ③ are correct (①과 ③ 모두 맞음)

---

**Question 8** To find departments with average salary >= 4,000,000, which approach is correct? (부서별 평균 급여를 구하되, 평균이 4000000원 이상인 부서만 보려면?)

- ① WHERE AVG(salary) >= 4000000
- ② HAVING AVG(salary) >= 4000000
- ③ GROUP BY HAVING AVG(salary) >= 4000000
- ④ ORDER BY AVG(salary) >= 4000000

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Why might these two queries return different results? (다음 쿼리의 결과가 다를 이유는?)

```
Query A:
SELECT COUNT(*) FROM employees;

Query B:
SELECT COUNT(manager_id) FROM employees;
```

- ① Query A is slower (쿼리 A는 더 느림)
- ② Query B excludes rows where manager_id is NULL (결과가 작을 수 있음) (쿼리 B는 manager_id가 NULL인 행 제외)
- ③ Both return same result (둘 다 같은 결과)
- ④ Error in Query B (쿼리 B에 오류)

---

**Question 10** What is the result when using aggregate functions without GROUP BY? (GROUP BY 없이 집계함수만 사용할 때의 결과는?)

```sql
SELECT COUNT(*), SUM(salary), AVG(salary), MAX(salary)
FROM employees;
```

- ① Error occurs (오류 발생)
- ② Returns overall statistics for all employees (1 row) (전체 직원의 통계 - 1행 반환)
- ③ Repeats for each employee (행 수 만큼) (각 직원별로 반복)
- ④ Empty result (빈 결과)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain differences between COUNT(*), SUM(), AVG(), MAX(), MIN(). (COUNT(*), SUM(), AVG(), MAX(), MIN()의 차이를 설명하시오.)

---

**Question 12** Explain situations requiring GROUP BY and write a query for counting employees per department. (GROUP BY를 사용해야 하는 상황을 설명하고, 부서별 직원 수를 구하는 쿼리를 작성하시오.)

---

**Question 13** Explain impact of NULL values on aggregate functions and provide examples where COUNT(*) and COUNT(column) return different results. (NULL 값이 집계함수에 미치는 영향을 설명하고, COUNT(*)와 COUNT(column)의 결과가 다를 수 있는 경우를 예시하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain necessity of HAVING clause and clarify difference from WHERE. (HAVING 절의 필요성을 설명하고, WHERE와 HAVING의 차이를 명확히 하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain precautions when grouping by multiple columns (GROUP BY col1, col2) and performance optimization methods. (여러 열로 그룹화할 때 주의할 사항과 성능 최적화 방법을 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch7_aggregation CHARACTER SET utf8mb4;
USE ch7_aggregation;

-- Create sales table (판매 테이블 생성)
CREATE TABLE sales (
    sale_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10, 2),
    sale_date DATE,
    employee_id INT
);

-- Create products table (상품 테이블 생성)
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50),
    category VARCHAR(30),
    price DECIMAL(10, 2)
);

-- Insert sales data (판매 데이터 입력)
INSERT INTO sales VALUES
(1, 1, 10, 50000, '2024-01-15', 1),
(2, 2, 5, 100000, '2024-01-15', 1),
(3, 1, 8, 50000, '2024-01-16', 2),
(4, 3, 3, 200000, '2024-01-16', 2),
(5, 2, 15, 100000, '2024-01-17', 1),
(6, 1, 20, 50000, '2024-01-17', 3),
(7, 4, 2, 500000, '2024-01-18', 3),
(8, 2, 10, 100000, '2024-01-18', 2);

-- Insert products data (상품 데이터 입력)
INSERT INTO products VALUES
(1, 'Laptop A', 'Electronics', 50000),
(2, 'Mouse B', 'Electronics', 100000),
(3, 'Monitor C', 'Electronics', 200000),
(4, 'Keyboard D', 'Electronics', 500000);

-- Query all data (모든 데이터 조회)
SELECT * FROM sales;
SELECT * FROM products;
```

Submission: Screenshot showing all sales records and products (제출: sales 테이블에 8개 판매 기록과 products 테이블이 모두 보이는 스크린샷)

---

**Question 17** Perform the following on sales table and verify results. (sales 테이블에서 다음을 수행하고 결과를 확인하시오.)

```sql
-- 1. Total sales quantity (전체 판매량 합계)
SELECT SUM(quantity) AS total_quantity FROM sales;

-- 2. Average price (평균 가격)
SELECT AVG(unit_price) AS avg_price FROM sales;

-- 3. Highest price product (최고 가격 상품)
SELECT MAX(unit_price) AS max_price FROM sales;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Perform the following on sales table. (sales 테이블에서 다음을 수행하시오.)

```sql
-- 1. Sales quantity per product (상품별 판매량)
SELECT product_id, SUM(quantity) AS total_quantity
FROM sales
GROUP BY product_id;

-- 2. Average price per product (상품별 평균 가격)
SELECT product_id, AVG(unit_price) AS avg_price
FROM sales
GROUP BY product_id;

-- 3. Sales count per product (상품별 판매 횟수)
SELECT product_id, COUNT(*) AS sales_count
FROM sales
GROUP BY product_id;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

**Question 19** Perform the following analysis on sales table. (sales 테이블에서 다음 분석을 수행하시오.)

```sql
-- 1. Products with sales quantity >= 5 (판매량이 5개 이상인 상품)
SELECT product_id, SUM(quantity) AS total_quantity
FROM sales
GROUP BY product_id
HAVING SUM(quantity) >= 5;

-- 2. Products with average price >= 100,000 (평균 가격이 100000원 이상인 상품)
SELECT product_id, AVG(unit_price) AS avg_price
FROM sales
GROUP BY product_id
HAVING AVG(unit_price) >= 100000;

-- 3. Products sold 2 or more times (판매 횟수가 2회 이상인 상품)
SELECT product_id, COUNT(*) AS sales_count
FROM sales
GROUP BY product_id
HAVING COUNT(*) >= 2;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex aggregate queries. (다음의 복합 집계 쿼리를 작성하고 실행하시오.)

```
Requirements:

1. Grouping by category and product for aggregation
   Group by category and product_name, 
   showing total quantity and average price

2. Category sales status (sales qty, count, avg price)
   Sorted by quantity DESC, limited to top results

3. Top 3 categories by sales (LIMIT)
   Group by category, order by total quantity DESC

4. 2 or more creative aggregate queries:
   - GROUP BY with HAVING combination
   - Using COUNT(DISTINCT)
   - Apply sorting and limiting

Submission:
   - SQL code for each query
   - Execution result screenshot for each query

요구사항:

1. 카테고리별, 상품별로 그룹화하여 판매량과 가격 집계

2. 카테고리별 판매 현황 (판매량, 판매 횟수, 평균 가격)

3. 판매량 상위 3개 카테고리 (LIMIT)

4. 자유로운 집계 쿼리 2개 이상:
   - GROUP BY와 HAVING 조합
   - COUNT(DISTINCT) 활용
   - 정렬 및 제한

제출:
   - 각 쿼리의 SQL 코드
   - 각 쿼리의 실행 결과 스크린샷
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                                    |
| :------: | :----: | :--------------------------------------------------------------------------------------------- |
|    1    |   ②   | COUNT(*) includes NULL, COUNT(column) excludes NULL (NULL을 포함/제외)                         |
|    2    |   ②   | GROUP BY groups rows and applies aggregate functions (행들을 그룹화 후 집계함수 적용)          |
|    3    |   ④   | Different functions handle differently (집계함수에 따라 다름)                                  |
|    4    |   ②   | HAVING filters grouped results (그룹화 결과 필터링)                                            |
|    5    |   ②   | COUNT(DISTINCT) counts unique values only (중복 제거한 유일값 개수)                            |
|    6    |   ②   | Correct (올바름)                                                                               |
|    7    |   ④   | WHERE individual rows, HAVING groups, ③ also correct (WHERE는 개별, HAVING은 그룹, ③도 맞음) |
|    8    |   ②   | Use HAVING for group conditions (HAVING으로 그룹 조건 필터링)                                  |
|    9    |   ②   | Query B excludes NULL values (manager_id가 NULL인 행 제외)                                     |
|    10    |   ②   | Without GROUP BY, returns 1 row of overall stats (GROUP BY 없으면 전체 통계 1행)               |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Aggregate Function Differences

**Model Answer (모범 답안):**

```
COUNT(*): Count all rows (includes NULL)
COUNT(column): Count non-NULL values

SUM(column): Sum of numeric column (excludes NULL)
AVG(column): Average of numeric column (excludes NULL)
MAX(column): Maximum value (excludes NULL)
MIN(column): Minimum value (excludes NULL)

NULL Handling:
- SUM, AVG, MAX, MIN: Ignore NULL
- COUNT(*): Include NULL
- COUNT(column): Exclude NULL
```

---

### Question 12: GROUP BY Situations

**Model Answer (모범 답안):**

```
GROUP BY necessary when:
- Group by department, category, etc.
- Need statistics for each group
- Examples: average salary per dept, sales qty per product

Employees per department query:
SELECT dept_id, COUNT(*) AS employee_count
FROM employees
GROUP BY dept_id;

Result:
dept_id | employee_count
1       | 3
2       | 2
3       | 2
```

---

### Question 13: NULL Impact

**Model Answer (모범 답안):**

```
NULL impact on aggregate functions:
- COUNT(*): Includes NULL in count
- COUNT(column): Excludes NULL from count
- SUM, AVG, MAX, MIN: Ignore NULL

Example:
If 10 employees, 2 with manager_id = NULL:

COUNT(*) FROM employees → 10
COUNT(manager_id) FROM employees → 8 (excludes 2 NULLs)

Result:
- COUNT(*) = COUNT(manager_id) + NULL count
- Large difference when many NULL values exist
```

---

### Question 14: HAVING Necessity

**Model Answer (모범 답안):**

```
HAVING necessity:
- Filter groups created by GROUP BY

WHERE vs HAVING:

WHERE:
- Timing: Before GROUP BY
- Target: Individual rows
- Example: WHERE salary > 4000000

HAVING:
- Timing: After GROUP BY
- Target: Groups
- Example: HAVING AVG(salary) > 4000000
- Can use aggregate functions

Example query:
SELECT dept_id, AVG(salary)
FROM employees
WHERE salary > 4000000    -- Filter individual employees
GROUP BY dept_id
HAVING AVG(salary) > 4500000; -- Filter groups
```

---

### Question 15: Multiple Column GROUP BY

**Model Answer (모범 답안):**

```
Multiple column GROUP BY precautions:

1. Group count increases exponentially
   GROUP BY col1: 5 groups
   GROUP BY col1, col2: 5 × 10 = 50 groups

2. Don't select ungrouped columns in SELECT
   MySQL 5.7+ raises error

3. Consider sort order
   Same col1 group, sorted by col2

Performance optimization:
- Group only necessary columns
- Filter with WHERE first
- Use indexes
- Check column cardinality

Optimized query:
SELECT dept_id, position, COUNT(*) AS count
FROM employees
WHERE dept_id IS NOT NULL
GROUP BY dept_id, position
ORDER BY dept_id, COUNT(*) DESC;
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Table Creation

**Completion Criteria (완료 기준):**

✅ ch7_aggregation database created
✅ sales table with 8 records
✅ products table with 4 items

---

### Question 17: Basic Aggregate Functions

**Expected Result (예상 결과):**

```
1. total_quantity: 73 (10+5+8+3+15+20+2+10)
2. avg_price: 143,750
3. max_price: 500,000 (product 4)
```

---

### Question 18: GROUP BY Basics

**Completion Criteria (완료 기준):**

✅ Sales qty per product calculated
✅ Average price per product
✅ Sales count per product

**Expected Result (예상 결과):**

```
Sales quantity by product:
product_id | total_quantity
1          | 38
2          | 30
3          | 3
4          | 2
```

---

### Question 19: HAVING Filtering

**Model Answer (모범 답안):**

```sql
-- 1. Products with quantity >= 5
SELECT product_id, SUM(quantity) AS total_quantity
FROM sales
GROUP BY product_id
HAVING SUM(quantity) >= 5;

Result:
product_id | total_quantity
1          | 38
2          | 30

-- 2. Average price >= 100,000
SELECT product_id, AVG(unit_price) AS avg_price
FROM sales
GROUP BY product_id
HAVING AVG(unit_price) >= 100000;

Result:
product_id | avg_price
2          | 100,000
3          | 200,000
4          | 500,000

-- 3. Sold 2+ times
SELECT product_id, COUNT(*) AS sales_count
FROM sales
GROUP BY product_id
HAVING COUNT(*) >= 2;

Result:
product_id | sales_count
1          | 3
2          | 3
```

---

### Question 20: Complex Aggregation

**Model Answer (모범 답안):**

```sql
-- 1. Category and product grouping
SELECT category, product_name, SUM(quantity), AVG(price)
FROM sales
GROUP BY category, product_name;

-- 2. Category sales status
SELECT category, 
       SUM(quantity) AS total_qty,
       COUNT(*) AS sales_count,
       AVG(price) AS avg_price
FROM sales
GROUP BY category
ORDER BY total_qty DESC;

Result:
Electronics: 16 qty, 4 times, 76,666.67 avg

-- 3. Top 3 categories
SELECT category, SUM(quantity) AS total_qty
FROM sales
GROUP BY category
ORDER BY total_qty DESC
LIMIT 3;

-- 4. Creative Query 1: COUNT(DISTINCT)
SELECT COUNT(DISTINCT category) AS category_count,
       COUNT(DISTINCT product_name) AS product_count
FROM sales;

-- 5. Creative Query 2: Top sales
SELECT product_name, 
       SUM(quantity * price) AS total_sales
FROM sales
GROUP BY product_name
ORDER BY total_sales DESC
LIMIT 3;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
