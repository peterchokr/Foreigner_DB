# Chapter 3. SELECT Basics and Single Table Query

---

## 📋 Class Overview

**Class Topic**: Basic Data Query Using SELECT Statement (SELECT 문을 이용한 기본 데이터 조회)

**Learning Objectives** (수업 목표)

- Understand the basic structure and execution order of SELECT statement (SELECT 문의 기본 구조와 실행 순서 이해)
- Master basic functions such as column selection, aliases, and sorting (열 선택, 별칭, 정렬 등 기본 기능 숙달)
- Develop practical data query skills (실무 중심의 데이터 조회 능력 배양)

---

## 📚 Part 1: Theoretical Learning

### What You'll Learn in This Section

In this section, you will learn the SELECT statement, which is the foundation of SQL. You will understand the execution order of the SELECT statement and the role of each clause, and learn various functions such as column selection, duplicate removal, alias assignment, sorting, and row limiting. Through this, you will develop the ability to effectively query desired data from a database.

이 섹션에서는 SQL의 가장 기본이 되는 SELECT 문을 배웁니다. SELECT 문의 실행 순서와 각 절의 역할을 이해하고, 열 선택, 중복 제거, 별칭 지정, 정렬, 행 제한 등 다양한 기능을 학습합니다. 이를 통해 데이터베이스에서 원하는 데이터를 효과적으로 조회하는 능력을 기르게 됩니다.

### 1-1. Basic Structure of SELECT Statement

#### **Basic Form**

```sql
SELECT column_name1, column_name2, ...
FROM table_name;
```

### 1-2. Column Selection

```
* Usage: Query all columns (모든 열 조회)
SELECT * FROM student;

Specific columns only: Query only required columns (필요한 열만 조회)
SELECT student_id, name FROM student;

Multiple columns: Query in desired order (원하는 순서대로 조회)
SELECT name, student_id, gpa FROM student;
```

### 1-3. Column Alias

```sql
-- Using AS (AS 사용)
SELECT student_id AS student_number, name AS student_name FROM student;

-- Omit AS (AS 생략)
SELECT student_id student_number, name student_name FROM student;

-- Include quotes if contains spaces (공백 포함 시 따옴표)
SELECT student_id AS 'Student ID' FROM student;
```

### 1-4. DISTINCT (Remove Duplicates - 중복 제거)

```sql
-- Remove duplicates from department information (학과 정보 중복 제거)
SELECT DISTINCT department FROM student;

-- Remove duplicates from multiple columns (여러 열 중복 제거)
SELECT DISTINCT department, gpa FROM student;
```

### 1-5. LIMIT (Limit Number of Rows - 행 수 제한)

```sql
-- Query top 5 only (상위 5개만 조회)
SELECT * FROM student LIMIT 5;

-- Query 10 records starting from 6th (6번째부터 10개 조회)
SELECT * FROM student LIMIT 5 OFFSET 5;

-- Pagination: 10 per page (페이지네이션: 한 페이지에 10개)
-- Page 1 (1페이지)
SELECT * FROM student LIMIT 10;
-- Page 2 (2페이지)
SELECT * FROM student LIMIT 10 OFFSET 10;
```

### 1-6. ORDER BY (Sorting - 정렬)

```sql
-- Ascending (오름차순, ASC)
SELECT * FROM student ORDER BY gpa ASC;

-- Descending (내림차순, DESC)
SELECT * FROM student ORDER BY gpa DESC;

-- Multiple column sorting: Department ascending, GPA descending (복수 열 정렬: 학과별 오름차순, 학점 내림차순)
SELECT * FROM student 
ORDER BY department ASC, gpa DESC;
```

---

## 📚 Part 2: Sample Data Setup

### What You'll Learn in This Section

In this section, you will create the movie and product tables used for SELECT practice. By practicing with two tables that have various attributes, you will learn how to use SELECT statements in various situations.

이 섹션에서는 SELECT 실습에 사용할 movie와 product 테이블을 생성합니다. 다양한 속성을 가진 두 개의 테이블에서 실습함으로써 여러 상황에 대응하는 SELECT 문 활용법을 배웁니다.

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch3_practice CHARACTER SET utf8mb4;
USE ch3_practice;

-- Movie table (영화 테이블)
CREATE TABLE movie (
    movie_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(50) NOT NULL,
    genre VARCHAR(20),
    release_year INT,
    release_date DATE,
    director VARCHAR(30),
    rating DECIMAL(3, 1),
    runtime INT,
    country VARCHAR(20)
) CHARACTER SET utf8mb4;

INSERT INTO movie VALUES
(1, 'The Shopping Mall King', 'Drama', 2023, '2023-01-15', 'Kim Director', 8.5, 120, 'Korea'),
(2, 'The Art of Coding', 'Action', 2023, '2023-02-20', 'Lee Director', 7.8, 135, 'Korea'),
(3, 'Data World', 'Fantasy', 2022, '2022-12-10', 'Park Director', 8.2, 145, 'USA'),
(4, 'Romantic SQL', 'Romance', 2023, '2023-03-05', 'Choi Director', 7.5, 110, 'Korea'),
(5, 'Animation Server', 'Animation', 2023, '2023-04-01', 'Jeong Director', 8.0, 90, 'USA');

-- Product table (상품 테이블)
CREATE TABLE product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50) NOT NULL,
    category VARCHAR(20),
    price INT,
    stock INT,
    upload_date DATE,
    brand VARCHAR(20),
    rating DECIMAL(3, 2)
) CHARACTER SET utf8mb4;

INSERT INTO product VALUES
(1, 'Wireless Mouse', 'Electronics', 45000, 150, '2024-01-10', 'Logitech', 4.50),
(2, 'Mechanical Keyboard', 'Electronics', 120000, 80, '2024-01-12', 'Ducky', 4.60),
(3, 'Monitor Arm', 'Electronics', 65000, 200, '2024-01-08', 'Elgo', 4.30),
(4, 'Desk Lamp', 'Home Supplies', 35000, 300, '2024-01-05', 'Philips', 4.40),
(5, 'Chair Cushion', 'Furniture', 28000, 250, '2024-01-15', 'IKEA', 4.20);
```

---

## 💻 Part 3: Hands-on Practice

### What You'll Learn in This Section

In this section, you will execute all the functions of the SELECT statement you learned to query data. Starting from basic SELECT, you will practice various functions step by step: alias assignment, duplicate removal, sorting, and row limiting. Through each practice, you will be able to use the SELECT statement freely.

이 섹션에서는 배운 SELECT 문의 모든 기능을 실제로 실행하여 데이터를 조회합니다. 기본적인 SELECT부터 시작하여 별칭 지정, 중복 제거, 정렬, 행 제한 등 다양한 기능을 단계적으로 실습합니다. 각 실습을 통해 SELECT 문을 자유롭게 사용할 수 있게 됩니다.

```sql
-- =====================================================
-- 3-1. SELECT Basics (SELECT 기초)
-- =====================================================
-- Practice 3-1~3-10: Basic SELECT Statements (기본 SELECT 문)

-- 1. Query all movies (전체 영화 조회)
SELECT * FROM movie;

-- 2. Query only movie titles (영화 제목만 조회)
SELECT title FROM movie;

-- 3. Query movie titles and directors (영화 제목과 감독 조회)
SELECT title, director FROM movie;

-- 4. Query all products (모든 상품 조회)
SELECT * FROM product;

-- 5. Query product names and prices only (상품명과 가격만 조회)
SELECT product_name, price FROM product;

-- 6. Remove duplicate product categories (상품 카테고리 중복 제거)
SELECT DISTINCT category FROM product;

-- 7. Remove duplicate movie genres (영화 장르 중복 제거)
SELECT DISTINCT genre FROM movie;

-- 8. Query top 3 products (상위 3개 상품 조회)
SELECT * FROM product LIMIT 3;

-- 9. Query 2 products starting from 3rd (3번째 상품부터 2개 조회)
SELECT * FROM product LIMIT 2 OFFSET 2;

-- 10. Query movie titles and ratings (영화 제목과 평점 조회)
SELECT title, rating FROM movie;

-- =====================================================
-- 3-2. Column Aliases and Sorting (열 별칭과 정렬)
-- =====================================================
-- Practice 3-11~3-20: Aliases and Sorting (별칭 및 정렬)

-- 11. Alias movie title as 'Movie Title', director as 'Director Name' (영화 제목을 '영화명'으로, 감독을 '감독명'으로 별칭)
SELECT title AS 'Movie Title', director AS 'Director Name' FROM movie;

-- 12. Alias product name as 'Product', price as 'Sale Price' (상품명을 '상품', 가격을 '판매가'로 별칭)
SELECT product_name AS 'Product', price AS 'Sale Price' FROM product;

-- 13. Alias with spaces (공백을 포함한 별칭)
SELECT product_name AS 'Product Name', price AS 'Sale Price' FROM product;

-- 14. Calculated alias including price (가격을 포함한 계산 별칭)
SELECT product_name, price, price * 1.1 AS '10% Increased Price' FROM product;

-- 15. Sort movies by rating in descending order (영화를 평점 내림차순으로 정렬)
SELECT title, rating FROM movie ORDER BY rating DESC;

-- 16. Sort products by price in ascending order (상품을 가격 오름차순으로 정렬)
SELECT product_name, price FROM product ORDER BY price ASC;

-- 17. Sort products by stock in descending order (상품을 재고 많은 순으로 정렬)
SELECT product_name, stock FROM product ORDER BY stock DESC;

-- 18. Sort movies by release year ascending, then rating descending (영화를 개봉년도 오름차순, 평점 내림차순으로 정렬)
SELECT title, release_year, rating FROM movie 
ORDER BY release_year ASC, rating DESC;

-- 19. Sort products by category, then by price (상품을 카테고리순, 가격순으로 정렬)
SELECT product_name, category, price FROM product 
ORDER BY category ASC, price DESC;

-- 20. Query top 3 movies by rating (영화 평점 상위 3개만 조회)
SELECT title, rating FROM movie 
ORDER BY rating DESC LIMIT 3;

-- =====================================================
-- 3-3. Advanced Practice (고급 실습)
-- =====================================================
-- Practice 3-21~3-33: Complex Queries (복합 조회)

-- 21. Query product name and discounted price (20% discount) (상품명과 '할인가' 20% 할인 조회)
SELECT product_name, price * 0.8 AS 'Discount Price' FROM product;

-- 22. Query all movie information sorted by rating descending (영화 정보를 평점 내림차순으로 정렬하여 모두 조회)
SELECT * FROM movie ORDER BY rating DESC;

-- 23. Query all categories removing duplicate product categories (상품 중복 카테고리 제거하여 모든 카테고리 조회)
SELECT DISTINCT category FROM product;

-- 24. Query only top 5 products from all products (전체 상품 중 상위 5개만 조회)
SELECT * FROM product LIMIT 5;

-- 25. Query movie title and rating sorted by high rating (영화 제목과 평점을 평점 높은 순으로 조회)
SELECT title AS 'Movie Title', rating AS 'Rating' 
FROM movie ORDER BY rating DESC;

-- 26. Query 5 products starting from 3rd (상품 중 3번째부터 5개 조회)
SELECT product_name, price FROM product LIMIT 5 OFFSET 2;

-- 27. Query movie title, director, release year sorted by year (영화의 제목, 감독, 개봉년도 조회 연도순 정렬)
SELECT title, director, release_year 
FROM movie ORDER BY release_year;

-- 28. Sort products by stock descending, then by price descending (상품을 재고 많은 순으로, 같으면 가격 비싼 순으로 정렬)
SELECT product_name, stock, price 
FROM product ORDER BY stock DESC, price DESC;

-- 29. Query movie title, rating, director sorted by rating (영화 제목과 평점, 감독을 평점순으로 조회)
SELECT title, rating, director FROM movie ORDER BY rating DESC;

-- 30. Query product name, price, category sorted by category (상품명과 가격, 카테고리를 카테고리순으로 조회)
SELECT product_name, price, category FROM product ORDER BY category;

-- 31. Query only 2023 movies (title, director only) (2023년 개봉 영화만 조회 제목, 감독만)
SELECT title, director FROM movie WHERE release_year = 2023;

-- 32. Query products with price 50000 or more (가격이 50000원 이상인 상품만 조회)
SELECT * FROM product WHERE price >= 50000;

-- 33. Query top 5 movies by rating (평점이 높은 순으로 상위 5개 영화 조회)
SELECT title, rating FROM movie ORDER BY rating DESC LIMIT 5;
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the execution order of the SELECT statement and the processing process at each stage in detail. Using specific SQL examples, describe the entire process from retrieving data from the FROM clause to sorting by ORDER BY.

SELECT 문의 실행 순서와 각 단계에서의 처리 과정을 상세히 설명하세요. 구체적인 SQL 예시를 들어 FROM 절에서 데이터를 가져오는 과정부터 ORDER BY로 정렬되는 전체 과정을 서술하세요.

**Assignment 2**: Explain the role and usage method of the DISTINCT keyword, and provide specific practical examples of situations where duplicate values need to be removed.

DISTINCT 키워드의 역할과 사용 방법을 설명하고, 실무에서 중복된 값을 제거해야 하는 상황을 구체적으로 예시하여 설명하세요.

**Assignment 3**: Explain how the priority is determined when sorting by multiple columns using the ORDER BY clause, and clearly distinguish between the concepts of ASC and DESC.

ORDER BY 절을 사용하여 복수의 열로 정렬할 때 우선순위가 어떻게 결정되는지 설명하고, ASC와 DESC의 개념을 명확히 구분하여 서술하세요.

**Assignment 4**: Explain how to implement pagination using the LIMIT and OFFSET keywords, and provide an example of querying 3 pages with 10 records per page.

LIMIT과 OFFSET 키워드를 사용하여 페이지네이션을 구현하는 방식을 설명하고, 한 페이지에 10개씩 3페이지를 조회하는 예시를 제시하세요.

**Assignment 5**: Explain the concept and purpose of column aliases, and present principles and precautions for creating readable aliases in practice.

열 별칭의 개념과 사용 목적을 설명하고, 실무에서 가독성 좋은 별칭을 작성하기 위한 원칙과 주의사항을 제시하세요.

**Submission Format**: Word or PDF document (1-2 pages)

---

### Practical Assignments

**Assignment 1**: Query the title, director, and rating of all movies from the movie table, sorted by rating in descending order, and present the results.

movie 테이블에서 모든 영화의 제목, 감독, 평점을 조회하되, 평점이 높은 순서대로 정렬하여 결과를 제시하세요.

**Assignment 2**: Query the product name, price, and 10% increased price (displayed as an alias) from the product table. The results should be sorted in ascending order by the original price, with only the top 5 queried.

product 테이블에서 상품명, 가격, 그리고 10% 인상가를 별칭으로 표시하여 조회하세요. 결과는 원래 가격의 오름차순으로 정렬되어야 하며, 상위 5개만 조회하세요.

**Assignment 3**: Query all movie genres without duplicates from the movie table. Use the DISTINCT keyword to check how many different genres there are, and present what each genre is.

movie 테이블에서 영화 장르의 모든 종류를 중복 없이 조회하세요. DISTINCT 키워드를 사용하여 서로 다른 장르가 몇 개인지 확인하고, 각 장르가 무엇인지 제시하세요.

**Assignment 4**: Query the product name, price, and rating of electronics category products from the product table, sorted by rating in descending order. Write the SQL statement that uses a WHERE clause to filter only electronics and sorts with ORDER BY.

product 테이블에서 전자제품 카테고리의 상품명, 가격, 평점을 조회하되, 평점이 높은 순서대로 정렬하세요. WHERE 절을 사용하여 전자제품만 필터링하고, ORDER BY로 정렬하는 과정을 SQL 문으로 작성하세요.

**Assignment 5**: Execute all queries provided from Practice 3-1 to 3-33 in Part 3 directly and attach screenshots of each query result. Additionally, create 5 or more creative queries and present their results as well.

Part 3의 실습 3-1부터 3-33까지 제공된 모든 쿼리를 직접 실행하고, 각 쿼리의 결과를 스크린샷으로 첨부하세요. 추가로 5개 이상의 창의적인 쿼리를 작성하여 그 결과도 함께 제시하세요.

**Submission Format**: SQL file (Ch3_SELECT_Practice_[StudentID].sql) and result screenshots

---

Thank you for your attention.

Cho Jeonghyun (peterchokr@gmail.com). Yeungnam University College
