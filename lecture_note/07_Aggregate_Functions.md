# Chapter 7. Aggregate Functions

---

## 📖 Class Overview

In this chapter, you will learn aggregate functions that reduce multiple rows of data to a single result value. You will cover basic aggregate functions such as COUNT, SUM, AVG, MAX, MIN as well as advanced grouping techniques using GROUP BY and HAVING. This is an essential technology for calculating various statistical information such as sales volume, sales revenue, and average scores in practice.

이 장에서는 데이터베이스의 여러 행을 하나의 결과값으로 축약하는 집계함수(Aggregate Functions)를 학습합니다.    
COUNT, SUM, AVG, MAX, MIN 등 기본 집계함수부터 GROUP BY와 HAVING을 사용한 고급 그룹화 기법까지 다룹니다. 실무에서 판매량, 매출액, 평균 점수 등 다양한 통계정보를 계산하는 데 필수적인 기술입니다.

---

## 📚 Part 1: Theoretical Learning

### 🌟 What You'll Learn in This Section

- COUNT function - 다양한 사용법
- SUM, AVG, MAX, MIN functions - 합계, 평균, 최대, 최소
- GROUP BY clause - 그룹화를 사용한 그룹화
- HAVING clause - HAVING 절로 그룹 필터링
- NULL value handling - NULL 값 처리 방법
- Grouping performance optimization - 그룹화 성능 최적화

---

### 7.1 COUNT Function

The COUNT function returns the number of rows in the specified column.

COUNT 함수는 지정한 열의 행 개수를 반환합니다.

**Syntax (문법):**

```sql
SELECT COUNT(*) FROM table_name;
SELECT COUNT(column) FROM table_name;
SELECT COUNT(DISTINCT column) FROM table_name;
```

**Characteristics (특징):**

- COUNT(*): Returns count of all rows including NULLs (모든 행의 개수 반환 NULL 포함)
- COUNT(column): Returns count of non-NULL values in that column (해당 열의 NULL이 아닌 값의 개수)
- COUNT(DISTINCT column): Returns count of different values excluding duplicates (중복을 제거한 서로 다른 값의 개수)

**Example (예시):**

```sql
SELECT COUNT(*) FROM employees;              -- Total number of employees (전체 직원 수)
SELECT COUNT(manager_id) FROM employees;     -- Number of employees with managers (상급자가 있는 직원 수)
SELECT COUNT(DISTINCT dept_id) FROM employees; -- Number of departments (부서 수)
```

---

### 7.2 SUM Function

The SUM function returns the sum of a numeric column.

SUM 함수는 숫자 열의 합계를 반환합니다.

**Syntax (문법):**

```sql
SELECT SUM(column) FROM table_name;
```

**Characteristics (특징):**

- Only numeric data is possible (숫자 데이터만 가능)
- NULL values are automatically excluded (NULL 값은 자동으로 제외)
- Returns NULL if all values are NULL (모든 값이 NULL이면 NULL 반환)

**Example (예시):**

```sql
SELECT SUM(salary) FROM employees;  -- Total salary (전체 급여 합계)
SELECT SUM(quantity) FROM orders;   -- Total order quantity (전체 주문 수량 합계)
```

---

### 7.3 AVG Function

The AVG function returns the average of a numeric column.

AVG 함수는 숫자 열의 평균을 반환합니다.

**Syntax (문법):**

```sql
SELECT AVG(column) FROM table_name;
```

**Characteristics (특징):**

- NULL values are automatically excluded (NULL 값은 자동으로 제외)
- Returns NULL if all values are NULL (모든 값이 NULL이면 NULL 반환)
- Be careful with decimal places (소수점 자리수에 주의)

**Example (예시):**

```sql
SELECT AVG(salary) FROM employees;   -- Average salary (평균 급여)
SELECT ROUND(AVG(score), 2) FROM results; -- Average score with 2 decimals (평균 점수 소수 2자리)
```

---

### 7.4 MAX and MIN Functions

The MAX function returns the maximum value, and the MIN function returns the minimum value.

MAX 함수는 최대값, MIN 함수는 최소값을 반환합니다.

**Syntax (문법):**

```sql
SELECT MAX(column) FROM table_name;
SELECT MIN(column) FROM table_name;
```

**Characteristics (특징):**

- Can be used with all data types: numbers, characters, dates, etc. (숫자, 문자, 날짜 등 모든 데이터타입에 사용 가능)
- NULL values are automatically excluded (NULL 값은 자동으로 제외)
- Useful for finding the most recent date or largest character value (가장 최근 날짜나 가장 큰 문자값 찾기에 유용)

**Example (예시):**

```sql
SELECT MAX(salary) FROM employees;        -- Maximum salary (최고 급여)
SELECT MIN(birth_date) FROM employees;    -- Oldest birth date (가장 오래된 생년월일)
SELECT MAX(order_date) FROM orders;       -- Most recent order date (가장 최근 주문일)
```

---

### 7.5 GROUP BY Clause

GROUP BY divides rows into groups and applies aggregate functions to each group.

GROUP BY는 행들을 그룹으로 나누어 각 그룹에 대해 집계함수를 적용합니다.

**Syntax (문법):**

```sql
SELECT column, aggregate_function(column)
FROM table_name
GROUP BY column;
```

**Example (예시):**

```sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id;           -- Average salary by department (부서별 평균 급여)

SELECT category, COUNT(*) AS count
FROM products
GROUP BY category;          -- Number of products by category (카테고리별 상품 개수)
```

---

### 7.6 GROUP BY with Multiple Columns

Grouping by multiple columns allows more detailed analysis.

여러 열로 그룹화하여 더 세밀한 분석이 가능합니다.

**Example (예시):**

```sql
SELECT dept_id, year, COUNT(*) AS count
FROM employees
GROUP BY dept_id, year;     -- Employee count by department and year (부서, 연도별 직원 수)

SELECT category, color, SUM(quantity) AS total_qty
FROM inventory
GROUP BY category, color;   -- Total quantity by category and color (카테고리, 색상별 재고 수량)
```

---

### 7.7 HAVING Clause

HAVING applies conditions to GROUP BY results, acting as WHERE for grouped data.

HAVING은 GROUP BY 결과에 조건을 적용하는 WHERE 역할을 합니다.

**Syntax (문법):**

```sql
SELECT column, aggregate_function(column)
FROM table_name
GROUP BY column
HAVING aggregate_function(column) > value;
```

**Example (예시):**

```sql
SELECT dept_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 4000000;  -- Departments with average salary over 4 million (평균 급여가 400만 이상인 부서)

SELECT category, COUNT(*) AS product_count
FROM products
GROUP BY category
HAVING COUNT(*) >= 5;  -- Categories with 5 or more products (상품이 5개 이상인 카테고리)
```

---

### 7.8 Aggregate Functions and NULL Handling

NULL values are handled specially in aggregate functions.

NULL 값은 집계함수에서 특별하게 처리됩니다.

**Characteristics (특징):**

- COUNT(*) exception: NULL values are included in the count (COUNT(*) 제외: NULL 값도 개수에 포함)
- COUNT(column): NULL values are excluded (NULL 값 제외)
- SUM, AVG, MAX, MIN: All exclude NULL values (모두 NULL 제외)

**NULL Conversion (NULL 변환):**

```sql
SELECT SUM(commission) FROM employees;      -- NULL is excluded (NULL은 제외)
SELECT SUM(IFNULL(commission, 0)) FROM employees;  -- Convert NULL to 0 (NULL을 0으로 변환)
```

---

### 7.9 WITH ROLLUP

WITH ROLLUP displays group subtotals and grand totals together.

WITH ROLLUP은 그룹별 소계와 총계를 함께 표시합니다.

**Syntax (문법):**

```sql
SELECT column, aggregate_function(column)
FROM table_name
GROUP BY column WITH ROLLUP;
```

**Example (예시):**

```sql
SELECT dept_id, SUM(salary)
FROM employees
GROUP BY dept_id WITH ROLLUP;  -- Display department totals and grand total (부서별, 전체 합계를 표시)
```

---

## 📚 Part 2: Sample Data

### sales table

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch7_aggr CHARACTER SET utf8mb4;
USE ch7_aggr;

-- Create sales table (sales 테이블 생성)
CREATE TABLE sales (
    sale_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10, 2),
    sale_date DATE,
    employee_id INT
);

-- Insert sample data (샘플 데이터 삽입)
INSERT INTO sales VALUES
(1, 1, 10, 50000, '2024-01-15', 1),
(2, 2, 5, 100000, '2024-01-15', 1),
(3, 1, 8, 50000, '2024-01-16', 2),
(4, 3, 3, 200000, '2024-01-16', 2),
(5, 2, 15, 100000, '2024-01-17', 1),
(6, 1, 20, 50000, '2024-01-17', 3),
(7, 4, 2, 500000, '2024-01-18', 3),
(8, 2, 10, 100000, '2024-01-18', 2);
```

### products table

```sql
-- Create products table (products 테이블 생성)
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50),
    category VARCHAR(30),
    price DECIMAL(10, 2),
    stock INT
);

-- Insert product data (상품 데이터 삽입)
INSERT INTO products VALUES
(1, 'Laptop A', 'Electronics', 50000, 100),
(2, 'Mouse B', 'Electronics', 100000, 200),
(3, 'Monitor C', 'Electronics', 200000, 50),
(4, 'Keyboard D', 'Electronics', 500000, 30);
```

---

## 💻 Part 3: Hands-on Practice

### 🌟 What You'll Learn in This Section

In this section, you will correctly use aggregate functions, combine GROUP BY and HAVING, practice patterns frequently used in practice, and handle NULL values and optimize performance.

이 섹션에서는 집계함수의 올바른 사용법, GROUP BY와 HAVING의 조합, 실무에서 자주 사용되는 집계 패턴, NULL 처리 및 성능 최적화를 배웁니다.

```sql
-- =====================================================
-- 7-1~7-8: Basic Aggregate Functions (COUNT, SUM, AVG, MAX, MIN)
-- =====================================================

-- 1. COUNT function basics (total number of sales) (COUNT 함수 기본 전체 판매 건수)
SELECT COUNT(*) AS total_sales FROM sales;

-- 2. COUNT and DISTINCT (number of different products sold) (COUNT와 DISTINCT 판매된 서로 다른 상품 개수)
SELECT COUNT(DISTINCT product_id) AS distinct_products FROM sales;

-- 3. COUNT with NULL (count excluding NULLs) (NULL을 포함한 COUNT NULL 제외한 개수)
SELECT COUNT(product_id) AS non_null_count FROM sales;

-- 4. SUM function (total sales quantity) (SUM 함수 전체 판매량 합계)
SELECT SUM(quantity) AS total_quantity FROM sales;

-- 5. SUM with condition (total sales after specific date) (SUM과 조건 특정 날짜 이후 판매액 합계)
SELECT SUM(quantity * unit_price) AS total_sales_amount 
FROM sales 
WHERE sale_date >= '2024-01-16';

-- 6. AVG function (average sales quantity) (AVG 함수 평균 판매 수량)
SELECT AVG(quantity) AS avg_quantity FROM sales;

-- 7. MAX function (highest unit price) (MAX 함수 가장 높은 단가)
SELECT MAX(unit_price) AS max_price FROM sales;

-- 8. MAX and MIN combination (price range) (MAX와 MIN의 조합 단가 범위)
SELECT MAX(unit_price) - MIN(unit_price) AS price_range FROM sales;

-- =====================================================
-- 7-9~7-16: GROUP BY and HAVING
-- =====================================================

-- 9. GROUP BY basics (sales quantity by product) (GROUP BY 기본 상품별 판매 수량)
SELECT product_id, SUM(quantity) AS total_qty
FROM sales
GROUP BY product_id;

-- 10. GROUP BY and COUNT (number of sales by product) (GROUP BY와 COUNT 상품별 판매 건수)
SELECT product_id, COUNT(*) AS sales_count
FROM sales
GROUP BY product_id;

-- 11. GROUP BY with multiple columns (sales by employee and date) (여러 열로 GROUP BY 직원별, 날짜별 판매액)
SELECT employee_id, DATE(sale_date) AS sale_date, SUM(quantity * unit_price) AS daily_sales
FROM sales
GROUP BY employee_id, DATE(sale_date);

-- 12. GROUP BY and ORDER BY (products by sales quantity descending) (GROUP BY와 ORDER BY 상품별 판매량 내림차순)
SELECT product_id, SUM(quantity) AS total_qty
FROM sales
GROUP BY product_id
ORDER BY total_qty DESC;

-- 13. HAVING for group filtering (products with 3+ sales) (HAVING으로 그룹 필터링 판매 건수 3건 이상인 상품)
SELECT product_id, COUNT(*) AS sales_count
FROM sales
GROUP BY product_id
HAVING COUNT(*) >= 3;

-- 14. WHERE and HAVING combination (specific period + sales condition) (WHERE와 HAVING 조합 특정 기간 + 판매액 조건)
SELECT product_id, SUM(quantity * unit_price) AS total_sales
FROM sales
WHERE sale_date >= '2024-01-01'
GROUP BY product_id
HAVING SUM(quantity * unit_price) >= 600000;

-- 15. GROUP BY with LIMIT (top 3 products by sales) (GROUP BY 후 LIMIT 판매액 상위 3개 상품)
SELECT product_id, SUM(quantity * unit_price) AS total_sales
FROM sales
GROUP BY product_id
ORDER BY total_sales DESC
LIMIT 3;

-- 16. Multiple aggregate functions (sales amount, count, average per product) (여러 집계함수 조합 상품별 판매액, 건수, 평균)
SELECT product_id, 
       SUM(quantity * unit_price) AS total_sales,
       COUNT(*) AS sales_count,
       AVG(quantity * unit_price) AS avg_sales
FROM sales
GROUP BY product_id;

-- =====================================================
-- 7-17~7-25: Complex Aggregation and Advanced Features
-- =====================================================

-- 17. Category statistics (product count, average price, max price) (카테고리별 통계 상품 개수, 평균 가격, 최대 가격)
SELECT category, COUNT(*) AS product_count, 
       AVG(price) AS avg_price, MAX(price) AS max_price
FROM products
GROUP BY category;

-- 18. Employee sales performance (total sales, count, average) (직원별 판매 실적 총 판매액, 건수, 평균)
SELECT employee_id, 
       SUM(quantity * unit_price) AS total_sales,
       COUNT(*) AS sales_count,
       AVG(quantity * unit_price) AS avg_sales
FROM sales
GROUP BY employee_id;

-- 19. Daily aggregation (sales, transaction count, average unit price) (날짜별 집계 판매액, 건수, 평균 단가)
SELECT DATE(sale_date) AS sale_date,
       SUM(quantity * unit_price) AS daily_sales,
       COUNT(*) AS transaction_count,
       AVG(unit_price) AS avg_unit_price
FROM sales
GROUP BY DATE(sale_date);

-- 20. Complex aggregation (category, product, quantity, sales, average price) (복합 집계 카테고리, 상품별 판매량, 판매액, 평균 가격)
SELECT p.category, p.product_id, p.product_name,
       SUM(s.quantity) AS total_qty,
       SUM(s.quantity * s.unit_price) AS total_sales,
       AVG(s.unit_price) AS avg_unit_price
FROM products p
JOIN sales s ON p.product_id = s.product_id
GROUP BY p.category, p.product_id, p.product_name;

-- 21. NULL handling (sum treating NULL as 0) (NULL 처리 NULL을 0으로 처리한 합계)
SELECT SUM(IFNULL(stock, 0)) AS total_stock FROM products;

-- 22. CASE with aggregate functions (sales amount by category) (CASE와 집계함수 조합 판매액 범주별 개수)
SELECT CASE 
           WHEN quantity * unit_price >= 500000 THEN 'Large'
           WHEN quantity * unit_price >= 300000 THEN 'Medium'
           ELSE 'Small'
       END AS sales_category,
       COUNT(*) AS count
FROM sales
GROUP BY sales_category;

-- 23. Subtotals (WITH ROLLUP - category subtotals) (부분합 WITH ROLLUP - 카테고리별 소계)
SELECT category, COUNT(*) AS product_count
FROM products
GROUP BY category
WITH ROLLUP;

-- 24. Ranking (sales ranking in descending order) (순위 매기기 판매액 높은 순서대로 순위)
SELECT product_id, SUM(quantity * unit_price) AS total_sales,
       ROW_NUMBER() OVER (ORDER BY SUM(quantity * unit_price) DESC) AS ranking 
FROM sales
GROUP BY product_id;

-- 25. Ranking within groups (sales ranking per product) (그룹 내 랭킹 각 상품 내에서 판매 순위)
SELECT product_id, sale_date, quantity * unit_price AS sales_amount,
       ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY quantity * unit_price DESC) AS product_rank
FROM sales;
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the characteristics of COUNT, SUM, AVG, MAX, MIN functions respectively, and comparatively analyze their behavior when NULL values are included. Present use cases where each function is needed in practice along with examples.

COUNT, SUM, AVG, MAX, MIN 함수의 특징을 각각 설명하고, NULL 값이 포함되었을 때의 동작 방식을 비교 분석하세요. 실무에서 각 함수가 필요한 상황을 사례와 함께 제시하세요.

**Assignment 2**: Explain the differences between GROUP BY, WHERE, and HAVING. Clearly describe the execution order and roles when using WHERE and HAVING together.

GROUP BY와 WHERE, HAVING의 차이점을 설명하세요. WHERE와 HAVING을 함께 사용할 때의 실행 순서와 각각의 역할을 명확히 서술하세요.

**Assignment 3**: Explain precautions when grouping by multiple columns. Discuss the problems when ungrouped columns are included in the SELECT clause and present solutions.

여러 열로 GROUP BY할 때의 주의사항을 설명하세요. SELECT 절에 그룹화되지 않은 열이 포함될 경우의 문제점과 해결 방법을 논의하세요.

**Assignment 4**: Present performance optimization methods for queries containing aggregate functions. Explain techniques such as index utilization, aggregation timing adjustment, and partial aggregation.

집계함수가 포함된 쿼리의 성능 최적화 방법을 제시하세요. 인덱스 활용, 집계 시점 조절, 부분 집계 등의 기법을 설명하세요.

**Assignment 5**: Explain advanced aggregation techniques using WITH ROLLUP, window functions, and subqueries. Compare advantages and disadvantages of each technique and present use cases.

WITH ROLLUP, 윈도우 함수, 서브쿼리를 사용한 고급 집계 기법을 설명하세요. 각 기법의 장단점을 비교하고 활용 사례를 제시하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Write aggregation queries from the sales data to perform the following:

판매 데이터에서 다음의 집계 쿼리를 작성하세요:

- Total sales count, total sales amount, average sales amount (전체 판매 건수, 판매액 합계, 평균 판매액)
- Sales count, total sales amount, average sales amount by product (상품별 판매 건수, 판매액 합계, 평균 판매액)
- Employee sales performance (total sales, count, average) (직원별 판매 실적 판매액, 건수, 평균)
- Top 5 products by sales amount (판매액이 높은 순서대로 상위 5개 상품)

**Assignment 2**: Use GROUP BY and HAVING to query the following:

GROUP BY와 HAVING을 사용하여 다음을 조회하세요:

- Products with 3 or more sales (판매 건수가 3건 이상인 상품)
- Employees with total sales 500000 or more (판매액 합계가 500000 이상인 직원)
- Products with average sales higher than overall average (평균 판매액이 전체 평균보다 높은 상품)

**Assignment 3**: Perform complex aggregation including NULL handling, CASE statements, and format conversion:

NULL 처리, CASE 문, 형식 변환을 포함한 복합 집계를 수행하세요:

- Calculate total compensation by employee including commission (commission 포함 직원별 총 보상액 계산)
- Classify sales by category (Large/Medium/Small) and perform category statistics (판매액을 범주 대중소로 분류하여 범주별 통계)
- Analyze quarterly sales performance (분기별 판매 성과 분석)

**Assignment 4**: Use WITH ROLLUP to perform hierarchical aggregation:

WITH ROLLUP을 사용하여 계층적 집계를 수행하세요:

- Category and product sales subtotals and grand total (카테고리별, 상품별 판매액 소계 및 전체 합계)
- Regional and branch sales performance hierarchical display (지역별, 지점별 판매 실적 계층적 표시)
- Cumulative sales by year and month (연도별, 월별 누적 판매액)

**Assignment 5**: Execute all queries provided from Practice 7-1 to 7-25 in Part 3 directly and attach screenshots of each query result. Additionally, create 5 or more creative aggregation queries, present their results, and explain how each query can help in business decision-making.

Part 3의 실습 7-1부터 7-25까지 제공된 모든 쿼리를 직접 실행하고, 각 쿼리의 결과를 스크린샷으로 첨부하세요. 추가로 5개 이상의 창의적인 집계 쿼리를 작성하여 그 결과를 제시하고, 각 쿼리가 어떤 비즈니스 의사결정에 도움이 될 수 있는지 설명하세요.

**Submission Format**: SQL file (Ch7_Aggregate_Functions_[StudentID].sql) and result screenshots

제출 형식: SQL 파일 (Ch7_Aggregate_Functions_[학번].sql) 및 결과 스크린샷

---

Thank you for your attention.

Cho Jeonghyun (peterchokr@gmail.com). Yeungnam University College
