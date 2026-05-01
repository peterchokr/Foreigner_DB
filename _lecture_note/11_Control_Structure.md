# Chapter 11. Control Structures (Conditional and Loop Statements)

---

## 📖 Class Overview

In this chapter, you will comprehensively study the conditional and loop statements that were partially used in Chapter 10 to implement programming logic in stored procedures and functions. You will implement complex database logic using conditional statements like IF-THEN-ELSE and CASE, and loop statements like WHILE, REPEAT, and LOOP. The goal is to precisely understand control flow and develop the ability to handle diverse business requirements at the database level.

이 장에서는 10장에서 소개한 저장프로시저와 함수에서 프로그래밍 로직을 구현하기 위해 일부 사용했던 조건문과 반복문을 전체적으로 학습합니다. IF-THEN-ELSE, CASE 문과 같은 조건문, 그리고 WHILE, REPEAT, LOOP 문과 같은 반복문을 사용하여 복잡한 데이터베이스 로직을 구현합니다. 제어 흐름을 정확하게 이해하고 다양한 비즈니스 요구사항을 데이터베이스 수준에서 처리하는 능력을 개발하는 것이 목표입니다.

---

## 📚 Part 1: Theoretical Learning

### What You'll Learn in This Section

- Structure and usage of IF-THEN-ELSE statement
- Two types of CASE statement
- WHILE loop
- REPEAT-UNTIL loop
- LOOP statement
- Nested control structures
- Labels and loop control

---

### 11.1 IF-THEN-ELSE Statement

IF-THEN-ELSE performs different tasks based on conditions.

IF-THEN-ELSE는 조건에 따라 다른 작업을 수행합니다.

**Basic Syntax (기본 문법):**

```sql
IF condition THEN
  -- Execute when condition is true (조건이 참일 때 실행)
  statement1;
ELSE
  -- Execute when condition is false (조건이 거짓일 때 실행)
  statement2;
END IF;
```

**Using ELSEIF (ELSEIF 사용):**

```sql
IF condition1 THEN
  statement1;
ELSEIF condition2 THEN
  statement2;
ELSEIF condition3 THEN
  statement3;
ELSE
  statement4;
END IF;
```

**Example (예시):**

```sql
CREATE PROCEDURE grade_assignment (IN score INT, OUT grade CHAR)
BEGIN
  IF score >= 90 THEN
    SET grade = 'A';
  ELSEIF score >= 80 THEN
    SET grade = 'B';
  ELSEIF score >= 70 THEN
    SET grade = 'C';
  ELSEIF score >= 60 THEN
    SET grade = 'D';
  ELSE
    SET grade = 'F';
  END IF;
END;
```

---

### 11.2 CASE Statement - Simple Form

**Simple CASE Statement (간단한 형태의 CASE 문):**

```sql
CASE variable
  WHEN value1 THEN statement1;
  WHEN value2 THEN statement2;
  ...
  ELSE statement_default;
END CASE;
```

**Example (예시):**

```sql
DECLARE month_name VARCHAR(20);
SET month_name = CASE month_num
  WHEN 1 THEN 'January'
  WHEN 2 THEN 'February'
  WHEN 3 THEN 'March'
  ...
  ELSE 'Unknown'
END;
```

---

### 11.3 CASE Statement - Searched Form

**Searched CASE (검색 형태의 CASE 문):**

```sql
CASE
  WHEN condition1 THEN statement1;
  WHEN condition2 THEN statement2;
  ...
  ELSE statement_default;
END CASE;
```

**Example (예시):**

```sql
DECLARE salary_level VARCHAR(10);
SET salary_level = CASE
  WHEN salary >= 5000000 THEN 'High'
  WHEN salary >= 4000000 THEN 'Middle'
  WHEN salary >= 3000000 THEN 'Low'
  ELSE 'Entry'
END;
```

---

### 11.4 WHILE Loop

WHILE statement repeats while condition is true.

WHILE 문은 조건이 참인 동안 반복합니다.

**Syntax (문법):**

```sql
WHILE condition DO
  -- Statements to repeat (반복할 문장들)
  statement;
END WHILE;
```

**Example (예시):**

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

**Characteristics (특징):**

- Checks condition first, then repeats (조건을 먼저 확인하고 반복)
- Does not execute if condition is false (조건이 거짓이면 반복 실행 안 됨)

---

### 11.5 REPEAT-UNTIL Loop

REPEAT-UNTIL executes first, then checks condition.

REPEAT-UNTIL 문은 먼저 실행한 후 조건을 확인합니다.

**Syntax (문법):**

```sql
REPEAT
  -- Statements to repeat (반복할 문장들)
  statement;
UNTIL condition
END REPEAT;
```

**Example (예시):**

```sql
CREATE PROCEDURE repeat_example (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  REPEAT
    INSERT INTO temp_table VALUES (i, CONCAT('Data', i));
    SET i = i + 1;
  UNTIL i > count
  END REPEAT;
END;
```

**Characteristics (특징):**

- Executes at least once (최소한 한 번은 실행됨)
- Opposite of WHILE in condition check (WHILE과 반대로 조건 확인)

---

### 11.6 LOOP Statement

LOOP repeats infinitely, so LEAVE statement must be used to exit.

LOOP 문은 무한 반복하므로 LEAVE 문으로 탈출해야 합니다.

**Syntax (문법):**

```sql
[label_name:] LOOP
  -- Statements to repeat (반복할 문장들)
  statement;
  IF condition THEN
    LEAVE label_name;
  END IF;
END LOOP;
```

**Example (예시):**

```sql
CREATE PROCEDURE loop_example (IN max_count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  my_loop: LOOP
    INSERT INTO temp_table VALUES (i, CONCAT('Data', i));
    SET i = i + 1;
    IF i > max_count THEN
      LEAVE my_loop;
    END IF;
  END LOOP;
END;
```

---

### 11.7 ITERATE (Continue)

ITERATE statement moves to the next iteration.

ITERATE 문은 다음 반복으로 이동합니다.

**Example (예시):**

```sql
DECLARE i INT DEFAULT 0;
WHILE i < 10 DO
  SET i = i + 1;
  IF MOD(i, 2) = 0 THEN
    ITERATE;  -- Skip to next iteration for even numbers (짝수일 때 다음 반복으로)
  END IF;
  INSERT INTO odd_numbers VALUES (i);
END WHILE;
```

---

### 11.8 LEAVE (Exit)

LEAVE statement terminates the loop.

LEAVE 문은 반복을 종료합니다.

**Example (예시):**

```sql
my_loop: LOOP
  -- Loop statements (반복 문장)
  IF condition THEN
    LEAVE my_loop;
  END IF;
END LOOP;
```

---

### 11.9 Nested Control Structures

**Combine multiple control structures (여러 제어 구조를 결합):**

```sql
CREATE PROCEDURE complex_logic ()
BEGIN
  DECLARE i INT DEFAULT 1;
  
  WHILE i <= 5 DO
    IF i MOD 2 = 0 THEN
      CASE i
        WHEN 2 THEN INSERT INTO results VALUES (2, 'Two');
        WHEN 4 THEN INSERT INTO results VALUES (4, 'Four');
      END CASE;
    ELSE
      INSERT INTO results VALUES (i, 'Odd');
    END IF;
    SET i = i + 1;
  END WHILE;
END;
```

---

## 📚 Part 2: Sample Data

### Essential Table Structure (필수 테이블 구성)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch11_control CHARACTER SET utf8mb4;
USE ch11_control;

-- Create employees table (employees 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    dept_id INT,
    salary DECIMAL(10, 2)
);

-- Insert employee data (직원 데이터 삽입)
INSERT INTO employees VALUES
(1, 'Alex Johnson', 1, 5000000),
(2, 'Sarah Williams', 1, 4000000),
(3, 'David Brown', 2, 4500000),
(4, 'Emily Davis', 2, 3500000),
(5, 'Michael Wilson', 3, 4200000);

-- Create temp_table (for testing) (테스트용 테이블)
CREATE TABLE temp_table (
    id INT,
    data VARCHAR(100)
);
```

---

## 💻 Part 3: Hands-on Practice (15 Problems)

### What You'll Learn in This Section

In this section, you will implement complex database logic using conditional and loop statements. (이 섹션에서는 조건문과 반복문을 활용하여 복잡한 데이터베이스 로직을 구현합니다)

```sql
-- =====================================================
-- Section 1: Conditional Statements (1-4) (섹션 1: 조건문 1-4번)
-- =====================================================

-- 1. Basic IF-THEN (conditional processing) (기본 IF-THEN 조건에 따른 처리)
DELIMITER //
CREATE PROCEDURE CheckSalary (IN emp_id INT)
BEGIN
  DECLARE emp_salary DECIMAL;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary >= 5000000 THEN
    SELECT 'High salary' AS status;
  END IF;
END //
DELIMITER ;

CALL CheckSalary(1);

-- 2. IF-ELSEIF-ELSE (3 or more branches) (IF-ELSEIF-ELSE 3개 이상 분기)
DELIMITER //
CREATE PROCEDURE GradeAssignment (IN score INT)
BEGIN
  IF score >= 90 THEN
    SELECT 'A' AS grade;
  ELSEIF score >= 80 THEN
    SELECT 'B' AS grade;
  ELSEIF score >= 70 THEN
    SELECT 'C' AS grade;
  ELSE
    SELECT 'F' AS grade;
  END IF;
END //
DELIMITER ;

CALL GradeAssignment(85);

-- 3. Simple CASE (value mapping) (간단한 CASE 값에 따른 매핑)
DELIMITER //
CREATE PROCEDURE SimpleCaseExample (IN month_num INT)
BEGIN
  DECLARE month_name VARCHAR(20);
  SET month_name = CASE month_num
    WHEN 1 THEN 'January'
    WHEN 2 THEN 'February'
    WHEN 3 THEN 'March'
    ELSE 'Other'
  END;
  SELECT month_name;
END //
DELIMITER ;

CALL SimpleCaseExample(3);

-- 4. Data validation (conditional validation) (데이터 검증 조건에 따른 검증)
DELIMITER //
CREATE PROCEDURE ValidateData (IN emp_id INT, OUT is_valid INT)
BEGIN
  DECLARE emp_salary DECIMAL;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary IS NULL THEN
    SET is_valid = 0;
  ELSEIF emp_salary < 0 THEN
    SET is_valid = 0;
  ELSE
    SET is_valid = 1;
  END IF;
END //
DELIMITER ;

CALL ValidateData(1, @valid);
SELECT @valid;

-- =====================================================
-- Section 2: WHILE Loop (5-7) (섹션 2: WHILE 반복문 5-7번)
-- =====================================================

-- 5. WHILE basics (data generation) (WHILE 기본 데이터 생성)
DELIMITER //
CREATE PROCEDURE WhileLoop (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  WHILE i <= count DO
    INSERT INTO temp_table (id, data) VALUES (i, CONCAT('Data', i));
    SET i = i + 1;
  END WHILE;
END //
DELIMITER ;

CALL WhileLoop(10);

-- 6. WHILE with condition (conditional processing) (WHILE과 조건 조건부 처리)
DELIMITER //
CREATE PROCEDURE ConditionalWhile (IN max_value INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  WHILE i <= max_value DO
    IF i % 2 = 0 THEN
      INSERT INTO temp_table (id, data) VALUES (i, CONCAT('Even: ', i));
    END IF;
    SET i = i + 1;
  END WHILE;
END //
DELIMITER ;

CALL ConditionalWhile(20);

-- 7. WHILE cumulative calculation (sum calculation) (WHILE 누적 계산 합계 계산)
DELIMITER //
CREATE PROCEDURE SumCalculation (IN max_num INT, OUT total INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  DECLARE sum INT DEFAULT 0;
  WHILE i <= max_num DO
    SET sum = sum + i;
    SET i = i + 1;
  END WHILE;
  SET total = sum;
END //
DELIMITER ;

CALL SumCalculation(100, @result);
SELECT @result;

-- =====================================================
-- Section 3: REPEAT and LOOP (8-10) (섹션 3: REPEAT와 LOOP 반복문 8-10번)
-- =====================================================

-- 8. REPEAT basics (execute at least once) (REPEAT 기본 최소 1번 실행)
DELIMITER //
CREATE PROCEDURE RepeatLoop (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  REPEAT
    INSERT INTO temp_table (id, data) VALUES (i, CONCAT('Data', i));
    SET i = i + 1;
  UNTIL i > count
  END REPEAT;
END //
DELIMITER ;

CALL RepeatLoop(5);

-- 9. LOOP basics (exit with LEAVE) (LOOP 기본 LEAVE로 종료)
DELIMITER //
CREATE PROCEDURE LoopExample (IN max_count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  my_loop: LOOP
    INSERT INTO temp_table (id, data) VALUES (i, CONCAT('Iteration ', i));
    SET i = i + 1;
    IF i > max_count THEN
      LEAVE my_loop;
    END IF;
  END LOOP;
END //
DELIMITER ;

CALL LoopExample(10);

-- 10. LOOP with ITERATE (skip iteration) (LOOP와 ITERATE 반복 건너뛰기)
DELIMITER //
CREATE PROCEDURE LoopWithIterate (IN max_val INT)
BEGIN
  DECLARE i INT DEFAULT 0;
  my_loop: LOOP
    SET i = i + 1;
    IF i > max_val THEN
      LEAVE my_loop;
    END IF;
  
    IF i % 2 = 0 THEN
      ITERATE my_loop;
    END IF;
  
    INSERT INTO temp_table (id, data) VALUES (i, CONCAT('Odd: ', i));
  END LOOP;
END //
DELIMITER ;

CALL LoopWithIterate(20);

-- =====================================================
-- Section 4: Real-world Application (11-12) (섹션 4: 실무 응용 11-12번)
-- =====================================================

-- 11. Conditional INSERT (conditional insertion) (조건부 INSERT 조건에 따른 삽입)
DELIMITER //
CREATE PROCEDURE ConditionalInsert (IN emp_salary DECIMAL)
BEGIN
  IF emp_salary > 5000000 THEN
    INSERT INTO temp_table (id, data) VALUES (1, 'Top Earner');
  ELSEIF emp_salary > 4000000 THEN
    INSERT INTO temp_table (id, data) VALUES (2, 'Middle Earner');
  ELSE
    INSERT INTO temp_table (id, data) VALUES (3, 'Entry Level');
  END IF;
END //
DELIMITER ;

CALL ConditionalInsert(4500000);

-- 12. Conditional UPDATE (conditional update) (조건부 UPDATE 조건에 따른 수정)
DELIMITER //
CREATE PROCEDURE ConditionalUpdate (IN emp_id INT, IN new_salary DECIMAL)
BEGIN
  DECLARE old_salary DECIMAL;
  SELECT salary INTO old_salary FROM employees WHERE employee_id = emp_id;
  
  IF new_salary > old_salary * 1.5 THEN
    UPDATE employees SET salary = old_salary * 1.2 WHERE employee_id = emp_id;
  ELSE
    UPDATE employees SET salary = new_salary WHERE employee_id = emp_id;
  END IF;
END //
DELIMITER ;

CALL ConditionalUpdate(1, 6000000);

```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the characteristics of IF-THEN-ELSE and CASE statements in detail and discuss situations where each is appropriate. Analyze which is better in terms of readability when handling complex conditions.

IF-THEN-ELSE와 CASE 문의 특징을 상세히 설명하고, 각각이 적합한 상황을 논의하세요. 복잡한 조건을 처리할 때 가독성 면에서 어느 것이 나은지 분석하세요.

**Assignment 2**: Explain the differences between the three loop statements (WHILE, REPEAT, LOOP) in detail. Compare when to use each and their advantages and disadvantages, and present which one to choose in what situations.

WHILE, REPEAT, LOOP 세 가지 반복문의 차이점을 상세히 설명하세요. 각각의 사용 시기와 장단점을 비교하고, 어떤 상황에서 어느 것을 선택할지 제시하세요.

**Assignment 3**: Explain the roles of ITERATE and LEAVE statements in detail. Describe how these statements are used when precisely adjusting the control flow of loops.

ITERATE와 LEAVE 문의 역할을 상세히 설명하세요. 반복문의 제어 흐름을 정확하게 조정할 때 이들 문장이 어떻게 사용되는지 서술하세요.

**Assignment 4**: Discuss considerations when nesting control structures in detail. Propose how to write complex nested structures with good readability and present real-world cases combining conditional and loop statements.

제어 구조를 중첩시킬 때의 고려사항을 상세히 논의하세요. 복잡한 중첩 구조를 어떻게 가독성 있게 작성할 수 있는지 제안하세요. 조건문과 반복문을 결합한 실무 사례를 제시하세요.

**Assignment 5**: Explain the practical application of control structures in business logic in detail. Discuss how to choose appropriate control structures in various scenarios and the performance implications.

비즈니스 로직에서 제어 구조의 실무 활용을 상세히 설명하세요. 다양한 시나리오에서 적절한 제어 구조를 선택하는 방법과 성능 영향을 논의하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Write various conditional statements: IF-THEN-ELSE, multiple ELSEIF, CASE statement.

다양한 조건문을 작성하세요: IF-THEN-ELSE, 여러 ELSEIF, CASE 문.

**Assignment 2**: Write procedures using all three loop types (WHILE, REPEAT, LOOP).

세 가지 반복문(WHILE, REPEAT, LOOP)을 모두 사용하는 프로시저를 작성하세요.

**Assignment 3**: Write loop control procedures using ITERATE and LEAVE.

ITERATE와 LEAVE를 사용한 반복문 제어 프로시저를 작성하세요.

**Assignment 4**: Write procedures combining conditional and loop statements and include nested loop examples.

조건문과 반복문을 결합한 프로시저를 작성하고, 중첩된 반복문 예제를 포함하세요.

**Assignment 5**: Execute all queries provided from 11-1 to 11-15 in Part 3 and attach result screenshots for each query. Additionally, create 5 or more real-world scenario-based control structures and explain their purpose and usage methods.

Part 3의 실습 11-1부터 11-15까지 제공된 모든 쿼리를 직접 실행하고, 각 쿼리의 결과를 스크린샷으로 첨부하세요. 추가로 5개 이상의 비즈니스 시나리오 기반 제어 구조를 만들어 그 목적과 활용 방법을 설명하세요.

**Submission Format**: SQL file (Ch11_Control_Structure_[StudentID].sql) and result screenshots

제출 형식: SQL 파일 (Ch11_Control_Structure_[학번].sql) 및 결과 스크린샷

---

Thank you for your attention.  
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
