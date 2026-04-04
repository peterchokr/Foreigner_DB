# Chapter 4. WHERE Clause - Practice Problems

Dear students! After completing Chapter 4, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

4장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 4, you should understand the following:

- Data filtering using WHERE clause (WHERE 절을 사용한 데이터 필터링)
- Comparison operators (=, !=, <, >, <=, >=) (비교 연산자)
- Logical operators (AND, OR, NOT) (논리 연산자)
- IN, BETWEEN, LIKE operators (IN, BETWEEN, LIKE 연산자)
- NULL value handling (IS NULL, IS NOT NULL) (NULL 값 처리)
- Writing complex conditional expressions (복합 조건식 작성)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is the primary purpose of WHERE clause? (다음 중 WHERE 절의 기본 목적은?)

- ① Sort data (데이터를 정렬함)
- ② Filter rows matching conditions (조건에 맞는 행을 필터링함)
- ③ Change data type (데이터 타입을 변경함)
- ④ Limit number of rows (행의 개수를 제한함)

---

**Question 2** What is the difference between != and <> comparison operators? (비교 연산자 != 와 <> 의 차이는?)

- ① != doesn't work (!=는 작동 안 함)
- ② <> doesn't work (<>는 작동 안 함)
- ③ Both mean "not equal" (둘 다 같은 의미 - 같지 않다)
- ④ Completely different functionality (기능이 완전히 다름)

---

**Question 3** Which SQL correctly checks for NULL value? (다음 중 NULL 값을 올바르게 검사하는 SQL은?)

- ① WHERE phone = NULL;
- ② WHERE phone != NULL;
- ③ WHERE phone IS NULL;
- ④ WHERE phone <> NULL;

---

**Question 4** What is the main advantage of IN operator? (IN 연산자의 주요 장점은?)

- ① Faster execution speed (더 빠른 실행 속도)
- ② Good readability and concise expression of multiple values (가독성이 좋고 여러 값을 간결하게 표현)
- ③ More accurate search (더 정확한 검색)
- ④ Less memory usage (메모리 사용 감소)

---

**Question 5** What does LIKE '김%' mean? (LIKE '김%' 의 의미는?)

- ① Search exactly '김' only (정확히 '김' 만 검색)
- ② All strings starting with '김' (김으로 시작하는 모든 문자열)
- ③ All strings containing '김' (김을 포함하는 모든 문자열)
- ④ All strings ending with '김' (김으로 끝나는 모든 문자열)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** What is the correct explanation about AND and OR priority? (AND 와 OR의 우선순위에 관한 설명으로 올바른 것은?)

- ① AND and OR have same priority (AND와 OR은 같은 우선순위)
- ② AND executes before OR (AND가 OR보다 먼저 실행됨)
- ③ OR executes before AND (OR이 AND보다 먼저 실행됨)
- ④ Execution only left to right (왼쪽에서 오른쪽으로만 실행됨)

---

**Question 7** What is equivalent to BETWEEN 20 AND 30? (BETWEEN 20 AND 30 은 다음 중 어느 것과 같은가?)

- ① age > 20 AND age > 30
- ② age >= 20 AND age <= 30
- ③ age > 20 AND age < 30
- ④ age >= 20 OR age <= 30

---

**Question 8** In the following query, what is the execution sequence? (다음 쿼리에서 실행 순서는?)

```sql
WHERE city = 'Seoul' AND salary > 5000000 AND position = 'Manager'
```

- ① Execute left to right sequentially (왼쪽에서 오른쪽으로 순차 실행)
- ② Evaluate each condition, all must be true (각 조건을 평가하고 모두 만족해야 TRUE)
- ③ Condition order doesn't matter (조건 순서는 상관없음)
- ④ Execute from highest selectivity condition first (가장 선택도가 높은 조건부터)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Which of the following two queries has better performance? (다음 두 쿼리 중 성능이 더 좋은 것은?)

```
Query A:
WHERE city IN ('Seoul', 'Busan', 'Daegu', 'Daejeon', 'Gwangju')

Query B:
WHERE city = 'Seoul' OR city = 'Busan' OR city = 'Daegu' 
      OR city = 'Daejeon' OR city = 'Gwangju'
```

- ① Query A is faster (more concise) (쿼리 A가 더 빠름 - 더 간결)
- ② Query B is faster (more explicit) (쿼리 B가 더 빠름 - 더 명시적)
- ③ Both queries have same performance (두 쿼리 성능은 같음)
- ④ Depends on situation (상황에 따라 다름)

---

**Question 10** Analyze the situation and choose the most efficient WHERE clause. (다음 상황을 분석하고 가장 효율적인 WHERE 절을 선택하시오.)

"Query employees with salary >= 5,000,000 AND (position = 'Director' OR position = 'Executive'), excluding resigned employees (resign_date IS NOT NULL)"

(급여가 5000000원 이상이면서 직급이 '부장' 또는 '임원'인 직원을 조회하고, 대신 퇴직한 직원(resign_date가 NULL이 아닌)은 제외)

```
① WHERE salary >= 5000000 AND (position = '부장' OR position = '임원')
      AND resign_date IS NULL;

② WHERE salary >= 5000000 AND position IN ('부장', '임원')
      AND resign_date IS NULL;

③ WHERE salary >= 5000000 AND position IN ('부장', '임원')
      AND resign_date IS NOT NULL;
```

- ① Correct (all conditions appropriate) (올바름 - 모든 조건이 적절)
- ② Correct (more concise with IN) (올바름 - IN으로 더 간결)
- ③ Error (resign_date IS NOT NULL means resigned) (오류 - resign_date IS NOT NULL는 퇴직자)
- ④ Both ① and ② are correct (①과 ②가 모두 올바름)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain the execution order of WHERE clause and SELECT. (WHERE 절과 SELECT의 실행 순서를 설명하시오.)

---

**Question 12** Explain why = NULL doesn't work when checking NULL values. (NULL 값을 검사할 때 = NULL이 작동하지 않는 이유를 설명하시오.)

---

**Question 13** Explain the difference between IN and OR operators and provide examples of situations using each. (IN 연산자와 OR 연산자의 차이를 설명하고, 각각을 사용하는 상황을 예시하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain why AND has higher priority than OR, and provide practical examples where parentheses must be used correctly. (AND 연산자의 우선순위가 OR보다 높은 이유를 설명하고, 괄호를 올바르게 사용해야 하는 상황을 실예시로 제시하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain performance optimization methods when writing complex WHERE clauses. (복합 WHERE 절을 작성할 때 고려해야 할 성능 최적화 방법을 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database and table (데이터베이스 생성 및 테이블 생성)
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

-- Insert customer data (고객 데이터 입력)
INSERT INTO customer VALUES
(1, 'Alex Kim', 'Seoul', 35, 'Gold', 5000000, '010-1111-1111'),
(2, 'Sarah Lee', 'Busan', 28, 'Silver', 3500000, '010-2222-2222'),
(3, 'David Park', 'Seoul', 42, 'Gold', 6000000, '010-3333-3333'),
(4, 'Emily Choi', 'Daegu', 25, 'Silver', 3000000, '010-4444-4444'),
(5, 'Michael Kang', 'Seoul', 38, 'Platinum', 7500000, NULL);

-- Query all data (모든 데이터 조회)
SELECT * FROM customer;
```

Submission: Screenshot showing all 5 customers inserted (1 screenshot) (제출: 고객 테이블에 5명의 고객 정보가 모두 입력된 스크린샷 1장)

---

**Question 17** Perform the following queries on customer table and verify results. (customer 테이블에서 다음을 수행하고 결과를 확인하시오.)

```sql
-- 1. Query customers living in Seoul only (서울 거주 고객만 조회)
SELECT * FROM customer WHERE city = 'Seoul';

-- 2. Query customers age 30 or older (30세 이상 고객 조회)
SELECT * FROM customer WHERE age >= 30;

-- 3. Query customers with salary 4,000,000 or higher (월급 4000000원 이상 고객 조회)
SELECT * FROM customer WHERE salary >= 4000000;
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Perform the following queries on customer table. (customer 테이블에서 다음 조회를 수행하시오.)

```sql
-- 1. Customers living in Seoul AND age >= 30 (서울 거주 AND 30세 이상 고객)
SELECT * FROM customer 
WHERE city = 'Seoul' AND age >= 30;

-- 2. Gold grade AND salary >= 4,000,000 (Gold 등급 AND 월급 4000000원 이상)
SELECT * FROM customer 
WHERE grade = 'Gold' AND salary >= 4000000;

-- 3. Customers from Busan OR Daegu (using IN) (부산 OR 대구 거주 고객 - IN 사용)
SELECT * FROM customer 
WHERE city IN ('Busan', 'Daegu');
```

Submission: Screenshot showing all 3 query results (제출: 3개 쿼리 결과가 모두 보이는 스크린샷)

---

**Question 19** Perform the following analysis on customer table. (customer 테이블에서 다음 분석을 수행하시오.)

```
Questions:
1. Write SQL to query customers without phone number
2. Write SQL to filter by salary range (e.g., 3,000,000 - 5,000,000)
3. Write SQL to query customers whose name starts with 'Alex'
4. Provide screenshot of each query result

질문:
1. 휴대폰 번호가 없는 고객을 조회하는 SQL 작성
2. 금액 범위로 필터링 (예: 3000000 이상 5000000 이하) SQL 작성
3. 이름이 '김'으로 시작하는 고객을 조회하는 SQL 작성
4. 각 쿼리의 결과를 스크린샷으로 제시

Submission: 3 SQL codes + execution result screenshot (3개 SQL 코드 + 실행 결과 스크린샷)
```

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex WHERE clauses using customer table. (customer 테이블을 사용하여 다음 복합 WHERE 절을 작성하고 실행하시오.)

```
Requirements:
1. Customers living in Seoul AND (Gold OR Platinum grade)
   SQL: WHERE city = 'Seoul' AND (grade = 'Gold' OR grade = 'Platinum')
        또는 WHERE city = 'Seoul' AND grade IN ('Gold', 'Platinum')

2. (Age >= 30) AND (living in Busan OR Seoul) AND (salary >= 4,000,000)
   Write SQL

3. Customers with NO phone number AND salary >= 5,000,000
   Write SQL

4. Write 2 or more additional WHERE clauses:
   - Use NOT operator
   - Use LIKE pattern
   - Combine 3 or more AND/OR

Submission:
   - SQL code for each query
   - Execution result screenshot for each query

요구사항:
1. 서울 거주 AND (Gold 또는 Platinum 등급)인 고객
   SQL: WHERE city = 'Seoul' AND (grade = 'Gold' OR grade = 'Platinum')
        또는 WHERE city = 'Seoul' AND grade IN ('Gold', 'Platinum')

2. (30세 이상) AND (부산 또는 서울 거주) AND (월급 4000000원 이상)
   SQL 작성

3. 전화번호가 없으면서 월급이 5000000원 이상인 고객
   SQL 작성

4. 다음 조건을 만족하는 자유로운 WHERE 절 2개 이상 추가 작성:
   - NOT 연산자 활용
   - LIKE 패턴 활용
   - 3개 이상의 AND/OR 조합

제출:
   - 각 쿼리의 SQL 코드
   - 각 쿼리의 실행 결과 스크린샷
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                                                          |
| :------: | :----: | :------------------------------------------------------------------------------------------------------------------- |
|    1    |   ②   | WHERE filters rows matching conditions (WHERE는 조건에 맞는 행을 필터링)                                             |
|    2    |   ③   | != and <> both mean "not equal" (둘 다 같은 의미 - 같지 않다)                                                        |
|    3    |   ③   | NULL is checked only with IS NULL / IS NOT NULL (NULL은 IS NULL/IS NOT NULL로만 검사)                                |
|    4    |   ②   | IN concisely expresses multiple values with good readability (IN은 여러 값을 간결하게 표현)                          |
|    5    |   ②   | % represents 0 or more characters (% 는 0개 이상의 문자를 의미)                                                      |
|    6    |   ②   | AND has higher priority than OR (AND가 OR보다 우선순위가 높음)                                                       |
|    7    |   ②   | BETWEEN 20 AND 30 = >= 20 AND <= 30                                                                                  |
|    8    |   ③   | AND conditions are evaluated regardless of order, all must be true (AND 조건들은 순서와 상관없이 모두 만족해야 TRUE) |
|    9    |  ③  | Both possible but IN is more concise (둘 다 가능하지만 IN이 더 간결)                                                 |
|    10    |   ④   | Both ① and ② are correct (③ has inverted condition) (①②가 모두 올바름)                                          |

---

## Short Answer Model Answers (5 Questions)

### Question 11: WHERE and SELECT Execution Order

**Model Answer (모범 답안):**

```
1. FROM: Select table (테이블 선택)
2. WHERE: Filter rows by conditions (조건으로 행 필터링)
3. SELECT: Select desired columns from filtered rows (필터된 행에서 원하는 열만 선택)
4. ORDER BY: Sort results (결과 정렬 - 있으면)
5. LIMIT: Limit number of rows (행 수 제한 - 있으면)

Example: SELECT name, salary FROM customer WHERE city = 'Seoul'

Execution order: 
customer table → filter city='Seoul' rows → select name, salary columns
```

---

### Question 12: Why = NULL Doesn't Work

**Model Answer (모범 답안):**

```
Why = NULL doesn't work:
- NULL is not a value, it's a state (NULL은 값이 아니라 상태)
- NULL = NULL returns UNKNOWN, not TRUE/FALSE (NULL = NULL의 결과는 TRUE/FALSE가 아니라 UNKNOWN)
- SQL excludes UNKNOWN rows from SELECT results (SQL은 UNKNOWN 행을 SELECT 결과에서 제외)

Correct checking:
- IS NULL: Check NULL state (NULL 상태 확인)
- IS NOT NULL: Check non-NULL case (NULL이 아닌 경우 확인)

Example:
Wrong: WHERE phone = NULL; → Returns 0 rows
Correct: WHERE phone IS NULL; → Returns customers with no phone
```

---

### Question 13: IN vs OR

**Model Answer (모범 답안):**

```
IN Operator (IN 연산자):
- Syntax: WHERE city IN ('Seoul', 'Busan', 'Daegu')
- Advantage: Concise, good readability (간결하고 가독성 좋음)
- Use: When 3+ values (값이 3개 이상일 때)

OR Operator (OR 연산자):
- Syntax: WHERE city = 'Seoul' OR city = 'Busan' OR city = 'Daegu'
- Advantage: Explicit, flexible (명시적이고 유연)
- Use: When 1-2 values (값이 1-2개일 때)

Comparison (비교):
- IN: Better readability, easier optimization
- OR: Can express each condition clearly

Practical examples (실무 예시):
- 4+ cities: WHERE city IN ('Seoul', 'Busan', 'Daegu', 'Daejeon')
- Simple 2 conditions: WHERE grade = 'Gold' OR grade = 'Silver'
```

---

### Question 14: AND Priority and Parentheses

**Model Answer (모범 답안):**

```
Why AND has higher priority:
- Evaluates more specific conditions first (더 구체적인 조건을 먼저 평가)
- Makes data filtering more efficient (데이터 필터링을 더 효율적으로 수행)
- Gets intended results in complex conditions (복합 조건에서 의도한 결과를 얻음)

Situations requiring parentheses (괄호가 필요한 상황):

Wrong example:
WHERE city = 'Seoul' OR city = 'Busan' AND salary > 5000000;
Execution: (city = 'Seoul') OR (city = 'Busan' AND salary > 5000000)
→ All Seoul people + high-income Busan people (잘못된 결과)

Correct example:
WHERE (city = 'Seoul' OR city = 'Busan') AND salary > 5000000;
→ High-income people from Seoul or Busan (의도한 결과)

Conclusion: Always use parentheses when mixing OR and AND (OR과 AND를 섞을 때는 반드시 괄호로 명시)
```

---

### Question 15: Complex WHERE Clause Performance Optimization

**Model Answer (모범 답안):**

```
Optimization Method 1: Higher selectivity condition first (선택도가 높은 조건 먼저)
WHERE salary > 5000000 AND city = 'Seoul';
(Filtering by salary first reduces rows to process)

Optimization Method 2: Use indexes (인덱스 활용)
WHERE indexed_column = value AND other_column = value;
(Include indexed columns in conditions)

Optimization Method 3: Minimize function usage (함수 사용 최소화)
Good: WHERE hire_date >= '2024-01-01'
Bad: WHERE YEAR(hire_date) = 2024 (functions reduce optimization)

Optimization Method 4: Remove unnecessary OR (불필요한 OR 제거)
WHERE city IN ('Seoul', 'Busan') ← Use IN
Instead of:
WHERE city = 'Seoul' OR city = 'Busan' ← Avoid OR repetition

Optimization Method 5: Match data types (데이터 타입 일치)
WHERE salary = 5000000 (type match)
Instead of:
WHERE salary = '5000000' (implicit conversion occurs)
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Customer Table Creation and Data Entry

**Completion Criteria (완료 기준):**

✅ ch4_filtering database created (ch4_filtering 데이터베이스 생성됨)
✅ customer table created (7 columns) (customer 테이블 생성됨)
✅ 5 customers data inserted (5명의 고객 데이터 입력됨)
✅ SELECT * FROM customer executed (SELECT * FROM customer 실행됨)

**Expected result (예상 결과):**

```
customer_id | name         | city   | age | grade     | salary  | phone
1           | Alex Kim     | Seoul  | 35  | Gold      | 5000000 | 010-1111-1111
2           | Sarah Lee    | Busan  | 28  | Silver    | 3500000 | 010-2222-2222
3           | David Park   | Seoul  | 42  | Gold      | 6000000 | 010-3333-3333
4           | Emily Choi   | Daegu  | 25  | Silver    | 3000000 | 010-4444-4444
5           | Michael Kang | Seoul  | 38  | Platinum  | 7500000 | NULL
```

---

### Question 17: Customer Table Basic WHERE Queries

**Completion Criteria (완료 기준):**

✅ Seoul residents: 3 people (Alex Kim, David Park, Michael Kang) (3명)
✅ Age >= 30: 3 people (Alex Kim, David Park, Michael Kang) (3명)
✅ Salary >= 4,000,000: 3 people (Alex Kim, David Park, Michael Kang) ※ Sarah Lee is 3,500,000 (3명)

---

### Question 18: AND, OR Condition Queries

**Completion Criteria (완료 기준):**

✅ Seoul AND age >= 30: Alex Kim, David Park, Michael Kang (3 people) (3명)
✅ Gold AND salary >= 4,000,000: Alex Kim, David Park (2 people) (2명)
✅ Busan OR Daegu: Sarah Lee, Emily Choi (2 people) (2명)

---

### Question 19: NULL, BETWEEN, LIKE Queries

**Model Answer (모범 답안):**

```sql
-- 1. Phone number NULL
SELECT * FROM customer WHERE phone IS NULL;
Result: Michael Kang (1 person)

-- 2. BETWEEN (3,000,000 - 5,000,000)
SELECT * FROM customer 
WHERE salary BETWEEN 3000000 AND 5000000;
Result: Sarah Lee, Emily Choi, Alex Kim (3 people)

-- 3. LIKE name starts with 'Alex'
SELECT * FROM customer WHERE name LIKE 'Alex%';
Result: Alex Kim (1 person)
```

---

### Question 20: Complex WHERE Clauses

**Model Answer (모범 답안):**

```sql
-- 1. Seoul AND (Gold OR Platinum)
SELECT * FROM customer 
WHERE city = 'Seoul' AND (grade = 'Gold' OR grade = 'Platinum');

Result: Alex Kim, David Park, Michael Kang (3 people)

-- Or using IN:
SELECT * FROM customer 
WHERE city = 'Seoul' AND grade IN ('Gold', 'Platinum');

-- 2. (Age >= 30) AND (Busan/Seoul) AND (salary >= 4,000,000)
SELECT * FROM customer 
WHERE age >= 30 AND city IN ('Busan', 'Seoul') AND salary >= 4000000;

Result: Alex Kim, David Park, Michael Kang (3 people)

-- 3. Phone NULL AND salary >= 5,000,000
SELECT * FROM customer 
WHERE phone IS NULL AND salary >= 5000000;

Result: Michael Kang (1 person)

-- Additional Query 1: Using NOT
SELECT * FROM customer 
WHERE NOT grade = 'Silver' AND NOT city = 'Daegu';

-- Additional Query 2: Using LIKE
SELECT * FROM customer 
WHERE name LIKE 'A%' OR name LIKE '%ng';

-- Additional Query 3: Complex conditions
SELECT * FROM customer 
WHERE (city = 'Seoul' OR city = 'Busan') 
AND age >= 25 AND salary < 6000000;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
