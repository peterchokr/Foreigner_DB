# Chapter 12. Triggers - Practice Problems

Dear students! After completing Chapter 12, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

12장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 12, you should understand the following:

- Trigger concept and operation (트리거의 개념과 작동 원리)
- BEFORE and AFTER trigger differences (BEFORE와 AFTER 트리거의 차이)
- INSERT, UPDATE, DELETE triggers (명령어별 트리거)
- NEW and OLD references (NEW와 OLD 참조)
- Trigger applications (감사 로그, 데이터 검증)
- Trigger creation, query, deletion (생성, 조회, 삭제)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is definition of trigger? (트리거의 정의로 옳은 것은?)

- ① Manually called procedure (수동으로 호출하는 프로시저)
- ② Object automatically executed when DML occurs on table (특정 테이블의 DML 작업이 발생할 때 자동으로 실행)
- ③ Query retrieving data (데이터를 조회하는 쿼리)
- ④ DDL command changing table (테이블을 변경하는 DDL 명령어)

---

**Question 2** Primary purpose of BEFORE trigger? (BEFORE 트리거의 주요 용도는?)

- ① Logging (로그 기록)
- ② Data validation and automatic conversion (데이터 검증 및 자동 변환)
- ③ Perform cascading operations (연쇄 작업 수행)
- ④ Retrieve data (데이터 조회)

---

**Question 3** Primary purpose of AFTER trigger? (AFTER 트리거의 주요 용도는?)

- ① Data validation (데이터 검증)
- ② Modify original data (원본 데이터 변경)
- ③ Logging and cascading operations (로그 기록 및 연쇄 작업)
- ④ Query optimization (쿼리 최적화)

---

**Question 4** Meaning of NEW and OLD in trigger? (트리거에서 NEW와 OLD의 의미는?)

- ① Old and new data (오래된 데이터와 새로운 데이터)
- ② Trigger execution order (트리거 실행 순서)
- ③ Two table names (테이블의 두 가지 이름)
- ④ Database versions (데이터베이스의 버전)

---

**Question 5** What's available in UPDATE trigger? (UPDATE 트리거에서 사용 가능한 것은?)

- ① Only NEW available (NEW만 사용 가능)
- ② Only OLD available (OLD만 사용 가능)
- ③ Both NEW and OLD available (NEW와 OLD 모두 사용 가능)
- ④ Only variables (변수만 사용 가능)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Purpose of this INSERT trigger? (INSERT 트리거의 NEW 참조 목적은?)

```sql
CREATE TRIGGER validate_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary < 0 THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'No negative salary';
  END IF;
END;
```

- ① Insert only negative salary employees (음수 급여 직원만 삽입)
- ② Prevent negative salary data insertion (음수 급여 데이터 삽입 방지)
- ③ Automatic salary calculation (급여 자동 계산)
- ④ Validate all data (모든 데이터 검증)

---

**Question 7** Difference between trigger and procedure? (트리거와 프로시저의 차이는?)

- ① Trigger auto-executes, procedure manual call (트리거는 자동 실행, 프로시저는 수동 호출)
- ② Procedure auto-executes, trigger manual call (프로시저는 자동 실행, 트리거는 수동 호출)
- ③ Functionality completely same (기능이 완전히 같음)
- ④ Only performance differs (성능만 다름)

---

**Question 8** Syntax to delete trigger? (트리거 삭제 명령어는?)

- ① DELETE TRIGGER trigger_name;
- ② DROP TRIGGER trigger_name;
- ③ REMOVE TRIGGER trigger_name;
- ④ TRUNCATE TRIGGER trigger_name;

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Difference between BEFORE INSERT and AFTER INSERT trigger? (BEFORE INSERT와 AFTER INSERT 트리거의 차이는?)

- ① BEFORE validates data, AFTER logs (BEFORE는 검증, AFTER는 로그)
- ② AFTER can modify data (AFTER는 데이터 변경 가능)
- ③ BEFORE logs only (BEFORE는 로그 기록 전용)
- ④ No difference (차이가 없음)

---

**Question 10** Cautions when using triggers? (트리거 사용 시 주의사항은?)

- ① Performance degradation possibility (성능 저하 가능성)
- ② Debugging difficulty (디버깅 어려움)
- ③ Unexpected cascading reactions (예기치 않은 연쇄 반응)
- ④ All ①②③ (모두)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Define trigger and explain why it auto-executes. (트리거의 정의와 자동으로 실행되는 이유를 설명하시오.)

---

**Question 12** Explain differences between BEFORE and AFTER triggers and provide usage examples. (BEFORE 트리거와 AFTER 트리거의 차이를 설명하고, 각각의 활용 사례를 제시하시오.)

---

**Question 13** Explain meaning of NEW and OLD references, and availability for INSERT, UPDATE, DELETE. (NEW와 OLD 참조의 의미를 설명하고, INSERT, UPDATE, DELETE 트리거에서 각각의 사용 가능 여부를 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain audit log trigger concept and design trigger to monitor salary changes on UPDATE. (감사 로그 트리거의 개념을 설명하고, UPDATE 작업 시 급여 변경을 감시하는 트리거를 설계하시오.)

---

## Advanced Level (1 Question)

**Question 15** Analyze advantages and disadvantages of triggers, and explain when to implement with application logic instead. (트리거를 사용할 때의 장점과 단점을 분석하고, 트리거 대신 애플리케이션 로직으로 구현해야 하는 경우를 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch12_trigger CHARACTER SET utf8mb4;
USE ch12_trigger;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    salary INT,
    hire_date DATE
);

-- Create salary_history table (급여 이력 테이블 생성)
CREATE TABLE salary_history (
    history_id INT PRIMARY KEY AUTO_INCREMENT,
    emp_id INT,
    old_salary INT,
    new_salary INT,
    change_date DATETIME
);

-- Insert data (데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 5000000, '2020-01-15'),
(2, 'Sarah Lee', 4000000, '2020-06-20');

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
```

Submission: Screenshot showing 2 employee records (제출: employees 테이블에 2명 데이터가 모두 보이는 스크린샷)

---

**Question 17** Create and execute AFTER UPDATE trigger to monitor salary changes. (UPDATE 이전에 급여 변경을 감시하는 AFTER UPDATE 트리거를 생성하고 실행하시오.)

```sql
-- Create trigger (트리거 생성)
CREATE TRIGGER log_salary_update
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_history (emp_id, old_salary, new_salary, change_date)
    VALUES (NEW.employee_id, OLD.salary, NEW.salary, NOW());
  END IF;
END;

-- Modify salary (급여 수정)
UPDATE employees SET salary = 5500000 WHERE employee_id = 1;

-- Verify results (결과 확인)
SELECT * FROM employees WHERE employee_id = 1;
SELECT * FROM salary_history;
```

Submission: Screenshot of employees and salary_history results (제출: employees와 salary_history 테이블 결과 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Create and execute data validation BEFORE INSERT trigger. (데이터 검증 BEFORE INSERT 트리거를 생성하고 실행하시오.)

```sql
-- Prevent negative salary trigger (음수 급여 방지 트리거)
CREATE TRIGGER validate_salary_insert
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary < 0 THEN
    SIGNAL SQLSTATE '45000'
    SET MESSAGE_TEXT = 'Salary cannot be negative';
  END IF;
  
  -- Auto-set hire_date (hire_date 자동 설정)
  IF NEW.hire_date IS NULL THEN
    SET NEW.hire_date = CURDATE();
  END IF;
END;

-- Normal INSERT (with auto hire_date) (정상 INSERT)
INSERT INTO employees (name, salary) VALUES ('David Park', 4500000);

-- Attempt negative salary (will cause error) (음수 급여 시도)
-- INSERT INTO employees VALUES (NULL, 'Emily Choi', -3000000, '2024-01-01');

-- Verify results (결과 확인)
SELECT * FROM employees WHERE name = 'David Park';
```

Submission: Screenshot showing INSERT result and trigger operation (제출: INSERT 결과 및 트리거 동작 스크린샷)

---

**Question 19** Create BEFORE DELETE trigger to archive data. (DELETE 이전에 데이터를 아카이브하는 BEFORE DELETE 트리거를 생성하고 실행하시오.)

```sql
-- Create archive table (아카이브 테이블 생성)
CREATE TABLE employee_archive (
    archive_id INT PRIMARY KEY AUTO_INCREMENT,
    emp_id INT,
    emp_name VARCHAR(30),
    emp_salary INT,
    deleted_date DATETIME
);

-- Create DELETE trigger (DELETE 트리거 생성)
CREATE TRIGGER archive_employee_delete
BEFORE DELETE ON employees
FOR EACH ROW
BEGIN
  INSERT INTO employee_archive (emp_id, emp_name, emp_salary, deleted_date)
  VALUES (OLD.employee_id, OLD.name, OLD.salary, NOW());
END;

-- Delete employee (직원 삭제)
DELETE FROM employees WHERE employee_id = 2;

-- Verify results (결과 확인)
SELECT * FROM employees;
SELECT * FROM employee_archive;
```

Submission: Screenshot of employees and employee_archive after DELETE (제출: DELETE 후 employees와 employee_archive 결과 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex triggers. (다음의 복잡한 트리거를 작성하고 실행하시오.)

```
Requirements:

1. Salary increase monitoring trigger
   - Log special cases when salary raises ≥20%
   - Limit maximum salary (6,000,000 won max)

2. Data integrity trigger
   - Set default hire_date when adding employee
   - Prevent negative salary input
   - Record salary changes

3. Cascading trigger
   - Handle salary history when deleting employee
   - Record in archive table

4. Trigger verification
   - Query all created triggers
   - Validate trigger operation

Submission:
   - SQL code for each trigger
   - Execution result screenshot for each
   - Trigger query result (SHOW TRIGGERS)

요구사항:

1. 급여 인상 감시 트리거
   - 급여가 20% 이상 인상되면 특별 로그 기록
   - 급여 상한선 제한 (6000000원 초과 불가)

2. 데이터 무결성 트리거
   - 직원 추가 시 기본 hire_date 설정
   - 급여 음수 입력 방지
   - 급여 수정 시 이력 기록

3. 연쇄 트리거
   - 직원 삭제 시 급여 이력도 함께 처리
   - 아카이브 테이블에 기록

4. 트리거 조회 및 검증
   - 생성된 모든 트리거 확인
   - 트리거 동작 검증
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation |
|:--------:|:------:|:-----------|
| 1 | ② | Trigger auto-executes on DML work (자동 실행) |
| 2 | ② | BEFORE validates and converts (검증과 변환) |
| 3 | ③ | AFTER logs and cascades (로그와 연쇄) |
| 4 | ① | NEW/OLD = new/old data (새/구 데이터) |
| 5 | ③ | UPDATE allows both NEW and OLD (모두 가능) |
| 6 | ② | Prevent negative salary insertion (음수 방지) |
| 7 | ① | Trigger auto, procedure manual (자동/수동) |
| 8 | ② | DROP TRIGGER for deletion (DROP으로 삭제) |
| 9 | ① | BEFORE validates, AFTER logs (검증/로그) |
| 10 | ④ | All ①②③ are cautions (모두 주의) |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Trigger Definition

**Model Answer (모범 답안):**

```
Definition:
- Stored procedure that auto-executes when DML (INSERT, UPDATE, DELETE) 
  occurs on specific table

Why Auto-Execute:
- Trigger is database object
- DBMS automatically checks on DML
- Executes without explicit call
- Enforces business rules automatically

Advantages:
- Consistent data integrity
- Eliminates code duplication
- Automates auditing
```

---

### Question 12: BEFORE vs AFTER Triggers

**Model Answer (모범 답안):**

```
BEFORE Trigger:
- Timing: Before DML execution
- References: NEW available (INSERT: NEW only, UPDATE: both)
- Purpose: Data validation, automatic conversion
- Can Deny: SIGNAL can reject operation

Example:
CREATE TRIGGER validate_email
BEFORE INSERT ON users
FOR EACH ROW
BEGIN
  IF NEW.email NOT LIKE '%@%' THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Valid email needed';
  END IF;
END;

AFTER Trigger:
- Timing: After DML execution
- References: Both readable (read-only)
- Purpose: Logging, cascading, notification
- Cannot Deny: Already executed

Example:
CREATE TRIGGER log_user_changes
AFTER UPDATE ON users
FOR EACH ROW
BEGIN
  IF NEW.status != OLD.status THEN
    INSERT INTO audit_log VALUES (...);
  END IF;
END;

Use Cases:
BEFORE: Input validation, defaults, value conversion
AFTER: Audit logs, statistics, auto-updates
```

---

### Question 13: NEW and OLD References

**Model Answer (모범 답안):**

```
NEW:
- Meaning: New values to insert or modify
- INSERT trigger: NEW available (new data)
- UPDATE trigger: NEW available (modified value)
- DELETE trigger: NEW unavailable

OLD:
- Meaning: Values before modification or deletion
- INSERT trigger: OLD unavailable
- UPDATE trigger: OLD available (original value)
- DELETE trigger: OLD available (deleted value)

Availability:
             | NEW | OLD |
INSERT       |  ○ |  ✗ |
UPDATE       |  ○ |  ○ |
DELETE       |  ✗ |  ○ |

Example:
-- Detect UPDATE changes
IF NEW.salary != OLD.salary THEN
  -- Record salary change
END IF;

-- Archive before DELETE
INSERT INTO archive SELECT OLD.*;
```

---

### Question 14: Audit Log Trigger Design

**Model Answer (모범 답안):**

```
Concept:
- Trigger recording all data changes
- Tracks when, who, what changed
- Database security and monitoring

Design (Salary Change Monitoring):

CREATE TABLE salary_audit (
  audit_id INT PRIMARY KEY AUTO_INCREMENT,
  emp_id INT,
  old_salary INT,
  new_salary INT,
  change_date DATETIME,
  change_percent DECIMAL(5,2)
);

CREATE TRIGGER track_salary_changes
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_audit VALUES (
      NULL,
      NEW.employee_id,
      OLD.salary,
      NEW.salary,
      NOW(),
      ROUND((NEW.salary - OLD.salary) / OLD.salary * 100, 2)
    );
  END IF;
END;

Usage:
UPDATE employees SET salary = 5500000 WHERE employee_id = 1;

Verify:
SELECT * FROM salary_audit;
-- All changes, dates, raise percentages recorded
```

---

### Question 15: Trigger Advantages/Disadvantages

**Model Answer (모범 답안):**

```
Advantages:
1. Automate data integrity
   - Enforce business rules
   - Apply to all modification paths

2. Audit and security
   - Record all changes
   - Control permissions

3. Automate complex logic
   - Auto calculations
   - Data synchronization

Disadvantages:
1. Performance degradation
   - Overhead on all DML
   - Cascading triggers worsen

2. Debugging difficulty
   - Hidden logic
   - Unexpected cascades
   - Performance issues hard to trace

3. Maintenance complexity
   - Trigger dependencies
   - Migration difficulty

4. Low reusability
   - Trigger-specific to DB
   - Hard external integration

Trigger vs Application Logic:

Use Triggers:
✅ Need to protect DB itself
✅ Must apply to all paths (direct SQL, app)
✅ Simple validations

Use Application Logic:
✅ Complex business logic
✅ Need external system integration
✅ Easier debugging/testing
✅ Performance optimization needed
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Table Creation

**Completion Criteria (완료 기준):**

✅ ch12_trigger database created
✅ employees, salary_history tables created
✅ 2 employees data inserted

---

### Question 17: UPDATE Trigger

**Completion Criteria (완료 기준):**

✅ log_salary_update trigger created
✅ UPDATE executed (5000000 → 5500000)
✅ salary_history records change history

---

### Question 18: BEFORE INSERT Trigger

**Completion Criteria (완료 기준):**

✅ validate_salary_insert trigger created
✅ Auto hire_date setting confirmed
✅ Negative salary prevention confirmed

---

### Question 19: BEFORE DELETE Trigger

**Completion Criteria (완료 기준):**

✅ archive_employee_delete trigger created
✅ DELETE executed
✅ employee_archive shows backup

---

### Question 20: Complex Trigger Implementation

**Model Answer (모범 답안):**

```sql
-- 1. Salary raise monitoring + cap
CREATE TRIGGER salary_raise_check
BEFORE UPDATE ON employees
FOR EACH ROW
BEGIN
  DECLARE raise_pct INT;
  
  SET raise_pct = ROUND((NEW.salary - OLD.salary) / OLD.salary * 100);
  
  IF NEW.salary > 6000000 THEN
    SET NEW.salary = 6000000;
  END IF;
  
  IF raise_pct > 20 THEN
    INSERT INTO salary_audit (note) VALUES (CONCAT('High raise:', raise_pct, '%'));
  END IF;
END;

-- 2. Data integrity
CREATE TRIGGER employee_insert_validation
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary < 0 THEN
    SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'No negative salary';
  END IF;
  
  IF NEW.hire_date IS NULL THEN
    SET NEW.hire_date = CURDATE();
  END IF;
END;

-- 3. UPDATE history
CREATE TRIGGER salary_history_log
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_history (emp_id, old_salary, new_salary, change_date)
    VALUES (NEW.employee_id, OLD.salary, NEW.salary, NOW());
  END IF;
END;

-- 4. DELETE cascade
CREATE TRIGGER delete_employee_cascade
BEFORE DELETE ON employees
FOR EACH ROW
BEGIN
  INSERT INTO employee_archive SELECT NULL, OLD.*;
  INSERT INTO salary_history VALUES (NULL, OLD.employee_id, OLD.salary, 0, NOW());
END;

-- Verify
SHOW TRIGGERS;
```

---

Thank you for your attention.

Jeonghyun Cho (peterchokr@gmail.com)
Yeungnam University College
