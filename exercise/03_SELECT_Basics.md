# Chapter 3. SELECT Basics - Practice Problems

Dear students! After completing Chapter 3, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

3장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 3, you should understand the following:

- Understanding the basic structure of SELECT command (SELECT 명령어의 기본 구조 이해)
- SELECT execution order (FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT) (실행 순서 이해)
- Removing duplicates with DISTINCT (DISTINCT로 중복 제거)
- Sorting with ORDER BY (ORDER BY로 정렬)
- Pagination with LIMIT/OFFSET (페이지네이션)
- Using column aliases (열 별칭의 활용)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** In SELECT execution order, when is the WHERE clause executed? (SELECT 실행 순서에서 WHERE 절은 어디에 실행되는가?)

- ① Before FROM (FROM 이전)
- ② After FROM, before GROUP BY (FROM 이후, GROUP BY 이전)
- ③ After SELECT (SELECT 이후)
- ④ After ORDER BY (ORDER BY 이후)

---

**Question 2** What is the role of DISTINCT? (DISTINCT의 역할은?)

- ① Sort rows (행을 정렬함)
- ② Remove duplicate rows and show only unique rows (중복된 행을 제거하고 유일한 행만 표시)
- ③ Select only rows matching conditions (조건에 맞는 행만 선택)
- ④ Count the number of rows (행의 개수를 세어줌)

---

**Question 3** What is the purpose of column alias (alias) in the following SQL? (다음 SQL에서 열 별칭의 목적은?)

```sql
SELECT student_id AS 'Student ID', student_name AS 'Student Name'
FROM student;
```

- ① Change table name (테이블 이름 변경)
- ② Display column name more understandably in query results (조회 결과의 열 이름을 더 이해하기 쉽게 표시)
- ③ Change data type (데이터 타입 변경)
- ④ Improve WHERE clause performance (WHERE 절의 성능 향상)

---

**Question 4** What is the default sort order when using ORDER BY? (ORDER BY를 사용할 때 기본 정렬 순서는?)

- ① Random (무작위)
- ② Descending (DESC) (내림차순)
- ③ Ascending (ASC) (오름차순)
- ④ Input order (입력 순서)

---

**Question 5** What is the meaning of LIMIT 10 OFFSET 20? (LIMIT 10 OFFSET 20의 의미는?)

- ① Query first 10 rows (처음 10개 행 조회)
- ② Query first 20 rows (처음 20개 행 조회)
- ③ Query rows 21-30 (10 rows total) (21번째부터 30번째까지 10개 행 조회)
- ④ Query 10 rows infinitely starting from row 20 (20번째부터 10개씩 무한 조회)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Why is the WHERE clause executed before GROUP BY in the following query? (다음 쿼리에서 WHERE 절이 GROUP BY 절 이전에 실행되는 이유는?)

```sql
SELECT department, COUNT(*)
FROM employee
WHERE salary > 5000000
GROUP BY department;
```

- ① WHERE is always executed first (항상 WHERE가 먼저 실행됨)
- ② Filter necessary data with WHERE first, then apply GROUP BY (efficiency) (WHERE로 먼저 필요한 데이터만 필터링 후 GROUP BY 적용 - 효율성)
- ③ GROUP BY groups by department first, then WHERE filters (GROUP BY로 같은 부서끼리 묶은 후 WHERE로 필터링)
- ④ Order doesn't matter (순서는 상관없음)

---

**Question 7** To query top 5 movies released in 2023 or later by highest rating in movie table, which is correct? (movie 테이블에서 2023년 이후에 개봉한 영화들을 평점 높은 순으로 상위 5개만 조회하려면?)

```sql
① SELECT * FROM movie
   WHERE release_year >= 2023
   ORDER BY rating DESC
   LIMIT 5;

② SELECT * FROM movie
   LIMIT 5
   WHERE release_year >= 2023
   ORDER BY rating DESC;

③ SELECT * FROM movie
   ORDER BY rating DESC
   WHERE release_year >= 2023
   LIMIT 5;
```

- ① Correct order (WHERE → ORDER BY → LIMIT) (올바른 순서)
- ② Correct order (only LIMIT position is different) (올바른 순서 - LIMIT 위치만 다름)
- ③ Correct order (only WHERE position is different) (올바른 순서 - WHERE 위치만 다름)
- ④ Only ① is correct (①만 올바름)

---

**Question 8** What does ORDER BY category ASC, price DESC mean when sorting by multiple columns? (복수 열로 정렬할 때 ORDER BY category ASC, price DESC의 의미는?)

- ① Both category and price in ascending order (카테고리와 가격 모두 오름차순)
- ② Category ascending, price descending (same category items sorted by price) (카테고리는 오름차순, 가격은 내림차순 - 같은 카테고리 내 가격으로 정렬)
- ③ Category sorted first, price not sorted (카테고리 우선 정렬, 가격으로는 정렬 안 함)
- ④ Price sorted first, category ignored (가격 우선 정렬, 카테고리는 무시)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Why do the following two queries return different results? (다음 두 쿼리의 실행 결과가 다른 이유는?)

```
Query A:
SELECT * FROM movie
WHERE rating >= 8.0
LIMIT 10;

Query B:
SELECT * FROM movie
LIMIT 10
WHERE rating >= 8.0;
```

- ① Both queries return same result (두 쿼리 모두 같은 결과)
- ② Query A is valid, Query B is syntax error (WHERE must come before LIMIT) (쿼리 A는 valid, 쿼리 B는 문법 오류)
- ③ Query B is faster (쿼리 B가 더 빠름)
- ④ Both depend on system (둘 다 시스템에 따라 다름)

---

**Question 10** Which query is most efficient for the following situation? (다음 상황에서 가장 효율적인 쿼리는?)

"Among 1000 products, query top 20 from '전자제품' category by highest price, show 10 per page, currently viewing 3rd page"

(1000개 상품 중 '전자제품' 카테고리에서 가격이 높은 순으로 상위 20개를 조회하되, 페이지당 10개씩 보여주고 현재 3번째 페이지를 조회)

```
① SELECT * FROM product
   WHERE category = '전자제품'
   ORDER BY price DESC
   LIMIT 10 OFFSET 20;

② SELECT * FROM product
   ORDER BY price DESC
   LIMIT 10 OFFSET 20
   WHERE category = '전자제품';

③ SELECT * FROM product
   LIMIT 10 OFFSET 20
   WHERE category = '전자제품';
```

- ① Correct (filter with WHERE → ORDER BY → LIMIT/OFFSET) (올바름)
- ② Syntax error (문법 오류)
- ③ Syntax error (문법 오류)
- ④ Both ② and ③ are correct (②와 ③ 모두 올바름)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** List the 7 steps of SELECT execution order. (SELECT 명령어의 기본 실행 순서 7단계를 나열하시오.)

---

**Question 12** To query all genres from movie table without duplication, which keyword should be used? Explain why. (movie 테이블에서 장르(genre)가 중복되지 않게 모든 장르를 조회하려면 어떤 키워드를 사용해야 하며, 그 이유를 설명하시오.)

---

**Question 13** Write a SELECT statement to get the following result: (다음 결과를 얻기 위한 SELECT 문을 작성하시오.)

```
Query products from product table, use aliases:
- product_name → Product Name
- price → Base Price
- price * 1.1 → 10% Marked Up Price

product 테이블에서 전자제품의 가격을 조회, 열 이름을 다음과 같이 별칭으로 표시:
- product_name → 상품명
- price → 원가
- price * 1.1 → 10% 인상가
```

---

## Intermediate Level (1 Question)

**Question 14** Explain the importance of ORDER BY sorting multiple columns, and provide practical examples. (ORDER BY 복수 열 정렬의 중요성을 설명하고, 실무 예시를 제시하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain the pagination formula and calculate offset values for pages 1, 2, and 3 when showing 5 products per page. (페이지네이션 공식을 설명하고, 5개 상품씩 페이지네이션할 때 페이지 1, 2, 3의 OFFSET 값을 계산하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database and table (데이터베이스 생성 및 테이블 생성)
CREATE DATABASE ch3_practice CHARACTER SET utf8mb4;
USE ch3_practice;

-- Create movie table (영화 테이블 생성)
CREATE TABLE movie (
    movie_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(50),
    genre VARCHAR(20),
    release_year INT,
    rating DECIMAL(3,2)
);

-- Insert sample data (샘플 데이터 입력)
INSERT INTO movie VALUES
(1, 'Shopping Mall King', 'Drama', 2023, 8.5),
(2, 'Art of Coding', 'Action', 2023, 7.8),
(3, 'Data World', 'Fantasy', 2022, 8.2),
(4, 'Romantic SQL', 'Romance', 2023, 7.5),
(5, 'Animation Server', 'Animation', 2023, 8.0);

-- Query all data (모든 데이터 조회)
SELECT * FROM movie;
```

Submission: Screenshot showing all 5 movies inserted (1 screenshot) (제출: 5개 영화 데이터가 모두 입력된 스크린샷 1장)

---

**Question 17** Perform the following queries on movie table and verify results. (movie 테이블에서 다음을 수행하고 결과를 확인하시오.)

```sql
-- 1. Sort by rating highest first, show top 3 (평점 높은 순 상위 3개)
SELECT title, rating
FROM movie
ORDER BY rating DESC
LIMIT 3;

-- 2. Show unique genres (중복 제거된 장르만 조회)
SELECT DISTINCT genre
FROM movie;

-- 3. Query movies released 2023 or later (2023년 이후 개봉 영화)
SELECT title, release_year, rating
FROM movie
WHERE release_year >= 2023;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Perform the following queries on product table. (product 테이블에서 다음 조회를 수행하시오.)

```sql
-- 1. Query products from Electronics category (전자제품 카테고리 조회)
SELECT * FROM product
WHERE category = 'Electronics';

-- 2. Sort by price lowest first (가격 낮은 순 정렬)
SELECT product_name, price
FROM product
ORDER BY price ASC;

-- 3. Show top 3 only (상위 3개만 표시)
SELECT * FROM product
LIMIT 3;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

**Question 19** Perform the following analysis on movie table. (movie 테이블에서 다음 분석을 수행하시오.)

```
Questions:
1. Write SQL to get genres that appear more than once
2. Write SQL to show movies by release_year DESC, then by rating DESC
3. Write SQL to show movie titles with alias "Movie Title" and rating with alias "Score"
4. Provide screenshots of each query result

질문:
1. 2번 이상 나오는 장르를 조회하는 SQL 작성
2. 개봉년도 내림, 평점 내림 순으로 정렬하는 SQL 작성
3. 영화 제목에 "Movie Title" 별칭, 평점에 "Score" 별칭을 주는 SQL 작성
4. 각 쿼리의 결과를 스크린샷으로 제시

Submission: 3 SQL codes + execution result screenshots (SQL과 실행 결과 스크린샷)
```

---

## Advanced Level (1 Question)

**Question 20** Create product table and perform pagination and complex queries. (product 테이블을 생성하여 페이지네이션 및 복합 조회를 수행하시오.)

```
Requirements:
1. Create product table with 10 sample products
2. Pagination: page 1, 2, 3, 4 (3 items per page)
3. Find first product of each category sorted by category
4. Top 5 highest price products
5. Products with rating >= 4.5 sorted by price

요구사항:
1. 10개 상품으로 product 테이블 생성
2. 페이지네이션: 페이지 1, 2, 3, 4 (페이지당 3개)
3. 각 카테고리별 첫 상품 조회
4. 가격 TOP 5
5. 평점 4.5 이상을 가격으로 정렬

Submission:
   - CREATE TABLE SQL
   - INSERT SQL (10 items)
   - All SELECT query codes
   - Each query result screenshot

제출:
   - CREATE TABLE SQL
   - INSERT SQL (10개 상품)
   - 모든 SELECT 쿼리 코드
   - 각 쿼리의 실행 결과 스크린샷
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                                                                                                                       |
| :------: | :----: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|    1    |   ②   | SELECT execution order: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT (SELECT 실행 순서: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT) |
|    2    |   ②   | DISTINCT removes duplicate rows and shows only unique rows (DISTINCT는 중복된 행을 제거하고 유일한 행만 표시)                                                                     |
|    3    |   ②   | Column alias makes query result column names more understandable (열 별칭은 조회 결과의 열 이름을 더 이해하기 쉽게 표시)                                                          |
|    4    |   ③   | ORDER BY default is ascending (ASC) (ORDER BY 기본값은 오름차순)                                                                                                                  |
|    5    |   ③   | LIMIT 10 OFFSET 20 queries rows 21-30 (OFFSET = (page-1) * rows) (LIMIT 10 OFFSET 20은 21~30번째 10개 행 조회)                                                                    |
|    6    |   ②   | WHERE filters first to reduce processing volume for GROUP BY (efficiency) (WHERE로 먼저 필터링하면 GROUP BY의 처리량 감소 - 효율성)                                               |
|    7    |   ①   | Correct order: WHERE → ORDER BY → LIMIT (올바른 순서: WHERE → ORDER BY → LIMIT)                                                                                               |
|    8    |   ②   | ORDER BY category ASC, price DESC: category ascending first, price descending within same category (카테고리 우선 오름, 같은 카테고리 내 가격 내림)                               |
|    9    |   ②   | Query B has WHERE after LIMIT which violates SQL syntax (WHERE must come before LIMIT) (쿼리 B는 WHERE가 LIMIT 뒤에 있어 문법 오류)                                               |
|    10    |   ①   | WHERE to filter → ORDER BY to sort → LIMIT/OFFSET for pagination is correct (WHERE로 필터링 → ORDER BY로 정렬 → LIMIT/OFFSET으로 페이징이 올바름)                             |

---

## Short Answer Model Answers (5 Questions)

### Question 11: SELECT Execution Order (7 Steps)

**Model Answer (모범 답안):**

```
1. FROM: Determine table to query (조회할 테이블 결정)
2. WHERE: Filter rows by conditions (행 필터링)
3. GROUP BY: Group rows together (행을 그룹으로 묶음)
4. HAVING: Filter groups by conditions (그룹 필터링)
5. SELECT: Determine columns to query (조회할 열 결정)
6. ORDER BY: Sort results (결과 정렬)
7. LIMIT/OFFSET: Limit row count and specify start position (행 수 제한 및 시작 위치 지정)
```

---

### Question 12: Using DISTINCT

**Model Answer (모범 답안):**

- **Keyword:** DISTINCT
- **SQL:** SELECT DISTINCT genre FROM movie;
- **Reason:** Because genre column may have duplicates (e.g., Drama appears 2 times, Action 1 time), use DISTINCT to query only unique genres (genre 열에는 중복된 장르가 있을 수 있으므로 DISTINCT로 유일한 장르만 조회)

---

### Question 13: SELECT with Column Aliases

**Model Answer (모범 답안):**

```sql
SELECT product_name AS 'Product Name',
       price AS 'Base Price',
       ROUND(price * 1.1) AS '10% Marked Up Price'
FROM product
WHERE category = 'Electronics';
```

Or without AS:

```sql
SELECT product_name 'Product Name',
       price 'Base Price',
       ROUND(price * 1.1) '10% Marked Up Price'
FROM product
WHERE category = 'Electronics';
```

---

### Question 14: ORDER BY Multiple Columns

**Model Answer (모범 답안):**

```
Importance (중요성):
- Specify sort order explicitly for consistent results (정렬 순서를 명확히 지정하여 일관된 결과 보장)
- Sort partial duplicate values in detail (부분 중복 값을 세부적으로 정렬)

Practical examples (실무 예시):

1. Sort by department → salary (높은 순)
   SELECT * FROM employee
   ORDER BY department ASC, salary DESC;
   
2. Sort by sale_date → quantity
   SELECT * FROM sales
   ORDER BY sale_date ASC, quantity DESC;
   
3. Sort by department → grade → score (높은 순)
   SELECT * FROM student
   ORDER BY department ASC, grade ASC, score DESC;
```

---

### Question 15: Pagination Formula

**Model Answer (모범 답안):**

```
Formula: OFFSET = (page_number - 1) × rows_per_page
공식: OFFSET = (페이지번호 - 1) × 페이지당행수

Pagination with 5 products per page (5개 상품씩 페이지네이션):

Page 1:
SELECT * FROM product LIMIT 5 OFFSET 0;
OFFSET = (1 - 1) × 5 = 0 (Products 1-5)

Page 2:
SELECT * FROM product LIMIT 5 OFFSET 5;
OFFSET = (2 - 1) × 5 = 5 (Products 6-10)

Page 3:
SELECT * FROM product LIMIT 5 OFFSET 10;
OFFSET = (3 - 1) × 5 = 10 (Products 11-15)
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Movie Table Creation and Data Entry

**Completion Criteria (완료 기준):**

✅ ch3_practice database created (ch3_practice 데이터베이스 생성됨)
✅ movie table created (5 columns) (movie 테이블 생성됨)
✅ 5 movies data inserted (5개 영화 데이터 입력됨)
✅ SELECT * FROM movie executed (SELECT * FROM movie 실행됨)

**Screenshot content includes (스크린샷 포함 내용):**

- All 5 movies displayed (5개 영화 데이터 모두 표시)

---

### Question 17: Movie Table Various SELECT Queries

**Completion Criteria (완료 기준):**

✅ Sorted by rating DESC: Shopping Mall King(8.5) → Data World(8.2) → ...
✅ DISTINCT genre: Drama, Action, Fantasy, Romance, Animation (5 unique) (5개 유일)
✅ Released 2023 or later: Shopping Mall King, Art of Coding, Romantic SQL, Animation Server (4 items) (4개)

**Screenshot content includes (스크린샷 포함 내용):**

- All 3 query results accurately displayed (3개 쿼리 결과 모두 정확하게 표시)

---

### Question 18: Product Table Conditions Query

**Completion Criteria (완료 기준):**

✅ Electronics category: Wireless Mouse, Mechanical Keyboard, Monitor Arm (3 items) (3개)
✅ Price ascending order: Chair Cushion(28000) → Desk Lamp(35000) → ... (정확한 순서)
✅ Top 3 only: First 3 rows displayed (처음 3개 행만 표시)

---

### Question 19: Movie Table Complex Analysis

**Model Answer (모범 답안):**

```sql
-- 1. Genres appearing more than once
SELECT genre
FROM movie
GROUP BY genre
HAVING COUNT(*) > 1;

-- 2. Sort by year DESC, then rating DESC
SELECT * FROM movie
ORDER BY release_year DESC, rating DESC;

-- 3. With aliases
SELECT title AS 'Movie Title', rating AS 'Score'
FROM movie;
```

---

### Question 20: Product Pagination and Complex Queries

**Model Answer (모범 답안):**

```sql
-- Create table (테이블 생성)
CREATE TABLE product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50),
    category VARCHAR(20),
    price INT,
    rating DECIMAL(3,2)
);

-- Insert 10 products (10개 상품 입력)
INSERT INTO product VALUES
(1, 'Wireless Mouse', 'Electronics', 45000, 4.50),
(2, 'Mechanical Keyboard', 'Electronics', 120000, 4.60),
(3, 'Monitor Arm', 'Electronics', 65000, 4.30),
(4, 'Desk Lamp', 'Home', 35000, 4.40),
(5, 'Chair Cushion', 'Furniture', 28000, 4.20),
(6, 'Wireless Speaker', 'Electronics', 89000, 4.55),
(7, 'Table Lamp', 'Home', 42000, 4.35),
(8, 'Desk', 'Furniture', 250000, 4.70),
(9, 'Monitor', 'Electronics', 350000, 4.80),
(10, 'USB Hub', 'Electronics', 32000, 4.25);

-- Page 1 (rows 1-3) (페이지 1)
SELECT * FROM product LIMIT 3 OFFSET 0;

-- Page 2 (rows 4-6) (페이지 2)
SELECT * FROM product LIMIT 3 OFFSET 3;

-- Page 3 (rows 7-9) (페이지 3)
SELECT * FROM product LIMIT 3 OFFSET 6;

-- Page 4 (rows 10-12) (페이지 4)
SELECT * FROM product LIMIT 3 OFFSET 9;

-- First product of each category sorted by category (각 카테고리별 첫 상품)
SELECT product_name, category, price
FROM product
WHERE product_id IN (
    SELECT MIN(product_id) FROM product GROUP BY category
)
ORDER BY category;

-- Top 5 highest price (가격 TOP 5)
SELECT product_name, price
FROM product
ORDER BY price DESC
LIMIT 5;

-- Rating >= 4.5 sorted by price (평점 4.5 이상을 가격으로 정렬)
SELECT product_name, price, rating
FROM product
WHERE rating >= 4.5
ORDER BY price DESC;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
