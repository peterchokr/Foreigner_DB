# Chapter 4. WHERE Clause and Conditional Expressions

---

## 📋 Class Overview

**Class Topic**: Data Filtering Using WHERE Clause (WHERE 절을 이용한 데이터 필터링)

**Learning Objectives** (수업 목표)

- Understand comparison and logical operators perfectly (비교 연산자 및 논리 연산자 완벽 이해)
- Apply IN, BETWEEN, LIKE operators (IN, BETWEEN, LIKE 연산자 활용)
- Learn how to handle NULL values (NULL 값 처리 방법 습득)
- Develop ability to write complex conditional expressions (복잡한 조건식 작성 능력)

---

## 📚 Part 1: Theoretical Learning

### What You'll Learn in This Section

In this section, you will learn various methods of filtering data using the WHERE clause. You will study comparison operators, logical operators, and operators such as IN, BETWEEN, and LIKE, and develop the ability to write complex conditional expressions. You will also understand how to handle NULL values to perform accurate data queries.

이 섹션에서는 WHERE 절을 사용하여 데이터를 필터링하는 다양한 방법을 배웁니다. 비교 연산자, 논리 연산자, IN, BETWEEN, LIKE 등의 연산자를 학습하고, 복잡한 조건식을 작성하는 능력을 기릅니다. 또한 NULL 값의 처리 방법을 이해하여 정확한 데이터 조회를 할 수 있게 됩니다.

### 1-1. Comparison Operators

```
= (Equal): SELECT * FROM customer WHERE grade = 'Gold'; (같다)
!= or <> (Not Equal): SELECT * FROM customer WHERE city != 'Seoul'; (같지 않다)
< (Less Than): SELECT * FROM customer WHERE age < 30; (작다)
> (Greater Than): SELECT * FROM customer WHERE age > 25; (크다)
<= (Less Than or Equal): SELECT * FROM customer WHERE salary <= 5000000; (작거나 같다)
>= (Greater Than or Equal): SELECT * FROM customer WHERE age >= 20; (크거나 같다)
```

### 1-2. Logical Operators

```
AND (All conditions must be true): WHERE city = 'Seoul' AND age > 25; (모두 만족)
OR (At least one condition must be true): WHERE city = 'Seoul' OR city = 'Busan'; (하나라도 만족)
NOT (Negate the condition): WHERE NOT city = 'Seoul'; (조건 반대)
```

### 1-3. IN, BETWEEN, LIKE, IS NULL

```
IN: WHERE grade IN ('Gold', 'Silver');
BETWEEN: WHERE age BETWEEN 20 AND 30;
LIKE: WHERE name LIKE 'Kim%';
IS NULL: WHERE address IS NULL;
```

---

## 📚 Part 2: Sample Data

### What You'll Learn in This Section

In this section, you will create the customer table used for WHERE clause practice and insert various customer data. Based on customer information from actual business situations, you can practice various cases of condition filtering.

이 섹션에서는 WHERE 절 실습에 사용할 customer 테이블을 생성하고 다양한 고객 데이터를 삽입합니다. 실제 비즈니스 상황의 고객 정보를 기반으로 설계되어, 조건 필터링의 다양한 사례를 실습할 수 있습니다.

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch4_filtering CHARACTER SET utf8mb4;
USE ch4_filtering;

-- Create customer table (고객 테이블 생성)
CREATE TABLE customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30) NOT NULL,
    city VARCHAR(20),
    age INT,
    grade VARCHAR(10),
    salary INT,
    phone VARCHAR(15)
) CHARACTER SET utf8mb4;

-- Insert sample data (샘플 데이터 삽입)
INSERT INTO customer VALUES
(1, 'John Smith', 'Seoul', 35, 'Gold', 5000000, '010-1111-1111'),
(2, 'Emily Lee', 'Busan', 28, 'Silver', 3500000, '010-2222-2222'),
(3, 'Sarah Park', 'Seoul', 42, 'Gold', 6000000, '010-3333-3333'),
(4, 'Jessica Choi', 'Daegu', 25, 'Silver', 3000000, '010-4444-4444'),
(5, 'Michael Jung', 'Seoul', 38, 'Platinum', 7500000, NULL);
```

---

## 💻 Part 3: Hands-on Practice

### What You'll Learn in This Section

In this section, you will apply the various WHERE clause conditions you learned to filter data. Through various examples from single conditions to complex conditions, you will be able to use the WHERE clause freely. Additionally, you will understand the priority of conditional expressions and develop the ability to write efficient queries.

이 섹션에서는 배운 WHERE 절의 다양한 조건을 실제로 적용하여 데이터를 필터링합니다. 단일 조건부터 복합 조건까지 다양한 예제를 통해 WHERE 절을 자유롭게 사용할 수 있게 됩니다. 또한 조건식의 우선순위를 이해하고, 효율적인 쿼리를 작성하는 능력을 기르게 됩니다.

```sql
-- =====================================================
-- 3-1. Comparison Operators Practice (비교 연산자 실습)
-- =====================================================
-- Practice 4-1~4-10: Basic Comparison Operators (기본 비교 연산자)

-- 1. Query customers residing in Seoul (서울 거주 고객 조회)
SELECT * FROM customer WHERE city = 'Seoul';

-- 2. Query customers age 30 or over (30세 이상 고객 조회)
SELECT * FROM customer WHERE age >= 30;

-- 3. Query customers with Gold grade (Gold 등급 고객 조회)
SELECT * FROM customer WHERE grade = 'Gold';

-- 4. Query customers under age 35 (35세 미만 고객 조회)
SELECT * FROM customer WHERE age < 35;

-- 5. Query customers with salary 4000000 or more (4000000원 이상 월급 고객 조회)
SELECT * FROM customer WHERE salary >= 4000000;

-- 6. Query customers not residing in Busan (부산이 아닌 지역 거주 고객)
SELECT * FROM customer WHERE city != 'Busan';

-- 7. Query customers other than John Smith (김철수가 아닌 다른 고객)
SELECT * FROM customer WHERE name <> 'John Smith';

-- 8. Query customers exactly age 28 (정확히 28세인 고객)
SELECT * FROM customer WHERE age = 28;

-- 9. Query customers with salary 5000000 or less (5000000원 이하의 월급 고객)
SELECT * FROM customer WHERE salary <= 5000000;

-- 10. Query customers with grades other than Silver (Silver가 아닌 등급의 고객)
SELECT * FROM customer WHERE grade != 'Silver';

-- =====================================================
-- 3-2. Logical Operators Practice (논리 연산자 실습)
-- =====================================================
-- Practice 4-11~4-20: AND, OR, NOT Operators (AND, OR, NOT 연산자)

-- 11. Query customers residing in Seoul and age 30 or over (서울 거주하면서 30세 이상인 고객)
SELECT * FROM customer WHERE city = 'Seoul' AND age >= 30;

-- 12. Query Gold grade customers with salary 5000000 or more (Gold 등급이면서 월급이 5000000 이상인 고객)
SELECT * FROM customer WHERE grade = 'Gold' AND salary >= 5000000;

-- 13. Query customers residing in Seoul or Busan (서울 또는 부산 거주 고객)
SELECT * FROM customer WHERE city = 'Seoul' OR city = 'Busan';

-- 14. Query customers with Silver or Gold grade (Silver 또는 Gold 등급 고객)
SELECT * FROM customer WHERE grade = 'Silver' OR grade = 'Gold';

-- 15. Query customers age 30 or over and under 50 (30세 이상 50세 미만인 고객)
SELECT * FROM customer WHERE age >= 30 AND age < 50;

-- 16. Query customers residing in Daegu or Platinum grade (대구 거주 고객 또는 Platinum 등급 고객)
SELECT * FROM customer WHERE city = 'Daegu' OR grade = 'Platinum';

-- 17. Query customers not residing in Seoul (서울 거주가 아닌 고객)
SELECT * FROM customer WHERE NOT city = 'Seoul';

-- 18. Query customers with salary 4000000 or more and Silver grade (월급이 4000000 이상이면서 Silver 등급인 고객)
SELECT * FROM customer WHERE salary >= 4000000 AND grade = 'Silver';

-- 19. Query customers age 35 or over residing in Seoul (35세 이상인 고객 중 서울 거주 고객)
SELECT * FROM customer WHERE age >= 35 AND city = 'Seoul';

-- 20. Query Gold grade customers with salary 6000000 or more (Gold 등급이면서 6000000 이상의 월급 고객)
SELECT * FROM customer WHERE grade = 'Gold' AND salary >= 6000000;

-- =====================================================
-- 3-3. IN, BETWEEN, LIKE Practice (IN, BETWEEN, LIKE 실습)
-- =====================================================
-- Practice 4-21~4-30: IN, BETWEEN, LIKE Operators (IN, BETWEEN, LIKE 연산자)

-- 21. Query customers residing in Seoul, Busan, or Daegu (서울, 부산, 대구에 거주하는 고객)
SELECT * FROM customer WHERE city IN ('Seoul', 'Busan', 'Daegu');

-- 22. Query customers with Gold or Platinum grade (Gold 또는 Platinum 등급인 고객)
SELECT * FROM customer WHERE grade IN ('Gold', 'Platinum');

-- 23. Query customers age between 25 and 35 (나이가 25~35세 사이인 고객)
SELECT * FROM customer WHERE age BETWEEN 25 AND 35;

-- 24. Query customers with salary between 3000000 and 5000000 (월급이 3000000~5000000 사이인 고객)
SELECT * FROM customer WHERE salary BETWEEN 3000000 AND 5000000;

-- 25. Query customers with names starting with 'Kim' (이름이 '김'으로 시작하는 고객)
SELECT * FROM customer WHERE name LIKE 'Kim%';

-- 26. Query customers with names containing 'Young' (이름에 '영'을 포함하는 고객)
SELECT * FROM customer WHERE name LIKE '%Young%';

-- 27. Query customers with names ending with 'Ho' (이름이 '호'로 끝나는 고객)
SELECT * FROM customer WHERE name LIKE '%Ho';

-- 28. Query customers with phone numbers starting with '010-4' (휴대폰 번호가 '010-4'로 시작하는 고객)
SELECT * FROM customer WHERE phone LIKE '010-4%';

-- 29. Query customers residing in Seoul or Busan with Gold grade (서울, 부산 거주자이면서 Gold 등급)
SELECT * FROM customer WHERE city IN ('Seoul', 'Busan') AND grade = 'Gold';

-- 30. Query customers age 30 to 45 with salary 4000000 or more (30세 이상 45세 이하이면서 월급이 4000000 이상)
SELECT * FROM customer WHERE age BETWEEN 30 AND 45 AND salary >= 4000000;

-- =====================================================
-- 3-4. NULL Handling and Complex Conditions (NULL 처리 및 복합 조건)
-- =====================================================
-- Practice 4-31~4-40: NULL Handling and Complex Conditions (NULL 처리 및 복합 조건)

-- 31. Query customers with registered phone numbers (휴대폰 번호가 등록된 고객)
SELECT * FROM customer WHERE phone IS NOT NULL;

-- 32. Query customers without phone numbers (휴대폰 번호가 없는 고객)
SELECT * FROM customer WHERE phone IS NULL;

-- 33. Query customers residing in Seoul or Platinum grade (서울 거주자이거나 Platinum 등급인 고객)
SELECT * FROM customer WHERE city = 'Seoul' OR grade = 'Platinum';

-- 34. Query customers with salary less than 3500000 (월급이 3500000 미만인 고객)
SELECT * FROM customer WHERE salary < 3500000;

-- 35. Query customers with salary greater than 5000000 (월급이 5000000 초과인 고객)
SELECT * FROM customer WHERE salary > 5000000;

-- 36. Query customers age 25 to 40 with phone numbers (25세 이상 40세 이하인 고객 중 휴대폰이 있는 고객)
SELECT * FROM customer WHERE age BETWEEN 25 AND 40 AND phone IS NOT NULL;

-- 37. Query customers with Silver or Gold grade and salary 4000000 or more (Silver 또는 Gold 등급이면서 월급이 4000000 이상)
SELECT * FROM customer WHERE grade IN ('Silver', 'Gold') AND salary >= 4000000;

-- 38. Query customers residing in Daegu and age 30 or over (대구 거주하면서 나이가 30세 이상인 고객)
SELECT * FROM customer WHERE city = 'Daegu' AND age >= 30;

-- 39. Query customers with names containing '지' and age 30 or over (이름에 '지'를 포함하는 고객 중 30세 이상)
SELECT * FROM customer WHERE name LIKE '%Ji%' AND age >= 30;

-- 40. Query customers with Platinum grade or salary 6000000 or more (Platinum 등급이거나 월급이 6000000 이상인 고객)
SELECT * FROM customer WHERE grade = 'Platinum' OR salary >= 6000000;
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the concepts of AND and OR operators and their priority, and explain with specific examples why parentheses must be used correctly when writing complex conditional expressions.

AND와 OR 연산자의 개념과 우선순위를 설명하고, 복합 조건식을 작성할 때 괄호를 올바르게 사용해야 하는 이유를 구체적인 예시를 들어 설명하세요.

**Assignment 2**: Explain the differences between IN operator and OR operator, and discuss the readability improvement effect when using IN.

IN 연산자와 OR 연산자의 차이점을 설명하고, IN을 사용했을 때의 가독성 개선 효과를 논의하세요.

**Assignment 3**: Explain the differences between % and _ wildcard characters of the LIKE operator, and provide practical examples using each.

LIKE 연산자의 와일드카드 문자인 %와 _의 차이를 설명하고, 각각을 사용하는 실무 예시를 제시하세요.

**Assignment 4**: Explain what NULL values are and clearly describe the differences between IS NULL and = NULL.

NULL 값이 무엇인지 설명하고, IS NULL과 = NULL의 차이점을 명확히 서술하세요.

**Assignment 5**: Explain methods for composing conditional expressions considering performance when writing complex WHERE clauses, and present principles for writing efficient queries.

복합 WHERE 절을 작성할 때 성능을 고려한 조건식 구성 방법을 설명하고, 효율적인 쿼리 작성의 원칙을 제시하세요.

**Submission Format**: Word or PDF document (1-2 pages)

---

### Practical Assignments

**Assignment 1**: Write a SQL statement to query customers residing in Seoul and age 30 or over from the customer table, and present the results.

customer 테이블에서 서울 거주하면서 나이가 30세 이상인 고객을 조회하는 SQL 문을 작성하고 결과를 제시하세요.

**Assignment 2**: Write a query to query Gold grade customers with salary 4000000 or more.

월급이 4000000원 이상인 Gold 등급 고객을 조회하는 쿼리를 작성하세요.

**Assignment 3**: Write a SQL statement to query customers without phone numbers.

휴대폰 번호가 없는 고객을 조회하는 SQL 문을 작성하세요.

**Assignment 4**: Query customers residing in Busan or Daegu using the IN operator.

부산 또는 대구 거주 고객을 IN 연산자를 사용하여 조회하세요.

**Assignment 5**: Execute all queries provided from Practice 4-1 to 4-40 in Part 3 directly and attach screenshots of each query result.

Part 3의 실습 4-1부터 4-40까지 제공된 모든 쿼리를 직접 실행하고, 각 쿼리의 결과를 스크린샷으로 첨부하세요.

**Submission Format**: SQL file (Ch4_WHERE_Practice_[StudentID].sql) and screenshots

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
