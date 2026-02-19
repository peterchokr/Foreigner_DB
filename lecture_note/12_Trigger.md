# Chapter 12. Trigger

---

## 📖 Class Overview

In this chapter, you will learn about triggers, database objects that automatically execute when specific events occur. You will study how to use triggers that execute automatically before/after INSERT, UPDATE, DELETE to ensure data integrity, automatically record audit logs, and maintain data consistency. The goal is to understand the powerful features and precautions of triggers.

이 장에서는 특정 사건이 발생했을 때 자동으로 실행되는 데이터베이스 객체인 트리거(Trigger)를 학습합니다.    
INSERT, UPDATE, DELETE 이전/이후에 자동으로 실행되는 트리거를 사용하여 데이터 무결성을 보장하고, 감사 로그를 자동으로 기록하며, 데이터 일관성을 유지하는 방법을 다룹니다. 트리거의 강력한 기능과 주의사항을 이해하는 것이 목표입니다.

---

## 📚 Part 1: Theoretical Learning

### 12.1 Trigger Concept

#### What is a Trigger? (트리거란?)

**Trigger** is a stored procedure that automatically executes when INSERT, UPDATE, or DELETE operations occur on specific tables. It's like a "trigger mechanism" that automatically reacts when an event occurs.

트리거(Trigger)는 특정 테이블의 데이터에 INSERT, UPDATE, DELETE 작업이 발생했을 때 자동으로 실행되는 저장 프로시저입니다. 마치 어떤 사건이 발생하면 자동으로 반응하는 "촉발 장치"와 같습니다.

**Daily Life Analogy (일상생활의 비유):**

- Fire alarm system: Fire detector automatically sounds alarm when detecting heat (비상 경보 시스템: 화재 감지기가 열을 감지하면 자동으로 경보가 울림)
- Automatic door: Door opens automatically when someone approaches (자동 문: 사람이 다가가면 자동으로 열림)
- Database trigger: When data changes, specific tasks automatically execute (데이터베이스 트리거: 데이터가 변경되면 자동으로 특정 작업 실행)

#### Characteristics of Trigger (트리거의 특징)

**1. Automatic Execution (자동 실행)**

- No need for user to explicitly call (사용자가 명시적으로 호출할 필요가 없음)
- Automatically activates when INSERT/UPDATE/DELETE occurs (INSERT/UPDATE/DELETE가 발생하면 자동으로 작동)

**2. Ensure Data Integrity (데이터 무결성 보장)**

- Prevent incorrect data input (잘못된 데이터 입력 방지)
- Automatically validate data rules (데이터 규칙 자동 검증)
- Maintain consistent state (일관성 있는 상태 유지)

**3. Monitoring and Audit Function (감시 및 감사 기능)**

- Automatically record all data changes (모든 데이터 변경 자동 기록)
- Track who changed what data and when (누가 언제 어떤 데이터를 변경했는지 추적 가능)
- Implement security audit (보안 감사 Audit 구현)

**4. Automate Complex Business Rules (복잡한 비즈니스 규칙 자동화)**

- Eliminate possibility of user error (사용자의 실수 가능성 제거)
- Enforce business rules at database level (비즈니스 규칙을 데이터베이스 수준에서 강제)

#### Main Use Cases of Trigger (트리거의 주요 사용 사례)

✓ **Automatic Audit Log Recording (감사 로그 자동 기록)**

- Record when and who changed what data (언제 누가 어떤 데이터를 변경했는지 기록)

✓ **Data Validation and Constraint Enforcement (데이터 검증 및 제약 조건 강제)**

- Salary cannot be negative (급여는 음수가 될 수 없다)
- Price must be 0 or more (가격은 0 이상이어야 한다)

✓ **Automatic Calculation and Update (자동 계산 및 업데이트)**

- Inventory automatically decreases when ordering (주문 시 재고 자동 감소)
- Total amount automatically calculated (합계 금액 자동 계산)

✓ **Data Synchronization (데이터 동기화)**

- Changes in one table automatically reflected in another (한 테이블의 변경이 다른 테이블에 자동 반영)

✓ **Related Table Automatic Update (관련 테이블 자동 업데이트)**

- When employee deleted, related salary records also deleted (직원 삭제 시 관련 급여 기록도 삭제)

---

## 📚 Part 2: Sample Data and Table Structure

### Essential Setup for Practice (실습을 위한 필수 설정)

Create all tables and sample data needed for Part 3 examples to work properly.

Part 3의 예제들이 모두 작동하도록 필요한 모든 테이블과 샘플 데이터를 생성합니다.

```sql
-- =====================================================
-- Create database and basic setup (데이터베이스 생성 및 기본 설정)
-- =====================================================
CREATE DATABASE ch12_trigger CHARACTER SET utf8mb4;
USE ch12_trigger;

-- =====================================================
-- 1. employees table (Employee information) (employees 테이블 직원 정보)
-- =====================================================
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    salary DECIMAL(10, 2),
    position VARCHAR(50),
    department VARCHAR(50),
    hire_date DATE,
    emp_level VARCHAR(20),
    job_title VARCHAR(50),
    last_modified TIMESTAMP
);

-- Sample data (샘플 데이터)
INSERT INTO employees (name, salary, position, department, hire_date, emp_level, job_title)
VALUES 
('Alex Johnson', 5000000, 'Manager', 'Development', '2020-01-15', 'Level 3', 'Development Manager'),
('Sarah Williams', 4000000, 'Associate', 'Sales', '2020-06-20', 'Level 2', 'Sales Representative'),
('David Brown', 4500000, 'Associate', 'Planning', '2019-03-10', 'Level 2', 'Planner');

-- =====================================================
-- 2. salary_history table (Salary change history) (salary_history 테이블 급여 변경 이력)
-- =====================================================
CREATE TABLE salary_history (
    history_id INT PRIMARY KEY AUTO_INCREMENT,
    emp_id INT,
    emp_name VARCHAR(50),
    old_salary DECIMAL(10, 2),
    new_salary DECIMAL(10, 2),
    change_reason VARCHAR(100),
    changed_at TIMESTAMP
);

-- =====================================================
-- 3. salary_change_percent table (Salary change rate) (salary_change_percent 테이블 급여 변경 비율)
-- =====================================================
CREATE TABLE salary_change_percent (
    id INT PRIMARY KEY AUTO_INCREMENT,
    emp_id INT,
    change_percent DECIMAL(5, 2),
    changed_at TIMESTAMP
);

-- =====================================================
-- 4. audit_log table (Audit log) (audit_log 테이블 감사 로그)
-- =====================================================
CREATE TABLE audit_log (
    log_id INT PRIMARY KEY AUTO_INCREMENT,
    table_name VARCHAR(50),
    operation VARCHAR(10),
    column_name VARCHAR(50),
    old_value VARCHAR(255),
    new_value VARCHAR(255),
    changed_at TIMESTAMP
);

-- =====================================================
-- 5. products table (Product information) (products 테이블 상품 정보)
-- =====================================================
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100),
    price DECIMAL(10, 2),
    product_code VARCHAR(50),
    created_at TIMESTAMP
);

-- =====================================================
-- 6. employee_archive table (Retired employee storage) (employee_archive 테이블 퇴직 직원 보관)
-- =====================================================
CREATE TABLE employee_archive (
    archive_id INT PRIMARY KEY AUTO_INCREMENT,
    emp_id INT,
    emp_name VARCHAR(50),
    salary DECIMAL(10, 2),
    department VARCHAR(50),
    hire_date DATE,
    job_title VARCHAR(50),
    archived_at TIMESTAMP,
    archived_reason VARCHAR(100)
);

-- =====================================================
-- 7. salary_history_archive table (Salary history storage) (salary_history_archive 테이블 급여 이력 보관)
-- =====================================================
CREATE TABLE salary_history_archive (
    archive_history_id INT,
    emp_id INT,
    emp_name VARCHAR(50),
    old_salary DECIMAL(10, 2),
    new_salary DECIMAL(10, 2),
    change_reason VARCHAR(100),
    changed_at TIMESTAMP
);
```

### Verify Database Creation (데이터베이스 생성 확인)

Check that all tables are created correctly with the following commands:

다음 명령으로 모든 테이블이 정상 생성되었는지 확인하세요:

```sql
-- View all tables (모든 테이블 목록 확인)
SHOW TABLES;

-- Check employees table data (employees 테이블 데이터 확인)
SELECT * FROM employees;
```

---

## 📚 Part 3: Learning and Practice

### 12.2 Trigger Creation Syntax

#### Basic Syntax (기본 문법)

```sql
CREATE TRIGGER trigger_name
BEFORE/AFTER INSERT/UPDATE/DELETE ON table_name
FOR EACH ROW
BEGIN
  -- Trigger body (트리거 본문)
  trigger_statements;
END;
```

#### Meaning of Each Part (각 부분의 의미)

**Trigger Name (trigger_name 트리거 이름)**

- Unique name to distinguish trigger (트리거를 구분하는 고유 이름)
- Convention: `{time_point}_{operation}_{table_name}` format ({시점}_{작업}_{테이블명} 형식)

**Time Point (BEFORE/AFTER 시점)**

- **BEFORE**: Execute before data change (validation, value conversion, rejection) (데이터 변경 전에 실행 검증, 값 변환, 거부)
- **AFTER**: Execute after data change (log recording, cascade tasks) (데이터 변경 후에 실행 로그 기록, 연쇄 작업)

---

### 12.3 NEW and OLD

#### NEW and OLD Concept (NEW와 OLD의 개념)

In triggers, you can access data before and after changes using special variables **NEW** and **OLD**.

트리거 내에서는 NEW와 OLD라는 특수한 변수를 사용하여 변경 전후의 데이터에 접근할 수 있습니다.

#### Usable References by Operation Type (각 작업 유형별 사용 가능한 참조)

| Operation | NEW Available | OLD Available |
|-----------|---------------|---------------|
| INSERT | ✓ Yes | ✗ No |
| UPDATE | ✓ Yes | ✓ Yes |
| DELETE | ✗ No | ✓ Yes |

#### Real Example (실제 예시)

```sql
-- Trigger to track employee salary changes (직원 급여 변경을 추적하는 트리거)
DELIMITER //
CREATE TRIGGER salary_update_log
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  -- OLD.salary: Salary before modification (수정 전 급여)
  -- NEW.salary: Salary after modification (수정 후 급여)
  
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_history 
    (emp_id, emp_name, old_salary, new_salary, change_reason, changed_at)
    VALUES (NEW.employee_id, NEW.name, OLD.salary, NEW.salary, 'Regular Raise', NOW());
  END IF;
END //
DELIMITER ;

-- Test: Change salary (테스트: 급여 변경)
UPDATE employees SET salary = 5500000 WHERE employee_id = 1;

-- Verify result (결과 확인)
SELECT * FROM salary_history;
```

---

### 12.4 BEFORE Trigger - Data Validation & Conversion

#### Role of BEFORE Trigger (BEFORE 트리거의 역할)

Validate and convert data **before** it is actually saved to database.

데이터베이스에 실제로 저장되기 전에 데이터를 검증하고 필요하면 변환합니다.

#### Practical Example 1: Data Validation (실전 예제 1: 데이터 검증)

```sql
-- Enforce rule that salary must always be positive (급여는 반드시 양수여야 한다는 규칙 강제)
DELIMITER //
CREATE TRIGGER validate_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  -- Validate negative salary (음수 급여 검증)
  IF NEW.salary < 0 THEN
    SIGNAL SQLSTATE '45000'
    SET MESSAGE_TEXT = 'Salary cannot be negative. Please enter positive value.';
  END IF;
  
  -- Validate salary ceiling (CEO only) (급여 상한 검증 CEO만)
  IF NEW.salary > 100000000 AND NEW.position != 'CEO' THEN
    SIGNAL SQLSTATE '45000'
    SET MESSAGE_TEXT = 'Salary of 100 million or more only available for CEO.';
  END IF;
END //
DELIMITER ;

-- Test 1: Attempt to insert negative salary (should fail) (테스트 1: 음수 급여 입력 실패해야 함)
INSERT INTO employees (name, salary, position, department) 
VALUES ('Test', -100000, 'Associate', 'Development');
-- ❌ Error: Salary cannot be negative (오류: 급여는 음수일 수 없습니다)

-- Test 2: Insert normal salary (should succeed) (테스트 2: 정상 급여 입력 성공)
INSERT INTO employees (name, salary, position, department) 
VALUES ('Lee Sunsin', 5000000, 'Associate', 'Development');
-- ✅ Success
```

#### Practical Example 2: Automatic Value Setting (실전 예제 2: 자동 값 설정)

```sql
-- Automatically set hire date when registering new employee (신규 직원 등록 시 자동으로 등록일 설정)
DELIMITER //
CREATE TRIGGER set_hire_date_on_insert
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
  -- If hire_date not specified, automatically set to today (hire_date가 지정되지 않으면 오늘 날짜 자동 설정)
  IF NEW.hire_date IS NULL THEN
    SET NEW.hire_date = (CURDATE());
  END IF;
  
  -- If emp_level not specified, automatically set to 'Level 1' (등급이 지정되지 않으면 'Level 1' 자동 설정)
  IF NEW.emp_level IS NULL THEN
    SET NEW.emp_level = 'Level 1';
  END IF;
END //
DELIMITER ;

-- Test: Insert without specifying hire_date and emp_level (테스트: hire_date와 emp_level을 지정하지 않고 삽입)
INSERT INTO employees (name, salary, position, department) 
VALUES ('Michael Wilson', 4000000, 'Staff', 'Marketing');

-- Verify result (결과 확인)
SELECT name, hire_date, emp_level FROM employees WHERE name = 'Michael Wilson';
-- hire_date: Today's date (automatically set) (현재 날짜 자동 설정)
-- emp_level: Level 1 (automatically set) (Level 1 자동 설정)
```

---

### 12.5 AFTER Trigger - Log Recording & Cascade Tasks

#### Role of AFTER Trigger (AFTER 트리거의 역할)

Perform follow-up tasks such as log recording, email sending, updating other tables **after** data is actually saved.

데이터가 실제로 저장된 후에 로그 기록, 이메일 발송, 다른 테이블 업데이트 등의 후속 작업을 수행합니다.

#### Practical Example: Record Audit Log (실전 예제: 감사 로그 기록)

```sql
-- Record all changes to employee information in log table (직원 정보 변경 시 모든 변경사항을 로그 테이블에 기록)
DELIMITER //
CREATE TRIGGER audit_employee_update
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  -- Create separate log for each changed item (변경된 항목마다 별도의 로그 생성)
  IF NEW.name != OLD.name THEN
    INSERT INTO audit_log (table_name, operation, column_name, old_value, new_value, changed_at)
    VALUES ('employees', 'UPDATE', 'name', OLD.name, NEW.name, NOW());
  END IF;
  
  IF NEW.salary != OLD.salary THEN
    INSERT INTO audit_log (table_name, operation, column_name, old_value, new_value, changed_at)
    VALUES ('employees', 'UPDATE', 'salary', OLD.salary, NEW.salary, NOW());
  END IF;
  
  IF NEW.department != OLD.department THEN
    INSERT INTO audit_log (table_name, operation, column_name, old_value, new_value, changed_at)
    VALUES ('employees', 'UPDATE', 'department', OLD.department, NEW.department, NOW());
  END IF;
END //
DELIMITER ;

-- Test: Update employee information (테스트: 직원 정보 업데이트)
UPDATE employees 
SET name = 'Alex JohnsonJr',
    salary = 5500000,
    department = 'Planning'
WHERE employee_id = 1;

-- Verify result (결과 확인)
SELECT * FROM audit_log;
-- 3 log records automatically created (3개의 로그 레코드가 자동으로 생성됨)
```

---

### 12.6 INSERT Trigger

#### Purpose of INSERT Trigger (INSERT 트리거의 용도)

Trigger executed when new data is added to table.

새로운 데이터가 테이블에 추가될 때 실행되는 트리거입니다.

#### Practical Example: Automatic Code Generation (실전 예제: 자동 코드 생성)

```sql
-- Automatically generate product code when product added (상품이 추가될 때 자동으로 상품 코드 생성)
DELIMITER //
CREATE TRIGGER generate_product_code
BEFORE INSERT ON products
FOR EACH ROW
BEGIN
  -- Format: YYYY-MM + 4-digit serial number (형식: YYYY-MM + 4자리 일련번호)
  SET NEW.product_code = CONCAT(
    DATE_FORMAT(NOW(), '%Y-%m'),
    '-',
    LPAD(NEW.product_id, 4, '0')
  );
  
  -- Automatically set product registration time (상품 등록 시간 자동 설정)
  SET NEW.created_at = NOW();
END //
DELIMITER ;

-- Test: Add product (테스트: 상품 추가)
INSERT INTO products (product_name, price) 
VALUES ('Laptop', 1500000);

-- Verify result (결과 확인)
SELECT * FROM products;
-- product_code: 2024-01-0001 (automatically generated) (자동 생성)
-- created_at: Current time (automatically set) (현재 시간 자동 설정)
```

---

### 12.7 UPDATE Trigger

#### Purpose of UPDATE Trigger (UPDATE 트리거의 용도)

Track change history when data is modified or perform data validation.

데이터가 수정될 때 변경 이력을 추적하거나 데이터 검증을 수행합니다.

#### Practical Example 1: Track Change History (실전 예제 1: 변경 이력 추적)

```sql
-- Record change history every time salary changes (급여 변경이 있을 때마다 이력 기록)
DELIMITER //
CREATE TRIGGER track_salary_changes
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  -- Only record if salary actually changed (급여가 실제로 변경된 경우만 기록)
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_history 
    (emp_id, emp_name, old_salary, new_salary, change_reason, changed_at)
    VALUES (
      NEW.employee_id,
      NEW.name,
      OLD.salary,
      NEW.salary,
      'Regular Raise',
      NOW()
    );
  
    -- Calculate and record salary change percentage (급여 변경 비율 계산)
    INSERT INTO salary_change_percent
    (emp_id, change_percent, changed_at)
    VALUES (
      NEW.employee_id,
      ROUND((NEW.salary - OLD.salary) / OLD.salary * 100, 2),
      NOW()
    );
  END IF;
END //
DELIMITER ;

-- Test: Update salary (테스트: 급여 업데이트)
UPDATE employees SET salary = 5500000 WHERE employee_id = 2;

-- Verify result (결과 확인)
SELECT * FROM salary_history;
SELECT * FROM salary_change_percent;
```

#### Practical Example 2: Validate Data Before Modification (실전 예제 2: 수정 전 데이터 검증)

```sql
-- Prevent excessive salary increases (급여 인상이 과도하지 않도록 제한)
DELIMITER //
CREATE TRIGGER validate_salary_increase
BEFORE UPDATE ON employees
FOR EACH ROW
BEGIN
  DECLARE raise_percent DECIMAL(5, 2);
  
  -- Calculate salary raise percentage (급여 인상 비율 계산)
  SET raise_percent = ROUND((NEW.salary - OLD.salary) / OLD.salary * 100, 2);
  
  -- Cannot increase more than 50% at once (한 번에 50% 이상 인상 불가)
  IF raise_percent > 50 THEN
    SIGNAL SQLSTATE '45000'
    SET MESSAGE_TEXT = 'Salary cannot be increased more than 50% at once.';
  END IF;
  
  -- Salary basically cannot decrease (except demotion) (기본적으로 급여는 감소할 수 없음 강등 제외)
  IF NEW.salary < OLD.salary AND NEW.position = OLD.position THEN
    SIGNAL SQLSTATE '45000'
    SET MESSAGE_TEXT = 'Cannot decrease salary at same position.';
  END IF;
  
  -- Automatically update modification time (수정 시간 자동 업데이트)
  SET NEW.last_modified = NOW();
END //
DELIMITER ;

-- Test 1: Attempt to increase by 50% or more (should fail) (테스트 1: 50% 이상 인상 시도 실패)
UPDATE employees SET salary = 8000000 WHERE employee_id = 3;
-- ❌ Error (오류)

-- Test 2: Normal raise (should succeed) (테스트 2: 정상 인상 성공)
UPDATE employees SET salary = 5100000 WHERE employee_id = 3;
-- ✅ Success, last_modified automatically updated (성공, last_modified 자동 업데이트)
```

---

### 12.8 DELETE Trigger

#### Purpose of DELETE Trigger (DELETE 트리거의 용도)

Archive important data or clean up related information when data is deleted.

데이터 삭제 시 중요한 데이터를 아카이브하거나 관련 정보를 정리합니다.

#### Practical Example: Archive Before Delete (실전 예제: 삭제 전 아카이브)

```sql
-- Save all information to archive table before deleting employee (직원 삭제 전 모든 정보를 아카이브 테이블에 저장)
DELIMITER //
CREATE TRIGGER archive_employee_before_delete
BEFORE DELETE ON employees
FOR EACH ROW
BEGIN
  -- Preserve deleted employee information (삭제되는 직원 정보 보관)
  INSERT INTO employee_archive (
    emp_id, emp_name, salary, department, hire_date, 
    job_title, archived_at, archived_reason
  )
  VALUES (
    OLD.employee_id,
    OLD.name,
    OLD.salary,
    OLD.department,
    OLD.hire_date,
    OLD.job_title,
    NOW(),
    'Retirement'
  );
  
  -- Archive salary records related to deleted employee (삭제되는 직원과 관련된 급여 기록도 아카이브)
  INSERT INTO salary_history_archive
  SELECT * FROM salary_history 
  WHERE emp_id = OLD.employee_id;
END //
DELIMITER ;

-- Test: Delete employee (테스트: 직원 삭제)
DELETE FROM employees WHERE employee_id = 1;

-- Verify result (결과 확인)
SELECT * FROM employee_archive;
SELECT * FROM salary_history_archive;
```

---

### 12.9 View and Drop Trigger

#### How to View Triggers (트리거 조회 방법)

```sql
-- View all triggers in current database (현재 데이터베이스의 모든 트리거 조회)
SHOW TRIGGERS;

-- View triggers in specific database (특정 데이터베이스의 트리거 조회)
SHOW TRIGGERS FROM ch12_trigger;
```

#### How to Drop Trigger (트리거 삭제 방법)

```sql
-- Safe deletion (ignore if not exists) (안전한 삭제 존재하지 않으면 무시)
DROP TRIGGER IF EXISTS salary_update_log;
```

---

### 12.10 Precautions with Triggers

#### Performance Impact (성능 영향)

**Problems (문제점):**

- Trigger executes for every INSERT/UPDATE/DELETE (모든 INSERT/UPDATE/DELETE마다 트리거 실행)
- Performance degradation with bulk data insertion (대량 데이터 입력 시 성능 저하)

**Countermeasures (대처 방법):**

Temporarily delete trigger then recreate after bulk operations.

```sql
DROP TRIGGER IF EXISTS trigger_name;
CREATE TRIGGER trigger_name ...
```

#### Compatibility Issues (호환성 문제)

**Caution (주의):**

- Trigger syntax differs by database (데이터베이스마다 트리거 문법이 다름)
- MySQL, PostgreSQL, SQL Server all have different syntax (MySQL, PostgreSQL, SQL Server 모두 문법 상이)

#### Other Restrictions (기타 제약사항)

❌ Cannot use OLD value in BEFORE INSERT trigger (BEFORE INSERT 트리거에서 OLD 값 사용 불가)

❌ Cannot use NEW value in AFTER DELETE trigger (AFTER DELETE 트리거에서 NEW 값 사용 불가)

❌ Cannot use COMMIT/ROLLBACK inside trigger (트리거 내에서 COMMIT/ROLLBACK 사용 불가)

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the concept of trigger and present 5 situations where triggers should be used.

트리거의 개념을 설명하고, 사용해야 하는 상황 5가지 제시하세요.

**Assignment 2**: Explain the difference between BEFORE and AFTER triggers and provide practical examples for each.

BEFORE와 AFTER 트리거의 차이를 설명하고, 각각에 대한 실무 예제를 제시하세요.

**Assignment 3**: Summarize the concepts of NEW and OLD references and tabulate when each can be used.

NEW와 OLD 참조의 개념을 설명하고, 각각 사용 가능한 경우를 표로 정리하세요.

**Assignment 4**: Discuss the performance impact of triggers and propose optimization methods. Additionally, explain precautions when using triggers and cascade reaction issues.

트리거의 성능 영향을 논의하고 최적화 방안을 제시하세요. 트리거 사용 시 주의사항과 연쇄 반응 문제도 설명하세요.

**Assignment 5**: Analyze real-world business scenarios and explain when to use triggers versus other database features (stored procedures, views, constraints).

실무 비즈니스 시나리오를 분석하고, 트리거와 다른 데이터베이스 기능(저장프로시저, 뷰, 제약조건)을 언제 사용할지 설명하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Execute all examples from 12.3 to 12.8 in Part 3.

Part 3의 12.3 ~ 12.8 모든 예제를 실행하세요.

**Assignment 2**: Test each trigger operation and verify the results.

각 트리거의 작동을 테스트하고 결과를 확인하세요.

**Assignment 3**: Write 2 or more additional triggers based on different business scenarios.

다양한 비즈니스 시나리오를 기반으로 추가 트리거 2개 이상을 작성하세요.

**Assignment 4**: Create a comprehensive trigger system combining multiple triggers and document the cascade effects.

여러 트리거를 결합한 종합적인 트리거 시스템을 구축하고, 연쇄 반응을 문서화하세요.

**Assignment 5**: Execute all trigger examples from Part 3 and attach result screenshots for each. Additionally, create 5 or more real-world scenario-based triggers and explain their purpose and implementation methods.

Part 3의 모든 트리거 예제를 실행하고, 각 결과를 스크린샷으로 첨부하세요. 추가로 5개 이상의 실무 시나리오 기반 트리거를 만들어 그 목적과 구현 방법을 설명하세요.

**Submission Format**: SQL file (Ch12_Trigger_[StudentID].sql) and result screenshots

제출 형식: SQL 파일 (Ch12_Trigger_[학번].sql) 및 결과 스크린샷

---

Thank you for your attention.

Cho Jeonghyun (peterchokr@gmail.com). Yeungnam University College
