# Chapter 10. Views and Stored Procedures - Practice Problems

Dear students! After completing Chapter 10, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

10장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 10, you should understand the following:

- View concept and creation (뷰의 개념과 생성)
- View utilization and advantages/disadvantages (뷰의 활용과 장단점)
- View modification and deletion (뷰 수정과 삭제)
- Stored procedure concept and syntax (저장프로시저의 개념과 문법)
- Procedure parameters (IN, OUT, INOUT) (매개변수)
- Procedure execution and management (실행과 관리)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is most important characteristic of view? (뷰의 가장 중요한 특징은?)

- ① Store actual data (실제 데이터를 저장함)
- ② Virtual table not storing actual data (가상 테이블로 실제 데이터를 저장하지 않음)
- ③ Always faster than table (테이블보다 항상 빠름)
- ④ Modify original table (원본 테이블을 변경함)

---

**Question 2** Basic syntax for creating view? (뷰를 생성하는 기본 문법은?)

- ① CREATE TABLE view_name AS SELECT ...;
- ② CREATE VIEW view_name AS SELECT ...;
- ③ CREATE VIEW view_name FROM SELECT ...;
- ④ MAKE VIEW view_name AS SELECT ...;

---

**Question 3** Which defines stored procedure correctly? (저장프로시저의 정의로 옳은 것은?)

- ① Reusable SQL routine stored in database (데이터베이스에 저장되는 재사용 가능한 SQL 루틴)
- ② SQL statement executed only once (한 번만 실행되는 SQL 문)
- ③ Query unable to include conditionals (조건문을 포함할 수 없는 쿼리)
- ④ Executed only from client application (클라이언트 애플리케이션에서만 실행됨)

---

**Question 4** What is role of IN parameter in stored procedure? (저장프로시저의 IN 매개변수의 역할은?)

- ① Accept input values only (입력값만 받음)
- ② Return output values only (출력값만 반환함)
- ③ Both input and output possible (입력과 출력 모두 가능)
- ④ Execute without parameters (매개변수 없이 실행)

---

**Question 5** How to execute stored procedure? (저장프로시저를 실행하는 방법은?)

- ① SELECT procedure_name;
- ② RUN procedure_name;
- ③ CALL procedure_name(parameters);
- ④ EXECUTE procedure_name;

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which is NOT condition for updatable view? (수정 가능한 뷰의 조건으로 옳지 않은 것은?)

- ① Single table based (단일 테이블 기반)
- ② GROUP BY can be included (GROUP BY 포함 가능)
- ③ No JOIN (JOIN 미포함)
- ④ No DISTINCT (DISTINCT 미포함)

---

**Question 7** Which example uses OUT parameter correctly? (저장프로시저의 OUT 매개변수 사용 예는?)

```sql
① CREATE PROCEDURE GetCount (IN dept_id INT)
② CREATE PROCEDURE GetCount (OUT count INT)
③ CREATE PROCEDURE GetCount (INOUT salary DECIMAL)
```

- ① Input only (입력 전용)
- ② Output only (this uses OUT) (출력 전용 - OUT 사용)
- ③ Input/output combined (입출력 겸용)
- ④ Both ① and ② possible (①과 ② 모두 가능)

---

**Question 8** Correct syntax to delete view? (뷰를 삭제하는 올바른 문법은?)

- ① DELETE VIEW view_name;
- ② DROP VIEW view_name;
- ③ REMOVE VIEW view_name;
- ④ DROP TABLE view_name;

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Most important reason to use view? (뷰를 사용하는 가장 중요한 이유는?)

- ① Always better performance (항상 성능이 더 좋음)
- ② Provide data security and abstraction (데이터 보안과 추상화 제공)
- ③ Save storage space (저장 공간 절약)
- ④ UPDATE possible in all operations (모든 연산에서 UPDATE 가능)

---

**Question 10** Biggest difference between view and stored procedure? (저장프로시저와 뷰의 가장 큰 차이는?)

- ① View for query only, procedure for logic (뷰는 조회만, 프로시저는 로직 구현)
- ② Procedure for query only, view for modification (프로시저는 조회만, 뷰는 데이터 수정)
- ③ Both same functionality (둘 다 같은 기능)
- ④ View fast, procedure slow (뷰는 빠르고 프로시저는 느림)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Define view and explain why views are necessary. (뷰의 정의와 뷰가 필요한 이유를 설명하시오.)

---

**Question 12** Explain 3 main use cases for views. (뷰의 주요 활용 사례 3가지를 설명하시오.)

---

**Question 13** Define stored procedure and explain differences between IN, OUT, INOUT parameters. (저장프로시저의 정의와 매개변수 IN, OUT, INOUT의 차이를 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain conditions for updatable view and provide example of non-updatable view. (수정 가능한 뷰의 조건을 설명하고, 수정 불가능한 뷰의 예를 제시하시오.)

---

## Advanced Level (1 Question)

**Question 15** Compare and analyze differences, advantages, and disadvantages of views and stored procedures. (뷰와 저장프로시저의 차이와 각각의 장단점을 비교 분석하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch10_view_procedure CHARACTER SET utf8mb4;
USE ch10_view_procedure;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    dept_id INT,
    salary INT,
    hire_date DATE
);

-- Insert data (데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 1, 5000000, '2020-01-15'),
(2, 'Sarah Lee', 1, 4000000, '2020-06-20'),
(3, 'David Park', 2, 4500000, '2019-03-10');

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
```

Submission: Screenshot showing all 3 employee records (제출: employees 테이블에 3명 데이터가 모두 보이는 스크린샷)

---

**Question 17** Create views based on employees table and query them. (employees 테이블을 기반으로 뷰를 생성하고 조회하시오.)

```sql
-- 1. Simple view: Query employee name and salary only (단순 뷰)
CREATE VIEW employee_salary_view AS
SELECT name, salary FROM employees;

SELECT * FROM employee_salary_view;

-- 2. Conditional view: Query employees with salary >= 4,000,000 (조건부 뷰)
CREATE VIEW high_salary_view AS
SELECT name, salary FROM employees WHERE salary >= 4000000;

SELECT * FROM high_salary_view;
```

Submission: Screenshot showing query results of both views (제출: 2개 뷰의 조회 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Perform aggregation and modification using views. (뷰를 이용한 집계와 수정을 수행하시오.)

```sql
-- 1. Aggregation view: Department summary with count and average salary (집계 뷰)
CREATE VIEW dept_summary_view AS
SELECT dept_id, COUNT(*) AS emp_count, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;

SELECT * FROM dept_summary_view;

-- 2. UPDATE through view (updatable view) (뷰를 통한 UPDATE)
CREATE VIEW emp_update_view AS
SELECT employee_id, name, salary FROM employees;

UPDATE emp_update_view SET salary = 5500000 WHERE employee_id = 1;
SELECT * FROM emp_update_view;
```

Submission: Screenshot of aggregation view and UPDATE results (제출: 집계 뷰와 UPDATE 후 결과 스크린샷)

---

**Question 19** Create and execute stored procedures. (저장프로시저를 생성하고 실행하시오.)

```sql
-- 1. Procedure with IN parameter (입력 매개변수 프로시저)
CREATE PROCEDURE GetEmployeeInfo (IN emp_id INT)
BEGIN
  SELECT name, salary FROM employees WHERE employee_id = emp_id;
END;

CALL GetEmployeeInfo(1);

-- 2. Procedure with OUT parameter (출력 매개변수 프로시저)
CREATE PROCEDURE GetEmployeeCount (OUT count INT)
BEGIN
  SELECT COUNT(*) INTO count FROM employees;
END;

CALL GetEmployeeCount(@emp_count);
SELECT @emp_count AS employee_count;

-- 3. Procedure with conditional logic (조건문이 포함된 프로시저)
CREATE PROCEDURE CheckSalary (IN emp_id INT)
BEGIN
  DECLARE emp_salary INT;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary > 4500000 THEN
    SELECT CONCAT('High salary: ', emp_salary);
  ELSE
    SELECT CONCAT('Regular salary: ', emp_salary);
  END IF;
END;

CALL CheckSalary(1);
```

Submission: Screenshot of all 3 procedure execution results (제출: 3개 프로시저의 실행 결과 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex stored procedures. (다음의 복잡한 저장프로시저를 작성하고 실행하시오.)

```
Requirements:

1. Salary adjustment procedure
   - Increase salary by percentage per department
   - Cap at maximum threshold
   - Return results (use IN/OUT parameters)

2. Complex logic procedure
   - Use IF-ELSEIF-ELSE for salary grade determination
   - Per-grade processing (A: bonus, B: standard, C: promotion pending, etc.)

3. Data validation procedure
   - Verify existence of input employee ID
   - Return info if exists, error message if not

4. WHILE loop procedure
   - Batch calculate/update salaries for multiple employees
   - Process each employee with loop

Submission:
   - SQL code for each procedure
   - Execution result screenshot for each
   - Data comparison before/after execution

요구사항:

1. 급여 인상 프로시저
   - 부서별로 급여를 일정 비율 인상
   - 상한선 초과 시 상한선으로 설정
   - 결과 반환 (입력/출력 매개변수 활용)

2. 복합 로직 프로시저
   - IF-ELSEIF-ELSE 구문으로 급여 등급 판정
   - 등급별 처리 (A: 보너스 계산, B: 일반, C: 승진 대기 등)

3. 데이터 검증 프로시저
   - 입력된 직원 ID 존재 여부 확인
   - 존재하면 정보 반환, 미존재하면 오류 메시지

4. WHILE 반복을 사용한 프로시저
   - 여러 직원의 급여를 일괄 계산/업데이트
   - 반복문으로 각 직원 처리

제출:
   - 각 프로시저의 SQL 코드
   - 각 프로시저의 실행 결과 스크린샷
   - 실행 전후 데이터 비교
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                           |
| :------: | :----: | :------------------------------------------------------------------------------------ |
|    1    |   ②   | View is virtual table, not storing actual data (가상 테이블로 실제 데이터 저장 안 함) |
|    2    |   ②   | CREATE VIEW for view creation (CREATE VIEW로 뷰 생성)                                 |
|    3    |   ①   | Stored procedure: reusable SQL routine in DB (DB에 저장되는 SQL 루틴)                 |
|    4    |   ①   | IN: input parameter only (입력 매개변수만)                                            |
|    5    |   ③   | CALL to execute procedure (CALL로 프로시저 실행)                                      |
|    6    |   ②   | GROUP BY makes view non-updatable (GROUP BY 포함 시 수정 불가)                        |
|    7    |   ②   | OUT: output parameter only (출력 전용)                                                |
|    8    |   ②   | DROP VIEW to delete view (DROP VIEW로 뷰 삭제)                                        |
|    9    |   ②   | View purpose: security and abstraction (보안과 추상화)                                |
|    10    |   ①   | View: query only; Procedure: logic implementation (뷰는 조회만, 프로시저는 로직)      |

---

## Short Answer Model Answers (5 Questions)

### Question 11: View Definition and Necessity

**Model Answer (모범 답안):**

```
Definition:
- Virtual table based on one or more tables
- Not storing actual data (logical abstraction)
- Defined with SELECT query

Necessity:

1. Simplify complex queries
   - Encapsulate complex JOINs and GROUP BYs
   - Users query with simple SELECT

2. Data security
   - Expose only specific columns (exclude salary info)
   - Control sensitive data access

3. Data abstraction
   - Maintain compatibility when source table structure changes
   - Minimize user query modifications
```

---

### Question 12: View Use Cases

**Model Answer (모범 답안):**

```
1. Simplify complex queries
   CREATE VIEW sales_summary AS
   SELECT p.name, COUNT(*) AS cnt, SUM(s.qty) AS total
   FROM products p
   JOIN sales s ON p.id = s.prod_id
   GROUP BY p.id;
   
   Users: SELECT * FROM sales_summary;

2. Data security
   CREATE VIEW emp_public AS
   SELECT emp_id, name, dept_id FROM employees;
   -- Exclude salary, SSN, etc.

3. Data abstraction
   CREATE VIEW active_employees AS
   SELECT * FROM employees WHERE termination_date IS NULL;
   -- Auto-exclude terminated employees
```

---

### Question 13: Stored Procedure and Parameters

**Model Answer (모범 답안):**

```
Definition:
- Reusable SQL routine stored in DB
- Includes programming logic (conditionals, loops)
- Executed with CALL

Parameters:

1. IN (Input Parameter)
   - Pass values to procedure
   - Read only
   CREATE PROCEDURE get_emp (IN emp_id INT)

2. OUT (Output Parameter)
   - Return results from procedure
   - Write only
   CREATE PROCEDURE count_emp (OUT cnt INT)
   SELECT COUNT(*) INTO cnt FROM employees;
   
   Call: CALL count_emp(@c); SELECT @c;

3. INOUT (Input/Output Parameter)
   - Receive input, process, return
   - Read and write
   CREATE PROCEDURE adjust_salary (INOUT sal DECIMAL)
   SET sal = sal * 1.1;
```

---

### Question 14: Updatable View Conditions

**Model Answer (모범 답안):**

```
Conditions for Updatable View:
1. Single table based
2. No GROUP BY
3. No DISTINCT
4. No JOIN
5. No HAVING
6. No LIMIT
7. No subqueries

Updatable View:
CREATE VIEW emp_update AS
SELECT emp_id, name, salary FROM employees;

UPDATE emp_update SET salary = 5000000 WHERE emp_id = 1;

Non-Updatable View:
CREATE VIEW dept_summary AS
SELECT dept_id, COUNT(*) AS cnt, AVG(salary) AS avg_sal
FROM employees
GROUP BY dept_id;
-- Non-updatable due to GROUP BY, AVG

CREATE VIEW high_salary AS
SELECT DISTINCT name FROM employees WHERE salary > 4000000;
-- Non-updatable due to DISTINCT
```

---

### Question 15: View vs Stored Procedure Comparison

**Model Answer (모범 답안):**

```
Differences:

View:
- SELECT-based virtual table
- Primarily for querying (mostly read-only)
- Logical abstraction purpose
- No parameters
- Simplifies complex queries

Stored Procedure:
- SQL routine with logic
- Query, modify, delete, control all possible
- Business logic automation
- Parameters supported (IN, OUT, INOUT)
- Use conditionals, loops

Advantages:

View:
✅ Simplifies queries
✅ Provides security
✅ Easy maintenance
❌ Performance: calculation per query

Procedure:
✅ Implements complex logic
✅ Performance: pre-compiled
✅ Reusability
❌ Management complexity
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Employee Table Creation

**Completion Criteria (완료 기준):**

✅ ch10_view_procedure database created
✅ employees table created
✅ 3 employee records inserted

---

### Question 17: Basic View Creation and Query

**Expected Result (예상 결과):**

```
employee_salary_view:
Sarah Lee, 4000000
Alex Kim, 5000000
David Park, 4500000

high_salary_view:
Alex Kim, 5000000
Sarah Lee, 4000000
David Park, 4500000
```

---

### Question 18: Aggregation View and View UPDATE

**Completion Criteria (완료 기준):**

✅ dept_summary_view: department statistics
✅ View UPDATE successful
✅ Data verified after modification

---

### Question 19: Stored Procedure Execution

**Completion Criteria (완료 기준):**

✅ IN procedure: specific employee info retrieval
✅ OUT procedure: employee count return
✅ Conditional procedure: salary grade determination

---

### Question 20: Complex Procedure Implementation

**Model Answer (모범 답안):**

```sql
-- 1. Salary raise procedure
CREATE PROCEDURE RaiseSalary (IN emp_id INT, IN raise_rate DECIMAL, OUT new_salary INT)
BEGIN
  DECLARE max_salary INT DEFAULT 6000000;
  DECLARE current_sal INT;
  
  SELECT salary INTO current_sal FROM employees WHERE employee_id = emp_id;
  SET new_salary = ROUND(current_sal * (1 + raise_rate/100));
  
  IF new_salary > max_salary THEN
    SET new_salary = max_salary;
  END IF;
  
  UPDATE employees SET salary = new_salary WHERE employee_id = emp_id;
END;

CALL RaiseSalary(1, 10, @new_sal);
SELECT @new_sal;

-- 2. Salary grade assignment procedure
CREATE PROCEDURE AssignSalaryGrade (IN emp_id INT, OUT grade CHAR)
BEGIN
  DECLARE emp_salary INT;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary >= 5000000 THEN
    SET grade = 'A';
  ELSEIF emp_salary >= 4500000 THEN
    SET grade = 'B';
  ELSEIF emp_salary >= 4000000 THEN
    SET grade = 'C';
  ELSE
    SET grade = 'D';
  END IF;
END;

CALL AssignSalaryGrade(1, @g);
SELECT @g;

-- 3. Employee data validation procedure
CREATE PROCEDURE ValidateEmployee (IN emp_id INT, OUT result VARCHAR(100))
BEGIN
  DECLARE emp_exists INT;
  SELECT COUNT(*) INTO emp_exists FROM employees WHERE employee_id = emp_id;
  
  IF emp_exists > 0 THEN
    SELECT CONCAT('Employee exists: ', name) INTO result FROM employees WHERE employee_id = emp_id;
  ELSE
    SET result = 'Employee not found';
  END IF;
END;

CALL ValidateEmployee(1, @result);
SELECT @result;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
