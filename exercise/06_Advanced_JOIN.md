# Chapter 6. Advanced JOIN - Practice Problems

Dear students! After completing Chapter 6, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

6장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 6, you should understand the following:

- Difference and usage of LEFT JOIN and RIGHT JOIN (LEFT JOIN과 RIGHT JOIN의 차이와 사용)
- Self Join (joining same table with itself) (Self Join - 같은 테이블 자신과 JOIN)
- FULL OUTER JOIN MySQL implementation (LEFT + RIGHT + UNION) (FULL OUTER JOIN의 MySQL 구현)
- Multiple table JOIN (3 or more tables) (3개 이상 테이블 다중 JOIN)
- JOIN performance optimization (JOIN의 성능 최적화)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is the basic characteristic of RIGHT JOIN? (RIGHT JOIN의 기본 특징은?)

- ① Include all rows from left table (왼쪽 테이블의 모든 행 포함)
- ② Include all rows from right table (오른쪽 테이블의 모든 행 포함)
- ③ Only rows matching both tables (양쪽 테이블 모두에 매칭되는 행만)
- ④ Right table allows NULL only (오른쪽 테이블만 NULL 허용)

---

**Question 2** What is the concept of Self Join? (Self Join의 개념은?)

- ① Connect two different tables (두 개의 다른 테이블을 연결)
- ② Use same table twice to connect with itself (같은 테이블을 두 번 사용하여 자신과 연결)
- ③ Copy one table multiple times (한 테이블을 여러 번 복사)
- ④ Connect two databases (두 개의 데이터베이스를 연결)

---

**Question 3** What is FULL OUTER JOIN? (FULL OUTER JOIN은?)

- ① MySQL provides it natively (MySQL에서 기본 제공됨)
- ② MySQL doesn't support, implement with LEFT JOIN + RIGHT JOIN + UNION (MySQL에서는 지원 안 하며 LEFT JOIN + RIGHT JOIN + UNION으로 구현)
- ③ Execute LEFT JOIN and RIGHT JOIN sequentially (LEFT JOIN과 RIGHT JOIN을 순서대로 실행)
- ④ Combine all data from both tables (양쪽 테이블의 모든 데이터를 하나로 합침)

---

**Question 4** In which situation is Self Join needed? (다음 중 Self Join이 필요한 경우는?)

- ① Connect two different tables (서로 다른 두 테이블 연결)
- ② Express relationship between employee and manager (직원과 그 직원의 상급자 관계 표현)
- ③ Query multiple tables simultaneously (여러 테이블을 동시에 조회)
- ④ Sort data (데이터를 정렬할 때)

---

**Question 5** When RIGHT JOIN has no data in right table, result is? (RIGHT JOIN에서 오른쪽 테이블의 데이터가 없을 때 결과는?)

- ① Row excluded from results (해당 행은 결과에서 제외)
- ② Right table column shown as NULL (오른쪽 테이블의 컬럼이 NULL로 표시)
- ③ Left data displayed repeatedly (왼쪽 데이터만 반복해서 표시)
- ④ Error occurs (오류 발생)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** To use Self Join expressing employee and manager relationship? (Self Join을 사용하여 직원과 관리자를 표현하려면?)

```sql
① SELECT e1.name, e2.name
   FROM employee e1
   LEFT JOIN employee e2 ON e1.manager_id = e2.employee_id;

② SELECT e1.name, e2.name
   FROM employee e1
   JOIN employee e2 ON e1.manager_id = e2.manager_id;

③ SELECT e1.name FROM employee e1
   WHERE e1.manager_id IS NOT NULL;
```

- ① Correct (employee and their manager) (올바름 - 직원과 그 관리자)
- ② Correct (colleagues with same manager) (올바름 - 같은 관리자인 동료)
- ③ Correct (employees with manager) (올바름 - 관리자가 있는 직원)
- ④ Both ① and ② are correct (①과 ②가 올바름)

---

**Question 7** Which to use between LEFT and RIGHT JOIN for this situation? (다음 상황에서 LEFT JOIN과 RIGHT JOIN 중 어느 것을 사용?)

"Query all departments and employees in each department, including departments without employees"

(모든 부서와 각 부서에 속한 직원을 조회하되, 직원이 없는 부서도 포함)

```sql
① SELECT d.dept_name, e.name
   FROM department d
   LEFT JOIN employee e ON d.dept_id = e.dept_id;

② SELECT d.dept_name, e.name
   FROM employee e
   RIGHT JOIN department d ON d.dept_id = e.dept_id;
```

- ① Correct (department is reference) (올바름 - 부서가 기준)
- ② Correct (same meaning) (올바름 - 같은 의미)
- ③ Both ① and ② are correct (①과 ②가 모두 올바름)
- ④ Both are wrong (둘 다 잘못됨)

---

**Question 8** To implement FULL OUTER JOIN with LEFT JOIN and RIGHT JOIN? (FULL OUTER JOIN을 LEFT JOIN과 RIGHT JOIN으로 구현하려면?)

- ① LEFT JOIN only (LEFT JOIN만 사용)
- ② RIGHT JOIN only (RIGHT JOIN만 사용)
- ③ LEFT JOIN + RIGHT JOIN + UNION (removes duplicates) (LEFT JOIN + RIGHT JOIN + UNION - 중복 제거)
- ④ LEFT JOIN + RIGHT JOIN + UNION ALL (includes all rows) (LEFT JOIN + RIGHT JOIN + UNION ALL - 모든 행)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Important consideration when LEFT JOIN 3 or more tables? (3개 이상 테이블을 LEFT JOIN할 때 주의할 점은?)

```
SELECT *
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id
LEFT JOIN salary_grades sg ON e.salary BETWEEN sg.min_salary AND sg.max_salary;
```

- ① Each LEFT JOIN can increase number of rows (각 LEFT JOIN이 행 수를 증가시킬 수 있음)
- ② Must clarify join conditions to prevent duplication (조인 조건을 명확히 해야 중복 방지)
- ③ Number of NULL values may increase (NULL 값이 증가할 수 있음)
- ④ All correct (모두 맞음)

---

**Question 10** Most important factor for JOIN performance? (JOIN의 성능을 고려할 때 가장 중요한 요소는?)

- ① Table size (테이블의 크기)
- ② Join condition has primary/foreign key with index (조인 조건이 기본키/외래키이고 인덱스가 있는지 여부)
- ③ JOIN type (INNER vs LEFT) (JOIN 타입)
- ④ Number of functions used (사용하는 함수의 개수)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain relationship between LEFT JOIN and RIGHT JOIN, and how to convert between them for same results. (LEFT JOIN과 RIGHT JOIN의 관계를 설명하고, 같은 결과를 얻기 위해 LEFT JOIN과 RIGHT JOIN을 어떻게 변환하는지 설명하시오.)

---

**Question 12** Explain Self Join concept and provide 3 or more practical cases needed. (Self Join의 개념을 설명하고, 실무에서 필요한 경우를 3가지 이상 제시하시오.)

---

**Question 13** Explain situation needing FULL OUTER JOIN and how to implement in MySQL. (FULL OUTER JOIN이 필요한 상황을 설명하고, MySQL에서 이를 구현하는 방법을 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain impact of multiple LEFT JOINs on result row count and methods to avoid unexpected results. (여러 LEFT JOIN을 연결할 때 각 JOIN이 결과 행 수에 미치는 영향을 설명하고, 예상 외의 결과를 피하기 위한 방법을 제시하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain factors affecting JOIN performance (indexes, join order, join conditions) and optimization methods for each. (JOIN의 성능에 영향을 미치는 요소들을 설명하고, 각각의 최적화 방법을 제시하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch6_advanced CHARACTER SET utf8mb4;
USE ch6_advanced;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    dept_id INT,
    manager_id INT,
    salary DECIMAL(10, 2)
);

-- Create departments table (부서 테이블 생성)
CREATE TABLE departments (
    dept_id INT PRIMARY KEY AUTO_INCREMENT,
    department_name VARCHAR(50) NOT NULL,
    location VARCHAR(50)
);

-- Create salary_grades table (급여 등급 테이블 생성)
CREATE TABLE salary_grades (
    grade CHAR(1) PRIMARY KEY,
    min_salary DECIMAL(10, 2),
    max_salary DECIMAL(10, 2)
);

-- Insert employees data (직원 데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 1, NULL, 5000000),
(2, 'Sarah Lee', 1, 1, 4000000),
(3, 'David Park', 2, 1, 4500000),
(4, 'Emily Choi', 2, 3, 3500000),
(5, 'Michael Kang', 3, 1, 4200000),
(6, 'Lisa Choi', 3, 5, 3800000),
(7, 'John Park', 1, 1, 3200000);

-- Insert departments data (부서 데이터 입력)
INSERT INTO departments VALUES
(1, 'Sales', 'Seoul'),
(2, 'Technology', 'Daejeon'),
(3, 'HR', 'Seoul'),
(4, 'Finance', 'Busan');

-- Insert salary_grades data (급여 등급 데이터 입력)
INSERT INTO salary_grades VALUES
('A', 5000000, 6000000),
('B', 4000000, 4999999),
('C', 3000000, 3999999),
('D', 2000000, 2999999);

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
SELECT * FROM departments;
SELECT * FROM salary_grades;
```

Submission: Screenshot showing all three tables data (제출: 세 테이블의 데이터가 모두 보이는 스크린샷)

---

**Question 17** LEFT JOIN employees and departments and query the following. (employees와 departments를 LEFT JOIN하여 다음을 조회하시오.)

```sql
-- 1. All employees and department info (모든 직원과 부서 정보)
SELECT e.name, d.department_name, d.location
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;

-- 2. All departments and employee count (including departments without employees) (모든 부서와 직원 수 - 직원 없는 부서도 포함)
SELECT d.department_name, COUNT(e.employee_id) AS employee_count
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_id, d.department_name;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Use Self Join and query the following. (Self Join을 사용하여 다음을 조회하시오.)

```sql
-- 1. Each employee and their manager (각 직원과 상급자명)
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.employee_id;

-- 2. All employee pairs in same department (같은 부서의 모든 직원 쌍)
SELECT e1.name, e2.name
FROM employees e1
JOIN employees e2 ON e1.dept_id = e2.dept_id
WHERE e1.employee_id < e2.employee_id;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

**Question 19** JOIN 3 tables and query the following. (3개 테이블을 JOIN하여 다음을 조회하시오.)

```sql
-- 1. Employee, department, location, salary, grade (직원명, 부서명, 위치, 급여, 급여등급)
SELECT e.name, d.department_name, d.location, e.salary, sg.grade
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id
LEFT JOIN salary_grades sg ON e.salary BETWEEN sg.min_salary AND sg.max_salary;

-- 2. Department average salary (부서별 평균 급여)
SELECT d.department_name, AVG(e.salary) AS avg_salary
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_id, d.department_name;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute advanced JOIN queries. (다음의 고급 JOIN 쿼리를 작성하고 실행하시오.)

```
Requirements:

1. FULL OUTER JOIN implementation (LEFT + RIGHT + UNION)
   - Show all departments and employees (unassigned employees too)

2. Using NOT EXISTS
   - Query departments without employees

3. Employees count by salary grade
   - Use LEFT JOIN to include employees without grade

4. 2 or more complex JOIN queries:
   - Combine INNER JOIN and LEFT JOIN
   - Use with GROUP BY and HAVING
   - Apply sorting and limiting

Submission:
   - SQL code for each query
   - Execution result screenshot for each query

요구사항:

1. FULL OUTER JOIN 구현 (LEFT + RIGHT + UNION)
   - 모든 부서와 모든 직원 표시 (배치되지 않은 직원도)

2. NOT EXISTS를 사용한 쿼리
   - 직원이 배치되지 않은 부서 조회

3. 급여 등급별 직원 수
   - LEFT JOIN으로 등급이 없는 직원도 포함

4. 자유로운 복합 JOIN 쿼리 2개 이상:
   - INNER JOIN과 LEFT JOIN 조합
   - GROUP BY와 HAVING 활용
   - 정렬 및 제한

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
|    1    |   ②   | RIGHT JOIN includes all rows from right table (오른쪽 테이블 모두 포함)                 |
|    2    |   ②   | Self Join uses same table twice to connect with itself (같은 테이블을 자신과 연결)      |
|    3    |   ②   | MySQL doesn't support FULL OUTER, use LEFT+RIGHT+UNION (MySQL은 FULL OUTER JOIN 미지원) |
|    4    |   ②   | Express hierarchy (employee-manager) with Self Join (계층 관계 표현에 Self Join 사용)   |
|    5    |   ②   | RIGHT JOIN shows right table columns as NULL if no data (오른쪽 데이터 없으면 NULL)     |
|    6    |   ①   | Correct (department is reference) (①가 올바름)                                         |
|    7    |   ③   | ① and ② have same meaning (department as reference) (①②가 같은 의미)                |
|    8    |   ③   | FULL OUTER = LEFT + RIGHT + UNION (remove duplicates) (중복 제거)                       |
|    9    |   ④   | All are important considerations (모두 맞음)                                            |
|    10    |   ②   | Indexes and PK-FK relationship most important (인덱스와 기본키-외래키가 가장 중요)      |

---

## Short Answer Model Answers (5 Questions)

### Question 11: LEFT JOIN and RIGHT JOIN Relationship

**Model Answer (모범 답안):**

```
Relationship between LEFT JOIN and RIGHT JOIN:

LEFT JOIN A LEFT JOIN B: All A data + B matching
RIGHT JOIN B RIGHT JOIN A: All B data + A matching
- Only table order changes = same meaning

Conversion example:

LEFT JOIN approach:
SELECT * FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id;

RIGHT JOIN conversion:
SELECT * FROM employees e
RIGHT JOIN departments d ON d.dept_id = e.dept_id;

Result: Identical (department as reference, employee can be NULL)
```

---

### Question 12: Self Join Practical Cases

**Model Answer (모범 답안):**

```
Self Join practical cases:

1. Employee-Manager relationship
   SELECT e.name, m.name
   FROM employees e
   LEFT JOIN employees m ON e.manager_id = m.employee_id;
   → Show employee's superior

2. Category-Subcategory relationship
   SELECT c1.category, c2.category
   FROM categories c1
   JOIN categories c2 ON c1.category_id = c2.parent_category_id;
   → Show parent and child categories

3. Product-Related product relationship
   SELECT p1.product_name, p2.product_name
   FROM products p1
   JOIN product_relations...;
   → Show related products

4. City-City distance
   SELECT c1.city, c2.city, d.distance
   → Show distance between cities
```

---

### Question 13: FULL OUTER JOIN

**Model Answer (모범 답안):**

```
Situation needing FULL OUTER JOIN:
- Compare all data from both tables
- Show all data regardless of matching
- Find mismatches (unassigned employees, departments without employees)

MySQL implementation:

SELECT d.department_name, e.name
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
UNION
SELECT d.department_name, e.name
FROM departments d
RIGHT JOIN employees e ON d.dept_id = e.dept_id;

Result:
- Show all departments (NULL if no employee)
- Show all employees (NULL if no department)
- Remove duplicates (UNION)
```

---

### Question 14: Multiple LEFT JOIN Row Count Impact

**Model Answer (모범 답안):**

```
Problem: Each LEFT JOIN can increase row count

Example:
employee: 10 rows
department: 5 rows
salary_grades: 5 rows

LEFT JOIN impact:
- e and d: max 50 rows (1:N)
- Add sg: max 250 rows

Expected: Each employee 1 row only

Solutions:
1. GROUP BY for aggregation
2. Use DISTINCT
3. Make join conditions more specific
4. Select needed columns before aggregation
```

---

### Question 15: JOIN Performance Optimization

**Model Answer (모범 답안):**

```
Factor 1: Indexes
- Index on join condition columns essential
- Effect: 10-100x speed improvement

Factor 2: Join order
- Higher selectivity table first
- Effect: Reduce rows to process

Factor 3: Join conditions
- Use PK-FK relationships
- Minimize function usage
- Bad: ON YEAR(e.date) = YEAR(d.date)
- Good: ON e.dept_id = d.dept_id

Optimized query:
SELECT e.name, d.department_name
FROM employees e           -- indexed column
LEFT JOIN departments d 
  ON e.dept_id = d.dept_id -- PK-FK
WHERE e.salary > 5000000   -- filter first
ORDER BY e.employee_id;
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Table Creation

**Completion Criteria (완료 기준):**

✅ ch6_advanced database created
✅ employees: 7 employees
✅ departments: 4 departments
✅ salary_grades: 4 grades

---

### Question 17: LEFT JOIN Query

**Expected Result 1 (모든 직원):**

```
name          | department_name | location
Alex Kim      | Sales          | Seoul
Sarah Lee     | Sales          | Seoul
David Park    | Technology     | Daejeon
Emily Choi    | Technology     | Daejeon
Michael Kang  | HR             | Seoul
Lisa Choi     | HR             | Seoul
John Park     | Sales          | Seoul
```

**Expected Result 2 (부서별 직원 수):**

```
department_name | employee_count
Sales          | 3
Technology     | 2
HR             | 2
Finance        | 0
```

---

### Question 18: Self Join

**Expected Result 1:**

```
employee_name | manager_name
Alex Kim      | NULL
Sarah Lee     | Alex Kim
David Park    | Alex Kim
Emily Choi    | David Park
Michael Kang  | Alex Kim
Lisa Choi     | Michael Kang
John Park     | Alex Kim
```

**Expected Result 2:**

```
name1        | name2
Alex Kim     | Sarah Lee
Alex Kim     | John Park
Sarah Lee    | John Park
David Park   | Emily Choi
Michael Kang | Lisa Choi
```

---

### Question 19: 3-Table JOIN

**Model Answer (모범 답안):**

```sql
-- Query 1: Employee details with grade
SELECT e.name, d.department_name, d.location, e.salary, sg.grade
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id
LEFT JOIN salary_grades sg ON e.salary BETWEEN sg.min_salary AND sg.max_salary;

-- Query 2: Department average salary
SELECT d.department_name, AVG(e.salary) AS avg_salary
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_id, d.department_name;
```

---

### Question 20: Advanced Queries

**Model Answer (모범 답안):**

```sql
-- 1. FULL OUTER JOIN
SELECT COALESCE(d.dept_id, e.dept_id) AS dept_id,
       d.department_name, e.name
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
UNION
SELECT e.dept_id, d.department_name, e.name
FROM departments d
RIGHT JOIN employees e ON d.dept_id = e.dept_id;

-- 2. NOT EXISTS (departments without employees)
SELECT d.department_name
FROM departments d
WHERE NOT EXISTS (
    SELECT 1 FROM employees e
    WHERE e.dept_id = d.dept_id
);

-- 3. Employee count by salary grade
SELECT sg.grade, COUNT(e.employee_id) AS employee_count
FROM salary_grades sg
LEFT JOIN employees e 
  ON e.salary BETWEEN sg.min_salary AND sg.max_salary
GROUP BY sg.grade;

-- 4. Highest salary per department
SELECT d.department_name, e.name, e.salary
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id
WHERE e.salary = (
    SELECT MAX(salary) FROM employees
    WHERE dept_id = e.dept_id
);

-- 5. Above average salary employees
SELECT e.name, e.salary, d.department_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id
WHERE e.salary > (
    SELECT AVG(salary) FROM employees
)
ORDER BY e.salary DESC;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
