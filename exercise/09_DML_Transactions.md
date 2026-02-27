# Chapter 9. DML and Transactions - Practice Problems

Dear students! After completing Chapter 9, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

9장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 9, you should understand the following:

- DML (Data Manipulation Language) concept (DML의 개념)
- INSERT, UPDATE, DELETE commands (명령어)
- Transaction concept (트랜잭션의 개념)
- COMMIT, ROLLBACK, SAVEPOINT (명령어)
- Data consistency and integrity (데이터 일관성과 무결성)
- Transaction isolation levels (트랜잭션 격리 수준)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** What is DML? (DML의 정의로 옳은 것은?)

- ① Language defining database structure (DDL: CREATE, ALTER) (데이터베이스 구조를 정의하는 언어)
- ② Language for inserting, updating, deleting data (INSERT, UPDATE, DELETE) (데이터를 입력, 수정, 삭제하는 언어)
- ③ Language for querying data (SELECT) (데이터를 조회하는 언어)
- ④ Language managing user permissions (사용자 권한을 관리하는 언어)

---

**Question 2** When columns not specified in INSERT statement? (INSERT 문법에서 열을 명시하지 않으면?)

- ① Error occurs (오류 발생)
- ② Must input all column values in order (모든 열의 값을 순서대로 입력해야 함)
- ③ NULL is inserted (NULL이 입력됨)
- ④ Optional to input (선택적으로 입력 가능)

---

**Question 3** When WHERE clause missing in UPDATE? (UPDATE에서 WHERE 절이 없으면?)

- ① Error occurs (오류 발생)
- ② All rows in column are updated (해당 열의 모든 행이 수정됨)
- ③ Nothing updated (아무것도 수정되지 않음)
- ④ Only last row updated (마지막 행만 수정됨)

---

**Question 4** What is basic characteristic of transaction? (트랜잭션의 기본 특징은?)

- ① Database query only (데이터베이스 조회만 가능)
- ② Multiple SQL treated as single unit of work (여러 SQL을 하나의 작업 단위로 취급)
- ③ Always must succeed (항상 성공해야 함)
- ④ Cannot be undone (되돌릴 수 없음)

---

**Question 5** What is role of COMMIT? (COMMIT의 역할은?)

- ① Undo work (작업 취소)
- ② Save work (transaction ends) (작업 저장 - 트랜잭션 종료)
- ③ Revert to specific point (특정 지점으로 되돌림)
- ④ Begin transaction (트랜잭션 시작)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which syntax is correct for INSERT, UPDATE, DELETE? (INSERT, UPDATE, DELETE 중 올바른 문법은?)

```sql
① INSERT INTO employees (name, salary) VALUES ('Alex Kim', 5000000);

② UPDATE employees SET salary = 6000000 WHERE name = 'Sarah Lee';

③ DELETE FROM employees WHERE employee_id > 10;
```

- ① Correct (올바름)
- ② Correct (올바름)
- ③ Correct (올바름)
- ④ All ①②③ are correct (①②③ 모두 올바름)

---

**Question 7** When is ROLLBACK needed? (ROLLBACK이 필요한 상황은?)

- ① When saving all changes (모든 변경사항을 저장할 때)
- ② When error occurs in transaction, undo all changes (트랜잭션 중 오류 발생 시 모든 변경 취소)
- ③ When undoing specific command only (특정 명령어만 되돌릴 때)
- ④ When initializing database (데이터베이스를 초기화할 때)

---

**Question 8** What is purpose of SAVEPOINT? (SAVEPOINT의 용도는?)

- ① Set transaction start point (트랜잭션 시작 지점 설정)
- ② Set mid-transaction save point for partial rollback (중간에 저장 지점 설정하여 필요시 되돌리기)
- ③ Create database backup (데이터베이스 백업 생성)
- ④ Control multi-user access (여러 사용자 접근 제어)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Why is transaction essential in this situation? (다음 상황에서 트랜잭션이 필수인 이유는?)

"Bank transfer: Withdraw 1,000,000 from account A → Deposit 1,000,000 into account B"

(은행 계좌 송금: A 계좌에서 100만원 출금 → B 계좌에 100만원 입금)

- ① Prevent money loss if withdrawal succeeds but deposit fails (출금만 성공하고 입금 실패 시 돈 손실 방지)
- ② Both operations must succeed or both fail (atomicity) (두 작업이 모두 성공하거나 모두 실패해야 함)
- ③ Save transfer record (송금 기록을 저장하기 위해)
- ④ Both ① and ② (①과 ②)

---

**Question 10** What constraints ensure data consistency? (데이터 일관성을 보장하기 위한 제약조건은?)

- ① Transaction alone is sufficient (트랜잭션만으로 충분)
- ② Constraints (PK, FK, CHECK) and transactions together required (제약조건과 트랜잭션 함께 필요)
- ③ Constraints alone are sufficient (제약조건만으로 충분)
- ④ Log file usage (로그 파일 사용)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain differences between INSERT, UPDATE, DELETE commands. (INSERT, UPDATE, DELETE 명령어의 차이를 설명하시오.)

---

**Question 12** Define transaction and explain necessity, provide 3+ practical cases. (트랜잭션의 정의와 필요성을 설명하고, 실무에서 트랜잭션이 필요한 사례를 3가지 이상 제시하시오.)

---

**Question 13** Explain difference between COMMIT and ROLLBACK, provide examples. (COMMIT과 ROLLBACK의 차이를 설명하고, 각각 사용하는 상황을 예시하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain SAVEPOINT concept and its usage in complex transactions. (SAVEPOINT의 개념을 설명하고, 복잡한 트랜잭션에서 SAVEPOINT를 사용하는 방법을 설명하시오.)

---

## Advanced Level (1 Question)

**Question 15** Explain database ACID properties and their role in transaction management. (데이터베이스의 ACID 특성을 설명하고, 각각이 트랜잭션 관리에서 어떤 역할을 하는지 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch9_dml CHARACTER SET utf8mb4;
USE ch9_dml;

-- Create employees table (직원 테이블 생성)
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30),
    position VARCHAR(20),
    salary INT,
    hire_date DATE
);

-- Insert initial data (초기 데이터 입력)
INSERT INTO employees VALUES
(1, 'Alex Kim', 'Manager', 5000000, '2020-01-15'),
(2, 'Sarah Lee', 'Deputy', 4000000, '2021-03-20'),
(3, 'David Park', 'Staff', 3500000, '2022-06-10');

-- Query all data (모든 데이터 조회)
SELECT * FROM employees;
```

Submission: Screenshot showing all initial employee data (제출: employees 테이블에 초기 데이터가 모두 입력된 스크린샷 1장)

---

**Question 17** Perform and verify the following operations. (다음을 수행하고 결과를 확인하시오.)

```sql
-- 1. INSERT: Add new employee (새 직원 추가)
INSERT INTO employees VALUES
(4, 'Emily Choi', 'Staff', 3200000, '2023-09-01');

SELECT * FROM employees;

-- 2. UPDATE: Salary increase (급여 인상)
UPDATE employees SET salary = 5500000 WHERE name = 'Alex Kim';

SELECT * FROM employees WHERE name = 'Alex Kim';

-- 3. DELETE: Remove employee (직원 삭제)
DELETE FROM employees WHERE employee_id = 3;

SELECT * FROM employees;
```

Submission: Screenshot showing all operation results (제출: 각 단계의 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (2 Questions)

**Question 18** Use transaction to perform the following. (트랜잭션을 사용하여 다음을 수행하시오.)

```sql
-- Start transaction (트랜잭션 시작)
START TRANSACTION;

-- 1. Add multiple employees (여러 직원 추가)
INSERT INTO employees VALUES
(5, 'Michael Kang', 'Deputy', 4300000, '2023-01-15');

INSERT INTO employees VALUES
(6, 'Lisa Park', 'Staff', 3400000, '2023-02-20');

-- 2. Bulk salary increase for staff (사원 급여 5% 인상)
UPDATE employees SET salary = ROUND(salary * 1.05) WHERE position = 'Staff';

-- 3. Verify data (데이터 확인)
SELECT * FROM employees;

-- Commit transaction (트랜잭션 커밋)
COMMIT;

-- Final result verification (최종 결과 확인)
SELECT * FROM employees;
```

Submission: Screenshot of transaction execution results (제출: 트랜잭션 실행 결과 스크린샷)

---

**Question 19** Perform transaction with ROLLBACK. (ROLLBACK을 사용한 트랜잭션을 수행하시오.)

```sql
-- Transaction 1: Normal commit (정상 커밋)
START TRANSACTION;
UPDATE employees SET salary = 6000000 WHERE employee_id = 1;
COMMIT;

-- Transaction 2: Rollback due to error (오류로 인한 ROLLBACK)
START TRANSACTION;
UPDATE employees SET salary = 7000000 WHERE employee_id = 1;
INSERT INTO employees VALUES (7, 'John Lee', 'Manager', 5500000, '2023-03-10');
-- (Assume error) ROLLBACK to undo (오류 발생으로 가정 - ROLLBACK으로 되돌림)
ROLLBACK;

-- Result: emp_id 1 is 6000000, employee 7 not added (결과 확인)
SELECT * FROM employees;
```

Submission: Screenshot of ROLLBACK transaction results (제출: 트랜잭션 ROLLBACK 결과 스크린샷)

---

## Advanced Level (1 Question)

**Question 20** Write and execute complex transaction. (다음의 복잡한 트랜잭션을 작성하고 실행하시오.)

```
Requirements:

1. Organization restructure transaction
   - Add new department
   - Change employee assignments
   - Adjust salaries
   - Cancel all changes if failed

2. SAVEPOINT for partial rollback
   - Set multiple SAVEPOINTs
   - Rollback specific operations
   - Maintain other changes

3. Success/failure scenario testing
   - Normal processing: COMMIT
   - Error processing: ROLLBACK
   - Partial processing: SAVEPOINT + ROLLBACK

4. Data integrity validation
   - Verify data consistency before/after transaction
   - Confirm automatic cancellation on constraint violation

Submission:
   - SQL code for each transaction
   - Execution result screenshot for each step
   - Data comparison before/after transaction

요구사항:

1. 조직 개편 트랜잭션
   - 신규 부서 추가
   - 직원 배치 변경
   - 급여 조정
   - 실패 시 전체 취소

2. SAVEPOINT를 사용한 부분 되돌리기
   - 여러 개의 SAVEPOINT 설정
   - 특정 작업만 되돌리기
   - 나머지는 유지

3. 성공/실패 시나리오 테스트
   - 정상 처리: COMMIT
   - 오류 처리: ROLLBACK
   - 부분 처리: SAVEPOINT + ROLLBACK

4. 데이터 무결성 검증
   - 트랜잭션 전후 데이터 일관성 확인
   - 제약조건 위반 시 자동 취소 확인

제출:
   - 각 트랜잭션의 SQL 코드
   - 각 단계의 실행 결과 스크린샷
   - 트랜잭션 전후 데이터 비교
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                    |
| :------: | :----: | :----------------------------------------------------------------------------- |
|    1    |   ②   | DML: INSERT, UPDATE, DELETE (데이터 변조)                                      |
|    2    |   ②   | Must input all columns in order (모든 열의 값을 순서대로 입력)                 |
|    3    |   ②   | Without WHERE, all rows updated (주의 필요!) (모든 행 수정)                    |
|    4    |   ②   | Transaction treats multiple SQL as single unit (여러 SQL을 하나의 작업 단위로) |
|    5    |   ②   | COMMIT saves work (transaction ends) (작업 저장)                               |
|    6    |   ④   | All ①②③ have correct syntax (①②③ 모두 올바른 문법)                       |
|    7    |   ②   | ROLLBACK undoes all changes on error (오류 시 모든 변경 취소)                  |
|    8    |   ②   | SAVEPOINT sets mid-transaction save point (중간 저장점 설정)                   |
|    9    |   ④   | Both ① and ② correct (①②가 모두 맞음)                                      |
|    10    |   ②   | Constraints and transactions both needed (제약조건과 트랜잭션 함께 필요)       |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Differences Between INSERT, UPDATE, DELETE

**Model Answer (모범 답안):**

```
INSERT (Insert):
- Add new row
- Syntax: INSERT INTO table (cols) VALUES (vals);
- Example: Add new employee

UPDATE (Update):
- Change existing row data
- Syntax: UPDATE table SET col = val WHERE condition;
- Example: Salary increase

DELETE (Delete):
- Delete row
- Syntax: DELETE FROM table WHERE condition;
- Example: Remove terminated employee

Caution:
- WHERE essential for UPDATE, DELETE (prevent full table impact)
- Backup before execution recommended
```

---

### Question 12: Transaction Definition and Necessity

**Model Answer (모범 답안):**

```
Definition:
- Unit of logical work
- Multiple SQL treated as one
- All succeed or all fail (atomicity)

Necessity:
- Ensure data consistency
- Prevent data integrity break from partial success

Practical Cases:

1. Bank Transfer
   Withdraw(A) → Deposit(B)
   Both succeed or both cancel

2. Order Processing
   Decrease inventory → Create order
   Both applied or both cancel

3. HR Record
   Termination processing → Delete salary
   Must process together

4. Inventory Management
   Sales → Inventory decrease → Sales record
   All 3 must succeed for meaning

5. Account Transfer
   Deduct A account → Add B account
   Recover on mid-failure
```

---

### Question 13: COMMIT vs ROLLBACK

**Model Answer (모범 답안):**

```
COMMIT:
- Role: Save transaction changes
- Timing: After work completion
- Effect: Reflect changes in database

ROLLBACK:
- Role: Undo transaction changes
- Timing: On error or intentional undo
- Effect: Restore to pre-transaction state

Usage Situations:

COMMIT Usage:
START TRANSACTION;
INSERT INTO employees ...;
UPDATE employees ...;
-- Verify all work success
COMMIT;

ROLLBACK Usage:
START TRANSACTION;
DELETE FROM employees WHERE ...;
-- Discover deletion mistake
ROLLBACK;  -- Cancel deletion

Data Perspective:
Before COMMIT: Other users can't see changes
After COMMIT: All users confirm changes
After ROLLBACK: No changes occurred
```

---

### Question 14: SAVEPOINT Usage

**Model Answer (모범 답안):**

```
Concept:
- Set save point mid-transaction
- Partial rollback instead of full ROLLBACK

Syntax:
SAVEPOINT savepoint_name;
ROLLBACK TO savepoint_name;

Usage Example:
START TRANSACTION;
  INSERT INTO employees VALUES (...);
  SAVEPOINT sp1;  -- Save point 1
  
  UPDATE employees SET ...;
  SAVEPOINT sp2;  -- Save point 2
  
  DELETE FROM employees WHERE ...;
  -- DELETE error occurs
  ROLLBACK TO sp2;  -- Revert to sp2 (keep UPDATE)
  
COMMIT;

Result:
- INSERT maintained
- UPDATE maintained
- DELETE cancelled

Practical Application:
Divide complex work into stages
Set SAVEPOINT per stage
Rollback on error per stage only
```

---

### Question 15: ACID Properties

**Model Answer (모범 답안):**

```
ACID Properties:

1. Atomicity (원자성)
   - Transaction completely succeeds or completely fails
   - No partial success
   - Role: Ensure data consistency

2. Consistency (일관성)
   - DB maintains consistent state before/after transaction
   - Constraints and rules honored
   - Example: Foreign key integrity maintained

3. Isolation (격리성)
   - Concurrent transactions don't affect each other
   - Each transaction executed independently
   - Isolation levels: READ UNCOMMITTED, READ COMMITTED, etc.

4. Durability (지속성)
   - Data permanently saved after COMMIT
   - Recoverable even on system failure
   - Guaranteed by log files

Role in Transaction Management:

Transfer Example:
A. Atomicity: Complete withdrawal or none (no partial withdrawal)
C. Consistency: Balance never goes negative
I. Isolation: Other withdrawals don't interfere
D. Durability: Withdrawal recorded even if power cuts
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Table Creation with Initial Data

**Completion Criteria (완료 기준):**

✅ ch9_dml database created
✅ employees table created
✅ 3 initial employee records inserted

---

### Question 17: INSERT, UPDATE, DELETE Execution

**Expected Result (예상 결과):**

```
After INSERT: 4 employees (added employee 4)
After UPDATE: Alex Kim salary 5,500,000
After DELETE: 3 employees (David Park deleted)
```

---

### Question 18: Transaction with COMMIT

**Completion Criteria (완료 기준):**

✅ Added 2 new employees
✅ Increased all staff salary 5%
✅ Saved with COMMIT
✅ Final verification

---

### Question 19: Transaction with ROLLBACK

**Model Answer (모범 답안):**

```sql
-- Transaction 1: COMMIT
START TRANSACTION;
UPDATE employees SET salary = 6000000 WHERE employee_id = 1;
COMMIT;

-- Transaction 2: ROLLBACK
START TRANSACTION;
UPDATE employees SET salary = 7000000 WHERE employee_id = 1;
INSERT INTO employees VALUES (7, 'John Lee', 'Manager', 5500000, '2023-03-10');
ROLLBACK;

Result:
- Employee 1: 6000000 (Transaction 2 UPDATE cancelled)
- Employee 7: Not exists (INSERT cancelled)
```

---

### Question 20: Complex Transaction

**Model Answer (모범 답안):**

```sql
-- 1. Organization restructure transaction
START TRANSACTION;
  -- Create new department
  -- INSERT INTO departments ...;
  
  -- Change employee assignment
  UPDATE employees SET position = 'Deputy' WHERE employee_id = 2;
  SAVEPOINT sp1;
  
  -- Salary adjustment (Manager +10%)
  UPDATE employees SET salary = ROUND(salary * 1.1) WHERE position = 'Manager';
  SAVEPOINT sp2;
  
  -- Add new employee
  INSERT INTO employees VALUES (8, 'Lisa Park', 'Deputy', 4500000, '2023-04-15');
  
COMMIT;

-- 2. SAVEPOINT usage example
START TRANSACTION;
  DELETE FROM employees WHERE employee_id = 1;
  SAVEPOINT sp1;
  
  DELETE FROM employees WHERE employee_id = 2;
  -- Integrity violation error
  ROLLBACK TO sp1;  -- Revert to sp1
  
  -- Employee 1 deleted, Employee 2 maintained
  
COMMIT;

-- 3. Data integrity verification
SELECT COUNT(*) FROM employees;  -- Compare row count
SELECT * FROM employees WHERE employee_id = 1;  -- Check specific data
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
