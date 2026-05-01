# Chapter 10. View and Stored Procedure

---

## 📖 Class Overview

In this chapter, you will learn about views and stored procedures that provide logical abstraction for databases. Views simplify complex queries and control data access, while stored procedures automate repetitive tasks and implement application logic in the database. You will study how to simplify complex queries with views, control data access, and automate tasks with stored procedures. The goal is to enhance database maintainability and security.

이 장에서는 데이터베이스의 논리적 추상화를 제공하는 뷰(View)와 재사용 가능한 SQL 루틴인 저장프로시저(Stored Procedure)를 학습합니다.
뷰를 사용하여 복잡한 쿼리를 단순화하고 데이터 접근을 제어하며, 저장프로시저로 반복적인 작업을 자동화하고 애플리케이션 로직을 데이터베이스에 구현하는 방법을 다룹니다. 데이터베이스의 유지보수성과 보안을 강화하는 것이 목표입니다.

---

## 📚 Part 1: Theoretical Learning

### 10.1 View Concept

A view is a virtual table based on one or more tables. (뷰는 하나 이상의 테이블을 기반으로 하는 가상 테이블입니다.)

**Create View (뷰 생성):**

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Query View (뷰 조회):**

```sql
SELECT * FROM view_name;
```

**Characteristics (특징):**

- Does not store actual data (logical abstraction) (실제 데이터를 저장하지 않음 논리적 추상화)
- Defined as SELECT query (SELECT 쿼리로 정의됨)
- Can be queried like a table with SELECT (테이블처럼 SELECT로 조회 가능)
- Simplifies complex joins or aggregations (복잡한 조인이나 집계를 단순화)

**Why Views Are Needed (뷰가 필요한 이유):**

1. **Simplify Complex Queries (복잡한 쿼리 단순화)** - When you join multiple tables or create queries with complex calculations, you can create a view and later query it with just one line: SELECT * FROM view_name. (여러 테이블을 JOIN하거나 복잡한 계산이 포함된 쿼리를 뷰로 만들어두면, 나중에는 SELECT * FROM view_name 한 줄로 끝납니다)
2. **Security (보안)** - Instead of showing users the entire table, you can create a view showing only necessary columns (for example, employee information excluding salary information). (사용자에게 전체 테이블을 보여주지 않고, 필요한 컬럼 예: 급여 정보를 제외한 직원 정보 만 골라서 뷰로 만들어 제공할 수 있습니다)
3. **Consistency (일관성)** - You can enforce querying only data that matches specific conditions (for example, excluding resigned employees). (특정 조건 예: 퇴사자 제외 에 맞는 데이터만 조회하도록 강제할 수 있습니다)

---

### 10.2 View Use Cases

**1. Simplify Complex Queries (복잡한 쿼리 단순화):**

```sql
CREATE VIEW sales_summary AS
SELECT p.product_name, COUNT(*) AS sales_count, SUM(s.quantity) AS total_qty
FROM products p
JOIN sales s ON p.product_id = s.product_id
GROUP BY p.product_id, p.product_name;

-- Usage (사용)
SELECT * FROM sales_summary WHERE total_qty > 100;
```

**2. Data Security (데이터 보안):**

```sql
CREATE VIEW employee_public AS
SELECT employee_id, name, hire_date
FROM employees;  -- Exclude salary information (급여 정보 제외)
```

**3. Data Abstraction (데이터 추상화):**

```sql
CREATE VIEW current_employees AS
SELECT * FROM employees
WHERE termination_date IS NULL;
```

---

### 10.3 Modify and Drop Views

**Modify View (뷰 수정):**

```sql
ALTER VIEW view_name AS
SELECT column1, column2, ...
FROM table_name;
```

**Drop View (뷰 삭제):**

```sql
DROP VIEW view_name;
DROP VIEW IF EXISTS view_name;  -- Ignore error if not exists (존재하지 않으면 오류 무시)
```

**Drop Multiple Views (여러 뷰 삭제):**

```sql
DROP VIEW view1, view2, view3;
```

---

### 10.4 Updatable View

If certain conditions are met, INSERT, UPDATE, DELETE are possible on views. (특정 조건을 만족하면 뷰에 INSERT, UPDATE, DELETE가 가능합니다.)

**Conditions (조건):**

- Based on single table (단일 테이블을 기반으로 함)
- Does not include GROUP BY, DISTINCT, JOIN (GROUP BY, DISTINCT, JOIN을 포함하지 않음)
- Does not include subquery, UNION (서브쿼리, UNION을 포함하지 않음)
- Does not include HAVING, LIMIT (HAVING, LIMIT을 포함하지 않음)

**Example (예시):**

```sql
CREATE VIEW employee_view AS
SELECT employee_id, name, salary FROM employees;

-- Update through view (뷰를 통한 수정 가능)
UPDATE employee_view SET salary = 5000000 WHERE employee_id = 1;
```

---

### 10.5 Stored Procedure

A stored procedure is a reusable SQL routine stored in the database. (저장프로시저는 데이터베이스에 저장되는 재사용 가능한 SQL 루틴입니다.)

**Create (생성):**

```sql
CREATE PROCEDURE procedure_name (
  IN parameter1 INT,
  OUT parameter2 VARCHAR(50)
)
BEGIN
  -- Procedure body (프로시저 본문)
  SELECT column INTO parameter2 FROM table WHERE id = parameter1;
END;
```

**Characteristics (특징):**

- Can include conditional statements and loops (조건문, 반복문 포함 가능)
- Can use parameters (IN, OUT, INOUT) (매개변수 사용 가능 IN, OUT, INOUT)
- Can control transactions (트랜잭션 제어 가능)
- Performance improvement (pre-compiled) (성능 향상 미리 컴파일됨)

**Why Stored Procedures Are Needed (저장프로시저가 필요한 이유):**

1. **Code Reusability (코드 재사용)** - The same logic can be used across multiple applications. (같은 로직을 여러 애플리케이션에서 사용할 수 있습니다)
2. **Security (보안)** - You can protect data safely by not giving users direct table access but only permission to execute specific procedures. (사용자에게 테이블 직접 접근 권한을 주지 않고, 특정 프로시저를 실행할 권한만 부여하여 데이터를 안전하게 보호할 수 있습니다)
3. **Performance (성능)** - Once compiled, the execution plan is cached, making repeated executions faster. (한 번 컴파일되면 실행 계획이 캐시되므로 반복 실행 시 속도가 빠릅니다)
4. **Complex Business Logic (복잡한 비즈니스 로직)** - Can perform complex tasks using conditional statements and loops. (조건문, 반복문으로 복잡한 작업을 수행할 수 있습니다)
5. **Reduce Network Traffic (네트워크 부하 감소)** - Instead of sending dozens of lines of SQL code to the server, you only need to send a short line CALL procedure_name(), reducing network traffic. (수십 줄의 SQL 코드를 서버로 보내는 대신, CALL procedure_name() 이라는 짧은 한 줄만 보내면 되므로 네트워크 트래픽이 줄어듭니다)

---

### 10.6 Stored Procedure Parameters

**IN (Input Parameter):**

Pass data to the procedure. (프로시저로 데이터를 전달합니다.)

```sql
CREATE PROCEDURE get_employee (IN emp_id INT)
BEGIN
  SELECT * FROM employees WHERE employee_id = emp_id;
END;
```

**OUT (Output Parameter):**

Return results calculated in the procedure. (프로시저에서 계산한 결과를 반환합니다.)

```sql
CREATE PROCEDURE get_employee_count (OUT count INT)
BEGIN
  SELECT COUNT(*) INTO count FROM employees;
END;
```

**INOUT (Input/Output Parameter):**

Receive data, process it, and return the result. (데이터를 받아서 처리한 후 결과를 반환합니다.)

```sql
CREATE PROCEDURE process_salary (INOUT salary DECIMAL)
BEGIN
  SET salary = salary * 1.1;
END;
```

---

### 10.7 Stored Procedure Control Structures

**IF-THEN-ELSE:**

Perform different tasks based on conditions. (조건에 따라 다른 작업을 수행합니다.)

```sql
CREATE PROCEDURE check_salary (IN emp_id INT)
BEGIN
  DECLARE salary DECIMAL;
  SELECT salary_amount INTO salary FROM employees WHERE employee_id = emp_id;
  
  IF salary > 5000000 THEN
    SELECT 'High' AS salary_level;
  ELSEIF salary > 4000000 THEN
    SELECT 'Medium' AS salary_level;
  ELSE
    SELECT 'Low' AS salary_level;
  END IF;
END;
```

**WHILE Loop:**

Perform repetitive tasks. (반복적인 작업을 수행합니다.)

```sql
CREATE PROCEDURE insert_sample_data (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  WHILE i <= count DO
    INSERT INTO temp_table VALUES (i, CONCAT('Data', i));
    SET i = i + 1;
  END WHILE;
END;
```

**CASE Statement:**

Handle multiple conditions cleanly. (여러 조건을 깔끔하게 처리합니다.)

```sql
CREATE PROCEDURE get_grade (IN score INT, OUT grade CHAR)
BEGIN
  CASE
    WHEN score >= 90 THEN SET grade = 'A';
    WHEN score >= 80 THEN SET grade = 'B';
    WHEN score >= 70 THEN SET grade = 'C';
    ELSE SET grade = 'F';
  END CASE;
END;
```

---

### 10.8 Execute Stored Procedure

**Execute with CALL Statement (CALL 문으로 실행):**

```sql
CALL procedure_name(parameter_list);
```

**Example (예시):**

```sql
CALL get_employee(1);

-- Receive result with OUT parameter (OUT 매개변수로 결과 받기)
CALL get_employee_count(@count);
SELECT @count;
```

---

### 10.9 Drop Stored Procedure

**Drop Procedure (프로시저 삭제):**

```sql
DROP PROCEDURE procedure_name;
DROP PROCEDURE IF EXISTS procedure_name;
```

---

## 📚 Part 2: Sample Data

### Essential Table Structure (필수 테이블 구성)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch10_view CHARACTER SET utf8mb4;
USE ch10_view;

-- Create employees table (employees 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    dept_id INT,
    salary DECIMAL(10, 2),
    hire_date DATE
);

-- Insert employee data (직원 데이터 삽입)
INSERT INTO employees VALUES
(1, 'Alex Johnson', 1, 5000000, '2020-01-15'),
(2, 'Sarah Williams', 1, 4000000, '2020-06-20'),
(3, 'David Brown', 2, 4500000, '2019-03-10'),
(4, 'Emily Davis', 2, 3500000, '2021-07-15'),
(5, 'Michael Wilson', 3, 4200000, '2020-09-05');

-- Create departments table (departments 테이블 생성)
CREATE TABLE departments (
    dept_id INT PRIMARY KEY AUTO_INCREMENT,
    department_name VARCHAR(50),
    location VARCHAR(50)
);

-- Insert department data (부서 데이터 삽입)
INSERT INTO departments VALUES
(1, 'Sales', 'Seoul'),
(2, 'Technology', 'Daejeon'),
(3, 'Human Resources', 'Seoul'),
(4, 'Finance', 'Busan');

-- Create archive table (아카이브 테이블 생성)
CREATE TABLE employees_archive (
    employee_id INT,
    name VARCHAR(50),
    dept_id INT,
    salary DECIMAL(10, 2),
    hire_date DATE
);
```

---

## 💻 Part 3: Hands-on Practice

### What You'll Learn in This Section

In this section, you will practice data abstraction through views and implementation of business logic through stored procedures. (이 섹션에서는 뷰를 통한 데이터 추상화와 저장프로시저를 통한 비즈니스 로직 구현을 실습합니다)

```sql
-- =====================================================
-- Section 1: View Basics (1-5) (섹션 1: 뷰의 기본 1-5번)
-- =====================================================

-- 1. Simple view (expose specific columns only) (단순 뷰 특정 열만 노출)
CREATE VIEW employee_names AS
SELECT employee_id, name, hire_date
FROM employees;

SELECT * FROM employee_names;

-- 2. JOIN view (integrate multiple tables) (JOIN 뷰 여러 테이블 통합)
CREATE VIEW employee_department_view AS
SELECT e.employee_id, e.name, d.department_name, d.location
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id;

SELECT * FROM employee_department_view;

-- 3. Aggregate view (use GROUP BY) (집계 뷰 GROUP BY 사용)
CREATE VIEW dept_salary_summary AS
SELECT dept_id, COUNT(*) AS emp_count, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;

SELECT * FROM dept_salary_summary;

-- 4. Conditional view (auto filter with WHERE) (조건부 뷰 WHERE로 자동 필터링)
CREATE VIEW high_salary_employees AS
SELECT employee_id, name, salary
FROM employees
WHERE salary > 4500000;

SELECT * FROM high_salary_employees;

-- 5. Drop view (뷰 삭제)
DROP VIEW IF EXISTS high_salary_employees;

-- =====================================================
-- Section 2: Updatable View (6-8) (섹션 2: 수정 가능한 뷰 6-8번)
-- =====================================================

-- 6. Updatable view (single table, simple condition) (수정 가능한 뷰 단일 테이블, 단순 조건)
CREATE VIEW employee_view AS
SELECT employee_id, name, salary FROM employees;

-- 7. INSERT through view (뷰를 통한 INSERT)
INSERT INTO employee_view (name, salary)
VALUES ('Jessica Anderson', 4200000);

-- 8. UPDATE through view (뷰를 통한 UPDATE)
UPDATE employee_view SET salary = 4800000 WHERE employee_id = 2;

-- =====================================================
-- Section 3: Stored Procedure Basics (9-13) (섹션 3: 저장프로시저 기본 9-13번)
-- =====================================================

-- 9. Basic stored procedure (input parameter) (기본 저장프로시저 입력 매개변수)
DELIMITER //
CREATE PROCEDURE GetEmployeeInfo (IN emp_id INT)
BEGIN
  SELECT employee_id, name, salary, dept_id
  FROM employees
  WHERE employee_id = emp_id;
END //
DELIMITER ;

CALL GetEmployeeInfo(1);

-- 10. Output parameter (return result) (출력 매개변수 결과 반환)
DELIMITER //
CREATE PROCEDURE GetEmployeeCount (OUT emp_count INT)
BEGIN
  SELECT COUNT(*) INTO emp_count FROM employees;
END //
DELIMITER //

CALL GetEmployeeCount(@count);
SELECT @count;

-- 11. Input/Output parameter (salary increase) (입출력 매개변수 급여 인상)
DELIMITER //
CREATE PROCEDURE IncreaseSalary (INOUT salary DECIMAL)
BEGIN
  SET salary = salary * 1.1;
END //
DELIMITER ;

SET @my_salary = 5000000;
CALL IncreaseSalary(@my_salary);
SELECT @my_salary;

-- 12. IF-ELSE conditional statement (salary level classification) (IF-ELSE 조건문 급여 수준 분류)
DELIMITER //
CREATE PROCEDURE CheckSalaryLevel (IN emp_id INT)
BEGIN
  DECLARE emp_salary DECIMAL;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary > 5000000 THEN
    SELECT 'High' AS salary_level;
  ELSEIF emp_salary > 4000000 THEN
    SELECT 'Medium' AS salary_level;
  ELSE
    SELECT 'Low' AS salary_level;
  END IF;
END //
DELIMITER ;

CALL CheckSalaryLevel(1);

-- 13. CASE statement (grade assignment) (CASE 문 학점 할당)
DELIMITER //
CREATE PROCEDURE GetGrade (IN score INT, OUT grade CHAR(1))
BEGIN
  SET grade = CASE
    WHEN score >= 90 THEN 'A'
    WHEN score >= 80 THEN 'B'
    WHEN score >= 70 THEN 'C'
    ELSE 'F'
  END;
END //
DELIMITER ;

CALL GetGrade(85, @result);
SELECT @result;

-- =====================================================
-- Section 4: Advanced Procedure (14-16) (섹션 4: 고급 프로시저 14-16번)
-- =====================================================

-- 14. WHILE loop (repetitive processing) (WHILE 루프 반복 처리)
DELIMITER //
CREATE PROCEDURE InsertSampleData (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  WHILE i <= count DO
    INSERT INTO employees (name, dept_id, salary)
    VALUES (CONCAT('Employee', i), 1, 3000000 + (i * 100000));
    SET i = i + 1;
  END WHILE;
END //
DELIMITER ;

CALL InsertSampleData(5);

-- 15. Variable declaration and assignment (salary statistics) (변수 선언과 할당 급여 통계)
DELIMITER //
CREATE PROCEDURE CalculateSalaryInfo ()
BEGIN
  DECLARE total_salary DECIMAL;
  DECLARE avg_salary DECIMAL;
  DECLARE emp_count INT;
  
  SELECT SUM(salary) INTO total_salary FROM employees;
  SELECT AVG(salary) INTO avg_salary FROM employees;
  SELECT COUNT(*) INTO emp_count FROM employees;
  
  SELECT total_salary, avg_salary, emp_count;
END //
DELIMITER ;

CALL CalculateSalaryInfo();

-- 16. Procedure with transaction (department transfer) (트랜잭션 포함 프로시저 부서 이동)
DELIMITER //
CREATE PROCEDURE TransferEmployee (IN emp_id INT, IN new_dept INT)
BEGIN
  START TRANSACTION;
  
  UPDATE employees SET dept_id = new_dept WHERE employee_id = emp_id;
  
  COMMIT;
END //
DELIMITER ;

CALL TransferEmployee(1, 2);

-- =====================================================
-- Section 5: Real-world Application (17-20) (섹션 5: 실무 응용 17-20번)
-- =====================================================

-- 17. Data validation procedure (check existence) (데이터 검증 프로시저 존재 여부 확인)
DELIMITER //
CREATE PROCEDURE ValidateEmployee (IN emp_id INT, OUT is_valid INT)
BEGIN
  IF EXISTS(SELECT 1 FROM employees WHERE employee_id = emp_id) THEN
    SET is_valid = 1;
  ELSE
    SET is_valid = 0;
  END IF;
END //
DELIMITER ;

CALL ValidateEmployee(1, @valid);
SELECT @valid;

-- 18. Statistics calculation procedure (total, average, maximum) (통계 계산 프로시저 총합, 평균, 최고값)
DELIMITER //
CREATE PROCEDURE GetSalaryStatistics (OUT total DECIMAL, OUT average DECIMAL, OUT max DECIMAL)
BEGIN
  SELECT SUM(salary), AVG(salary), MAX(salary)
  INTO total, average, max FROM employees;
END //
DELIMITER ;

CALL GetSalaryStatistics(@t, @a, @m);
SELECT @t AS total, @a AS average, @m AS max;

-- 19. Migration procedure (data transfer) (마이그레이션 프로시저 데이터 이전)
DELIMITER //
CREATE PROCEDURE MigrateOldEmployees ()
BEGIN
  START TRANSACTION;
  
  INSERT INTO employees_archive
  SELECT * FROM employees WHERE hire_date < '2020-01-01';
  
  DELETE FROM employees WHERE hire_date < '2020-01-01';
  
  COMMIT;
END //
DELIMITER ;

CALL MigrateOldEmployees();

-- 20. Backup procedure (data copy) (백업 프로시저 데이터 복사)
DELIMITER //
CREATE PROCEDURE BackupData ()
BEGIN
  DELETE FROM employees_archive;
  INSERT INTO employees_archive
  SELECT * FROM employees;
END //
DELIMITER ;

CALL BackupData();
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the concept, characteristics, and use cases of views. Analyze the advantages and disadvantages of using views and discuss in which situations views should be used.

뷰의 개념, 특징, 활용 사례를 설명하세요. 뷰를 사용하는 장점과 단점을 분석하고, 어떤 상황에서 뷰를 사용해야 하는지 논의하세요.

**Assignment 2**: Explain the concept and characteristics of stored procedures. Describe situations where stored procedures are needed and considerations when handling application logic in databases.

저장프로시저의 개념과 특징을 설명하세요. 저장프로시저가 필요한 상황과 애플리케이션 로직을 데이터베이스에서 처리할 때의 고려사항을 서술하세요.

**Assignment 3**: Explain the differences in stored procedure parameters (IN, OUT, INOUT). Provide use cases for each.

저장프로시저의 매개변수(IN, OUT, INOUT)의 차이점을 설명하고, 각각의 활용 사례를 제시하세요.

**Assignment 4**: Explain the control structures of stored procedures (IF-THEN-ELSE, WHILE, CASE) and error handling methods. Discuss how to implement complex business logic.

저장프로시저의 제어 구조(IF-THEN-ELSE, WHILE, CASE)와 에러 처리 방법을 설명하세요. 복잡한 비즈니스 로직을 구현하는 방법을 논의하세요.

**Assignment 5**: Compare the performance characteristics of views and stored procedures. Provide criteria for choosing when to use views versus stored procedures.

뷰와 저장프로시저의 성능 특성을 비교하세요. 어떤 경우에 뷰를 사용할지, 저장프로시저를 사용할지 선택 기준을 제시하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Create various types of views: simple view, JOIN view, aggregate view, conditional view.

다양한 유형의 뷰를 생성하세요: 단순 뷰, JOIN 뷰, 집계 뷰, 조건부 뷰.

**Assignment 2**: Create an updatable view and practice INSERT and UPDATE through the view.

수정 가능한 뷰를 생성하고, 뷰를 통한 INSERT, UPDATE를 실습하세요.

**Assignment 3**: Write stored procedures with various parameters: IN, OUT, INOUT.

다양한 매개변수를 가진 저장프로시저를 작성하세요: IN, OUT, INOUT.

**Assignment 4**: Write stored procedures using control statements (IF-ELSE, CASE, WHILE).

제어문(IF-ELSE, CASE, WHILE)을 사용한 저장프로시저를 작성하세요.

**Assignment 5**: Execute all queries provided from 10-1 to 10-20 in Part 3 and attach result screenshots for each query. Additionally, create 5 or more real-world scenario-based views and procedures and explain their purpose and usage methods.

Part 3의 실습 10-1부터 10-20까지 제공된 모든 쿼리를 직접 실행하고, 각 쿼리의 결과를 스크린샷으로 첨부하세요. 추가로 5개 이상의 실무 시나리오 기반 뷰와 프로시저를 만들어 그 목적과 활용 방법을 설명하세요.

**Submission Format**: SQL file (Ch10_View_Procedure_[StudentID].sql) and result screenshots

제출 형식: SQL 파일 (Ch10_View_Procedure_[학번].sql) 및 결과 스크린샷

---

Thank you for your attention.  
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
