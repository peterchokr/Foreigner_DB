# Chapter 11. Conditional and Loop Statements - Practice Problems

Dear students! After completing Chapter 11, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

11장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 11, you should understand the following:

- IF-THEN-ELSE statement structure (IF-THEN-ELSE 문의 구조)
- CASE statement (간단한 형태와 검색 형태)
- WHILE, REPEAT, LOOP loops (반복문)
- Nested control structures (중첩된 제어 구조)
- Labels and loop control (LEAVE, ITERATE) (레이블과 반복문 제어)
- Practical applications and optimization (실무 활용 및 성능 최적화)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** Correct basic structure of IF-THEN-ELSE? (IF-THEN-ELSE 문의 기본 구조로 옳은 것은?)

- ① IF condition THEN statement; END;
- ② IF condition THEN statement; ELSE statement; END IF;
- ③ IF (condition) { statement; }
- ④ IF condition BEGIN statement; END;

---

**Question 2** Simple CASE statement form? (CASE 문의 간단한 형태는?)

- ① CASE WHEN condition THEN statement;
- ② CASE variable WHEN value THEN statement;
- ③ CASE condition WHEN value THEN statement;
- ④ CASE THEN statement;

---

**Question 3** Characteristic of WHILE loop? (WHILE 반복문의 특징은?)

- ① Always executes at least once (무조건 최소 1번 실행)
- ② Check condition first, then loop (조건을 먼저 확인하고 반복)
- ③ Loop without condition check (조건을 확인하지 않고 반복)
- ④ Exit with BREAK (BREAK로 탈출)

---

**Question 4** Difference between REPEAT-UNTIL and WHILE? (REPEAT-UNTIL 반복문과 WHILE의 차이는?)

- ① REPEAT checks condition first (REPEAT는 조건을 먼저 확인)
- ② WHILE always executes once (WHILE은 무조건 1번 실행)
- ③ REPEAT always executes once (condition checked after) (REPEAT는 무조건 1번 실행)
- ④ No difference (차이가 없음)

---

**Question 5** How to exit LOOP? (LOOP 반복문에서 탈출하는 방법은?)

- ① BREAK;
- ② EXIT;
- ③ LEAVE label_name;
- ④ STOP;

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which uses ELSEIF correctly? (다음 중 ELSEIF를 올바르게 사용한 것은?)

```sql
① IF score >= 90 THEN SET grade = 'A';
   ELSEIF score >= 80 THEN SET grade = 'B';
   ELSE SET grade = 'C';
   END IF;

② IF score >= 90 THEN SET grade = 'A';
   ELSE IF score >= 80 THEN SET grade = 'B';
   END IF;
   END IF;
```

- ① Correct (올바름)
- ② Correct (올바름)
- ③ Only ① correct (①만 올바름)
- ④ Only ② correct (②만 올바름)

---

**Question 7** Searched form CASE statement? (검색 형태의 CASE 문은?)

```sql
① CASE month_num WHEN 1 THEN '1월'

② CASE
   WHEN salary >= 5000000 THEN '상'
   WHEN salary >= 4000000 THEN '중'
   END CASE;
```

- ① Simple form (간단한 형태)
- ② Searched form (검색 형태)
- ③ Both same form (둘 다 같은 형태)
- ④ Both searched form (둘 다 검색 형태)

---

**Question 8** Using nested control structures? (중첩된 제어 구조의 사용 예는?)

- ① WHILE, IF, CASE together (WHILE IF CASE를 함께 사용)
- ② IF within CASE, CASE within IF (IF 내에서 CASE, CASE 내에서 IF)
- ③ IF and CASE sequentially (IF와 CASE를 연속으로 사용)
- ④ Both ① and ② (①과 ②)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Role of ITERATE statement? (ITERATE 문의 역할은?)

- ① Completely terminate loop (반복문을 완전히 종료)
- ② Skip current iteration, move to next (현재 반복 주기를 건너뛰고 다음으로 이동)
- ③ Increase iteration count (반복 횟수를 증가)
- ④ Re-evaluate condition (조건을 다시 평가)

---

**Question 10** Relationship between Label and LEAVE? (라벨과 LEAVE의 관계는?)

```sql
my_loop: LOOP
  IF condition THEN
    LEAVE my_loop;
  END IF;
END LOOP;
```

- ① Label identifies LOOP, LEAVE exits (라벨로 LOOP를 식별하고 LEAVE로 탈출)
- ② LEAVE alone can exit (LEAVE만으로 탈출 가능)
- ③ Label is optional (라벨은 선택사항)
- ④ Not required for exit (LOOP 탈출에는 필수 아님)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain IF-THEN-ELSE structure and ELSEIF usage. (IF-THEN-ELSE 문의 구조를 설명하고, ELSEIF를 사용하는 방법을 설명하시오.)

---

**Question 12** Explain two CASE forms and usage situations. (CASE 문의 두 가지 형태와 사용 상황을 예시하시오.)

---

**Question 13** Explain differences between WHILE, REPEAT, LOOP loops. (WHILE, REPEAT, LOOP 반복문의 차이를 설명하고, 각각의 특징을 비교하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain nested control structures and provide example including IF-THEN-CASE-WHILE. (중첩된 제어 구조의 개념을 설명하고, IF-THEN-CASE-WHILE을 모두 포함하는 예제를 작성하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain ITERATE and LEAVE statements with specific usage examples. (ITERATE와 LEAVE 문의 역할과 사용 방법을 설명하시오. 각각의 상황과 예시를 포함하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch11_control_structure CHARACTER SET utf8mb4;
USE ch11_control_structure;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    salary INT
);

-- Insert data (데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 5000000),
(2, 'Sarah Lee', 4000000),
(3, 'David Park', 4500000);

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
```

Submission: Screenshot showing 3 employee records (제출: employees 테이블에 3명 데이터가 모두 보이는 스크린샷)

---

**Question 17** Create and execute procedures using IF-THEN-ELSE and CASE. (IF-THEN-ELSE와 CASE 문을 사용한 프로시저를 작성하고 실행하시오.)

```sql
-- 1. Salary level check using IF-THEN-ELSE (IF-THEN-ELSE로 급여 등급 판정)
CREATE PROCEDURE CheckSalaryLevel (IN emp_id INT)
BEGIN
  DECLARE emp_salary INT;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  IF emp_salary > 4500000 THEN
    SELECT CONCAT(emp_salary, ' - High Salary');
  ELSEIF emp_salary > 4000000 THEN
    SELECT CONCAT(emp_salary, ' - Medium Salary');
  ELSE
    SELECT CONCAT(emp_salary, ' - Low Salary');
  END IF;
END;

CALL CheckSalaryLevel(1);
CALL CheckSalaryLevel(2);

-- 2. Assign grade using CASE (CASE 문으로 등급 할당)
CREATE PROCEDURE AssignGrade (IN emp_id INT, OUT grade CHAR)
BEGIN
  DECLARE emp_salary INT;
  SELECT salary INTO emp_salary FROM employees WHERE employee_id = emp_id;
  
  SET grade = CASE
    WHEN emp_salary >= 5000000 THEN 'A'
    WHEN emp_salary >= 4500000 THEN 'B'
    WHEN emp_salary >= 4000000 THEN 'C'
    ELSE 'D'
  END;
END;

CALL AssignGrade(1, @grade1);
SELECT @grade1;
```

Submission: Screenshot of procedure execution results (제출: 프로시저 실행 결과 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Process data using WHILE loop. (WHILE 반복문을 사용하여 데이터를 처리하시오.)

```sql
-- Create temporary table (임시 테이블 생성)
CREATE TABLE temp_results (
    id INT,
    data VARCHAR(50)
);

-- Insert data using WHILE (WHILE 반복문으로 데이터 삽입)
CREATE PROCEDURE InsertTestData (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  WHILE i <= count DO
    INSERT INTO temp_results VALUES (i, CONCAT('Data_', i));
    SET i = i + 1;
  END WHILE;
END;

CALL InsertTestData(5);
SELECT * FROM temp_results;

-- REPEAT loop (REPEAT 반복문)
CREATE PROCEDURE InsertTestDataRepeat (IN count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  REPEAT
    INSERT INTO temp_results VALUES (i + 5, CONCAT('DataR_', i));
    SET i = i + 1;
  UNTIL i > 5
  END REPEAT;
END;

CALL InsertTestDataRepeat(5);
SELECT * FROM temp_results;
```

Submission: Screenshot of final temp_results table (제출: temp_results 테이블의 최종 결과 스크린샷)

---

**Question 19** Create procedure with nested control structures. (중첩된 제어 구조를 사용한 프로시저를 작성하고 실행하시오.)

```sql
-- Create analysis table (분석 테이블 생성)
CREATE TABLE salary_analysis (
    emp_id INT,
    emp_name VARCHAR(30),
    salary INT,
    grade CHAR,
    status VARCHAR(30)
);

-- Procedure using nested IF-CASE (중첩된 IF-CASE를 사용한 프로시저)
CREATE PROCEDURE AnalyzeSalary (IN emp_id INT)
BEGIN
  DECLARE emp_name VARCHAR(30);
  DECLARE emp_salary INT;
  DECLARE grade CHAR;
  DECLARE status VARCHAR(30);
  
  SELECT name, salary INTO emp_name, emp_salary FROM employees WHERE employee_id = emp_id;
  
  -- IF statement for condition check (IF 문으로 조건 확인)
  IF emp_salary >= 4000000 THEN
    -- CASE to assign grade if salary sufficient (CASE로 등급 할당)
    SET grade = CASE
      WHEN emp_salary >= 5000000 THEN 'A'
      WHEN emp_salary >= 4500000 THEN 'B'
      ELSE 'C'
    END;
    SET status = 'Normal';
  ELSE
    SET grade = 'D';
    SET status = 'Needs Raise';
  END IF;
  
  INSERT INTO salary_analysis VALUES (emp_id, emp_name, emp_salary, grade, status);
END;

CALL AnalyzeSalary(1);
CALL AnalyzeSalary(2);
CALL AnalyzeSalary(3);

SELECT * FROM salary_analysis;
```

Submission: Screenshot of salary_analysis results (제출: salary_analysis 테이블의 분석 결과 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex control structure procedures. (다음의 복잡한 제어 구조 프로시저를 작성하고 실행하시오.)

```
Requirements:

1. Procedure using LOOP and LEAVE
   - Create labeled LOOP
   - Exit with LEAVE on condition
   - Limit iterations

2. Procedure using ITERATE
   - Skip iterations on condition
   - Conditional filtering
   - Selective data processing

3. Nested loops
   - IF-CASE within WHILE
   - Classify data by department/salary range
   - Process on multiple conditions

4. Execute and verify
   - Execute each procedure
   - Verify result data
   - Check conditions

Submission:
   - SQL code for each procedure
   - Execution result screenshot for each
   - Created table data after execution

요구사항:

1. LOOP와 LEAVE를 사용한 프로시저
   - 라벨을 붙인 LOOP 생성
   - 특정 조건에서 LEAVE로 탈출
   - 반복 횟수 제한

2. ITERATE를 활용한 프로시저
   - 특정 조건에서 반복 건너뛰기
   - 조건 필터링
   - 선택적 데이터 처리

3. 중첩된 반복문
   - WHILE 내에 IF-CASE 포함
   - 부서별/급여 범위별 데이터 분류
   - 여러 조건에 따른 처리

4. 프로시저 실행 및 결과 검증
   - 각 프로시저의 실행
   - 결과 데이터 확인
   - 조건 검증
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                               |
| :------: | :----: | :-------------------------------------------------------- |
|    1    |   ②   | Correct IF-THEN-ELSE syntax (올바른 문법)                 |
|    2    |   ②   | Simple CASE: CASE variable WHEN (간단한 형태)             |
|    3    |   ②   | WHILE checks condition first (조건을 먼저 확인)           |
|    4    |   ③   | REPEAT executes at least once (무조건 1번 실행)           |
|    5    |   ③   | Exit with labeled LOOP using LEAVE (LEAVE로 탈출)         |
|    6    |   ③   | Only ① correct ELSEIF syntax (①만 올바름)               |
|    7    |   ②   | Searched CASE: CASE WHEN condition (검색 형태)            |
|    8    |   ④   | Both possible nesting (둘 다 가능한 중첩)                 |
|    9    |   ②   | ITERATE skips current iteration (현재 반복을 건너뜀)      |
|    10    |   ①   | Label identifies, LEAVE exits (라벨로 식별, LEAVE로 탈출) |

---

## Short Answer Model Answers (5 Questions)

### Question 11: IF-THEN-ELSE and ELSEIF

**Model Answer (모범 답안):**

```
IF-THEN-ELSE Structure:

IF condition THEN
  -- True condition
  statement1;
ELSEIF condition2 THEN
  -- condition2 true
  statement2;
ELSE
  -- All conditions false
  statement3;
END IF;

ELSEIF Usage:
- Required for 3+ branches
- Checks conditions in order
- Executes first true branch
- Skips remaining conditions

Example:
IF score >= 90 THEN SET grade = 'A';
ELSEIF score >= 80 THEN SET grade = 'B';
ELSEIF score >= 70 THEN SET grade = 'C';
ELSE SET grade = 'D';
END IF;
```

---

### Question 12: Two CASE Forms

**Model Answer (모범 답안):**

```
1. Simple CASE
CASE variable
  WHEN value1 THEN statement1;
  WHEN value2 THEN statement2;
  ELSE statement_default;
END CASE;

Characteristics:
- Compare one variable to multiple values
- Only = comparison possible
- Fixed value mapping

Usage:
- Month number → month name
- Code → description
- Fixed value mapping

Example:
SET month_name = CASE month
  WHEN 1 THEN 'January'
  WHEN 2 THEN 'February'
  ELSE 'Unknown'
END;

2. Searched CASE
CASE
  WHEN condition1 THEN statement1;
  WHEN condition2 THEN statement2;
  ELSE statement_default;
END CASE;

Characteristics:
- Complex conditions possible
- Use >, <, AND, OR
- Range checking possible

Usage:
- Grade by range
- Multiple conditions
- Complex business logic

Example:
SET grade = CASE
  WHEN salary >= 5000000 THEN 'A'
  WHEN salary >= 4000000 AND dept = 1 THEN 'B'
  WHEN salary < 3000000 OR dept = 3 THEN 'D'
  ELSE 'C'
END;
```

---

### Question 13: Loop Comparison

**Model Answer (모범 답안):**

```
1. WHILE (Check condition first)
WHILE condition DO
  statement;
END WHILE;

Characteristics:
- Check condition → execute
- Can execute 0 times if false
- General-purpose loop

2. REPEAT-UNTIL (Execute then check)
REPEAT
  statement;
UNTIL condition
END REPEAT;

Characteristics:
- Always executes at least once
- Check after execution
- Like do-while

3. LOOP (Infinite, exit with LEAVE)
[label:] LOOP
  statement;
  IF condition THEN
    LEAVE label;
  END IF;
END LOOP;

Characteristics:
- Always loops
- Explicit exit with LEAVE
- Label required

Comparison:
WHILE: Pre-check, 0 possible
REPEAT: Minimum 1 execution
LOOP: Infinite, explicit exit
```

---

### Question 14: Nested Control Structures

**Model Answer (모범 답안):**

```
Concept:
- Control structure within control structure
- IF within CASE, CASE within IF, etc.
- Implement complex logic

Example:
CREATE PROCEDURE complex_logic ()
BEGIN
  DECLARE i INT DEFAULT 1;
  
  -- WHILE loop
  WHILE i <= 5 DO
    -- IF statement
    IF i MOD 2 = 0 THEN
      -- CASE statement
      SET grade = CASE i
        WHEN 2 THEN '2: Even'
        WHEN 4 THEN '4: Even'
        ELSE 'Other'
      END;
    ELSE
      SET grade = CONCAT(i, ': Odd');
    END IF;
  
    INSERT INTO results VALUES (i, grade);
    SET i = i + 1;
  END WHILE;
END;
```

---

### Question 15: ITERATE and LEAVE

**Model Answer (모범 답안):**

```
1. ITERATE Statement
Role:
- Skip current iteration
- Loop counter increments but skip rest of code
- Move to next iteration

Usage:
- Filter specific data
- Exclude specific values
- Distinguish even/odd

Example:
DECLARE i INT DEFAULT 0;
WHILE i < 10 DO
  SET i = i + 1;
  IF MOD(i, 2) = 0 THEN
    ITERATE;  -- Skip even numbers
  END IF;
  INSERT INTO odd_numbers VALUES (i);
END WHILE;

2. LEAVE Statement
Role:
- Completely exit loop
- Exit specific loop by label
- Skip remaining iterations

Usage:
- Exit on condition
- Limit max iterations
- Exit on error

Example:
my_loop: LOOP
  SET i = i + 1;
  IF i > 10 THEN
    LEAVE my_loop;  -- Complete exit
  END IF;
  INSERT INTO data VALUES (i);
END LOOP;

3. ITERATE vs LEAVE
ITERATE: Skip current, continue loop
LEAVE: Complete loop exit
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Employee Table Creation

**Completion Criteria (완료 기준):**

✅ ch11_control_structure database created
✅ employees table created
✅ 3 employees data inserted

---

### Question 17: Conditional Procedures

**Completion Criteria (완료 기준):**

✅ IF-THEN-ELSE procedure executed
✅ CASE procedure executed
✅ Results verified for each employee

---

### Question 18: Loop Procedures

**Completion Criteria (완료 기준):**

✅ WHILE inserts 5 rows
✅ REPEAT inserts additional 5 rows
✅ temp_results shows final 10 rows

---

### Question 19: Nested Control Structure

**Completion Criteria (완료 기준):**

✅ salary_analysis table created
✅ Nested IF-CASE procedure executed
✅ 3 employees analysis results saved

---

### Question 20: Complex Control Structure

**Model Answer (모범 답안):**

```sql
-- 1. LOOP with LEAVE
CREATE TABLE loop_test (
  iteration INT,
  value VARCHAR(50)
);

CREATE PROCEDURE TestLoopLeave ()
BEGIN
  DECLARE i INT DEFAULT 1;
  
  loop_label: LOOP
    IF i > 10 THEN
      LEAVE loop_label;
    END IF;
  
    INSERT INTO loop_test VALUES (i, CONCAT('Iteration_', i));
    SET i = i + 1;
  END LOOP;
END;

CALL TestLoopLeave();
SELECT * FROM loop_test;

-- 2. ITERATE loop
CREATE TABLE filtered_data (
  num INT,
  category VARCHAR(30)
);

CREATE PROCEDURE TestIterateLoop (IN max_val INT)
BEGIN
  DECLARE i INT DEFAULT 0;
  
  filter_loop: LOOP
    SET i = i + 1;
    IF i > max_val THEN
      LEAVE filter_loop;
    END IF;
  
    -- Skip multiples of 5
    IF i % 5 = 0 THEN
      ITERATE filter_loop;
    END IF;
  
    INSERT INTO filtered_data VALUES (i, 
      CASE 
        WHEN i % 2 = 0 THEN 'Even'
        ELSE 'Odd'
      END
    );
  END LOOP;
END;

CALL TestIterateLoop(20);
SELECT * FROM filtered_data;

-- 3. Nested loops
CREATE TABLE nested_results (
  row_num INT,
  col_num INT,
  value VARCHAR(50)
);

CREATE PROCEDURE NestedControlStructure (IN row_count INT, IN col_count INT)
BEGIN
  DECLARE i INT DEFAULT 1;
  DECLARE j INT DEFAULT 1;
  DECLARE category VARCHAR(50);
  
  WHILE i <= row_count DO
    SET j = 1;
    WHILE j <= col_count DO
      SET category = CASE
        WHEN (i * j) % 2 = 0 THEN 'Even'
        ELSE 'Odd'
      END;
    
      INSERT INTO nested_results VALUES (i, j, CONCAT('(', i, ',', j, ')=', category));
      SET j = j + 1;
    END WHILE;
    SET i = i + 1;
  END WHILE;
END;

CALL NestedControlStructure(3, 4);
SELECT * FROM nested_results;
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
