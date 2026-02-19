# Chapter 9. DML (Data Manipulation Language) and Transaction

---

## 📖 Class Overview

In this chapter, you will learn about DML commands (INSERT, UPDATE, DELETE) that manipulate data in a database and transactions that ensure data integrity. You will study how to accurately and safely insert, modify, and delete data, and how to maintain data consistency by processing multiple operations as a single logical unit. The goal is to develop the ability to prevent and recover from data integrity errors in practice.

이 장에서는 데이터베이스의 데이터를 조작하는 DML 명령어(INSERT, UPDATE, DELETE)와 데이터 무결성을 보장하는 트랜잭션(Transaction)을 학습합니다. 데이터를 정확하고 안전하게 입력, 수정, 삭제하는 방법과 여러 작업을 하나의 논리적 단위로 처리하여 데이터 일관성을 유지하는 방법을 다룹니다. 실무에서 데이터 무결성 오류를 방지하고 복구할 수 있는 능력을 개발하는 것이 목표입니다.

---

## 📚 Part 1: Theoretical Learning

### 9.1 INSERT Statement (Data Insertion)

INSERT adds new data to a table. (INSERT는 테이블에 새로운 데이터를 추가합니다.)

**Basic Syntax (기본 문법):**

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

**Example (예시):**

```sql
-- Insert new employee info into specified columns only (새로운 직원 정보를 지정된 열에만 삽입)
INSERT INTO employees (name, dept_id, salary)
VALUES ('Alex Johnson', 1, 5000000);
```

**Why Specify Column Names? (왜 열 이름을 지정해야 할까?)**

It is better to explicitly specify column names for several reasons. (명시적으로 열 이름을 지정하는 것이 좋은 이유:)
- Specifying column names makes the code clearer because you can see at a glance which value goes to which column. (각 값이 어느 열로 가는지 한눈에 알 수 있어 코드가 더 명확함)
- If a new column is added to the table, the existing query will not break. (테이블에 새로운 열이 추가되어도 기존 쿼리는 깨지지 않음)
- Maintenance becomes easier because the intent is clear when someone reads the code. (누군가 코드를 읽을 때 의도가 명확함)
- You can also take advantage of default values to skip columns that have NOT NULL constraints but have default values. (NOT NULL 제약이 있지만 기본값이 있는 열을 건너뛸 수 있음)

**❌ Dangerous Method (위험한 방법):**

```sql
-- Insert values in order for all columns (NOT RECOMMENDED!) (모든 열에 값을 순서대로 입력 비추천!)
INSERT INTO employees
VALUES (NULL, 'Sarah Williams', 1, 4000000);  -- Dangerous! (위험함!)
```

**Why Is This Dangerous? (왜 위험한가?)**

- If the table structure changes, this query will break. (테이블 구조가 변경되면 이 쿼리가 깨짐)
- You must know the exact order of columns. (열의 순서를 정확히 알아야 함)
- It is unclear to the reader what is being inserted. (코드를 읽는 사람이 무엇을 삽입하는지 불명확함)

**Bulk INSERT (Performance Optimization) (대량 INSERT 성능 최적화):**

```sql
-- Insert multiple rows at once (much faster than individual INSERT!) (한 번에 여러 행을 삽입 개별 INSERT보다 훨씬 빠름!)
INSERT INTO employees (name, dept_id, salary) VALUES
('David Brown', 2, 4500000),
('Emily Davis', 2, 3500000),
('Jennifer Miller', 1, 4100000);
```

**Advantages of Bulk INSERT (대량 INSERT의 장점):**

- Much faster than individual INSERT statements (개별 INSERT 문보다 훨씬 빠름)
- Reduced network traffic (네트워크 트래픽 감소)
- Processed as a single transaction for safety (단일 트랜잭션으로 처리되어 안전함)

**INSERT Using Subquery (Data Copying) (서브쿼리를 이용한 INSERT 데이터 복사):**

```sql
-- Copy data from one table to another (한 테이블의 데이터를 다른 테이블로 복사)
INSERT INTO employee_backup
SELECT * FROM employees 
WHERE dept_id = 1;
```

**Use Cases (사용 사례):**

- Back up data before major changes (주요 변경 전 데이터 백업)
- Copy old data to archive table (오래된 데이터를 아카이브 테이블로 복사)
- Data migration (데이터 마이그레이션)
- Generate test data from real data (실제 데이터로부터 테스트 데이터 생성)

---

### 9.2 UPDATE Statement (Data Modification)

UPDATE modifies existing data. (UPDATE는 기존 데이터를 수정합니다.)

**Basic Syntax (기본 문법):**

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**⚠️ Critical Warning! (치명적인 경고!)**

Always include a WHERE condition. Without it, all rows will be modified!
WHERE 조건을 반드시 포함하세요. 없으면 모든 행이 수정됩니다!

```sql
-- 🚨 Extremely dangerous! Never do this! (🚨 매우 위험! 절대 하지 마세요!)
UPDATE employees SET salary = 5000000;  -- No WHERE!
-- Result: All employees' salaries changed to 5000000! 😱 (결과: 모든 직원의 급여가 5000000으로 변경됨!)

-- ✅ Correct way (✅ 올바른 방법)
UPDATE employees SET salary = 5000000 
WHERE employee_id = 1;  -- Only modify specific employee (특정 직원만 수정)
```

**Safe UPDATE Procedure (안전한 UPDATE 절차):**

```sql
-- Step 1: First verify what will be modified with SELECT (단계 1: 먼저 SELECT로 무엇이 수정될지 확인)
SELECT * FROM employees WHERE dept_id = 1;

-- Step 2: Execute UPDATE if result is correct (단계 2: 결과가 맞으면 UPDATE 실행)
UPDATE employees 
SET salary = salary * 1.1  -- 10% increase (10% 인상)
WHERE dept_id = 1;

-- Step 3: Use transaction for safer approach (단계 3: 트랜잭션을 사용하면 더 안전함)
START TRANSACTION;
UPDATE employees SET salary = salary * 1.1 WHERE dept_id = 1;
COMMIT;  -- Or ROLLBACK (또는 ROLLBACK)
```

**UPDATE Using Expression (수식을 사용한 UPDATE):**

```sql
-- Calculate and update based on current value (현재 값을 기반으로 계산하여 업데이트)
UPDATE employees
SET salary = salary * 1.1  -- Increase current salary by 10% (현재 급여의 10% 인상)
WHERE dept_id = 1;
```

**Conditional UPDATE Using CASE (조건부 UPDATE CASE 사용):**

```sql
-- Apply different raise rates by department (부서별로 다른 인상률 적용)
UPDATE employees
SET salary = CASE
    WHEN dept_id = 1 THEN salary * 1.15  -- Sales: 15% raise (영업부: 15% 인상)
    WHEN dept_id = 2 THEN salary * 1.12  -- Tech: 12% raise (기술부: 12% 인상)
    WHEN dept_id = 3 THEN salary * 1.10  -- HR: 10% raise (인사부: 10% 인상)
    ELSE salary  -- Other departments: no raise (다른 부서: 인상 없음)
END;
```

---

### 9.3 DELETE Statement (Data Deletion)

DELETE removes data from a table. (DELETE는 테이블의 데이터를 삭제합니다.)

**Basic Syntax (기본 문법):**

```sql
DELETE FROM table_name
WHERE condition;
```

**⚠️ Very Important Warning! (매우 중요한 경고!)**

Without a WHERE condition, all rows will be permanently deleted!
WHERE 조건이 없으면 모든 행이 영구적으로 삭제됩니다!

```sql
-- 🚨 Extremely dangerous! Never do this! (🚨 극도로 위험! 절대 하지 마세요!)
DELETE FROM employees;  -- No WHERE!
-- Result: All employee data is gone! 💥 (결과: 모든 직원 데이터가 사라짐!)

-- ✅ Correct way (✅ 올바른 방법)
DELETE FROM employees WHERE employee_id = 7;  -- Delete specific employee (특정 직원만 삭제)
```

**Safe DELETE Procedure (안전한 DELETE 절차):**

```sql
-- Step 1: First verify what will be deleted (단계 1: 삭제될 데이터를 먼저 확인)
SELECT * FROM employees WHERE salary < 3500000;

-- Step 2: Execute DELETE if result is correct (단계 2: 결과가 맞으면 DELETE 실행)
DELETE FROM employees WHERE salary < 3500000;

-- Step 3: Safest method - Use transaction (단계 3: 가장 안전한 방법 - 트랜잭션 사용)
START TRANSACTION;
DELETE FROM employees WHERE salary < 3500000;
-- Verify result then
COMMIT;  -- Confirm deletion or (삭제 확정 또는)
ROLLBACK;  -- Cancel and restore (취소하고 원상복구)
```

**DELETE vs TRUNCATE Comparison (DELETE vs TRUNCATE 비교):**

| Feature | DELETE | TRUNCATE |
|---------|--------|----------|
| WHERE condition | ✅ Supported | ❌ Not supported |
| Rollback possible | ✅ Yes (in transaction) | ❌ No |
| Speed | Slow | Very fast |
| When to use | Selective deletion | Delete all rows |
| Table structure | Maintained | Maintained |

---

### 9.4 Transaction Concept

A transaction groups multiple SQL operations into a single logical unit. (트랜잭션은 여러 SQL 작업을 하나의 논리적 단위로 묶습니다.)

**Why Transactions Are Needed? (Bank Transfer Example) (왜 트랜잭션이 필요한가? 은행 송금 사례):**

Let's think about a bank transfer in a real banking system. (실제 은행 시스템에서 계좌 송금을 생각해봅시다.)

**❌ Problem Situation (Without Transaction) (문제 상황 트랜잭션 없이):**

```sql
-- Withdraw 100,000 from account 1 (계좌 1에서 100,000원 출금)
UPDATE accounts SET balance = balance - 100000 
WHERE account_id = 1001;  
-- ✅ Success! (성공!)

-- System crashes here! 😱 (여기서 갑자기 시스템이 다운됨!)
-- Server down, database connection lost, power cut, etc.

-- Deposit 100,000 to account 2 (not executed) (계좌 2에 100,000원 입금 실행 안 됨)
UPDATE accounts SET balance = balance + 100000 
WHERE account_id = 1002;  
-- ❌ Not executed (실행되지 않음)
```

**What Happens to the Results? (결과가 어떻게 되는가?)**

- Account 1: 100,000 deducted ✅ (completed)
- Account 2: unchanged (deposit not made) ❌
- Result: 100,000 disappears! (very big problem!)

- 계좌 1: 100,000원 차감됨 ✅ (완료됨)
- 계좌 2: 그대로 (입금 안 됨) ❌
- 결과: 100,000원이 사라짐! (매우 큰 문제!)

**Bank is ruined** 😞

**✅ Solution (Using Transaction) (해결책 트랜잭션 사용):**

```sql
-- Start transaction (트랜잭션 시작)
START TRANSACTION;

  -- Withdraw from account 1 (계좌 1에서 출금)
  UPDATE accounts SET balance = balance - 100000 
  WHERE account_id = 1001;
  
  -- Deposit to account 2 (계좌 2에 입금)
  UPDATE accounts SET balance = balance + 100000 
  WHERE account_id = 1002;

-- If both succeed, confirm (둘 다 성공했으면 확정)
COMMIT;

-- Or if problem occurs, cancel all (또는 문제가 있으면 모두 취소)
ROLLBACK;
```

**Result (결과):**

- ✅ Both updates succeed: COMMIT → Both changes are saved (둘 다 성공: COMMIT → 두 변경사항이 모두 저장됨)
- ❌ Either fails: ROLLBACK → Both changes are cancelled (어느 하나라도 실패: ROLLBACK → 두 변경사항이 모두 취소됨)
- 🚫 Intermediate state never occurs! (중간 상태는 절대 발생하지 않음!)

**Bank is safe** 😊

**Transaction Characteristics (트랜잭션의 특징):**

- **All or Nothing**: Everything succeeds or everything fails (모두 성공하거나 모두 실패함)
- **Prevent Incomplete State**: Incomplete state is never saved (불완전한 상태가 절대 저장되지 않음)
- **Ensure Data Consistency**: Data is always in valid state (데이터 일관성 보장: 언제나 데이터는 유효한 상태를 유지)
- **Safety**: If problems occur, can be returned to previous state (문제가 발생하면 이전 상태로 돌려놓을 수 있음)

---

### 9.5 ACID Properties

Four essential characteristics that guarantee transaction safety. (트랜잭션의 안전성을 보장하는 네 가지 핵심 특성입니다.)

**A - Atomicity (원자성):**

**Definition**: "All or Nothing" - either all operations of a transaction are performed completely or all are cancelled completely.   
정의: "All or Nothing" - 트랜잭션의 모든 작업이 완전히 수행되거나 완전히 취소됨

**Problem Situation (문제 상황):**

```sql
START TRANSACTION;
  UPDATE accounts SET balance = balance - 100000 WHERE id = 1001;  -- ✅ Success
  UPDATE accounts SET balance = balance + 100000 WHERE id = 1002;  -- ❌ Fail!

COMMIT;  -- First is saved, second is not → Data mismatch! (첫 번째만 저장되고 두 번째는 안 됨 → 데이터 불일치!)
```

**Solution (해결책):**

Database handles automatically: (데이터베이스가 자동으로 처리:)

- ❌ If any fails → ROLLBACK (cancel all) (어느 하나라도 실패 → ROLLBACK 모두 취소)
- ✅ If all succeed → COMMIT (save all) (모두 성공 → COMMIT 모두 저장)

**Why Is This Important? (왜 중요한가?)**

- Without atomicity, money would leave one account but not arrive at another. (원자성이 없으면 돈이 한 계좌에서는 빠지지만 다른 계좌에 들어오지 않음)
- Inventory would decrease by 1 but no sale record. (재고가 1개 감소하지만 판매 기록이 남지 않음)
- This causes confusing incomplete data state. (혼란스러운 불완전한 데이터 상태 발생)

---

### C - Consistency (일관성)

**Definition**: The database maintains a valid state before and after a transaction. In other words, the physical laws (rules) of the database must not be broken before and after the transaction.   
정의: 트랜잭션 전후로 데이터베이스가 유효한 상태를 유지함. 데이터베이스의 물리 법칙(규칙)이 트랜잭션 전후로 깨지지 않아야 한다는 뜻

**Example (예시):**

```
Bank rule: Sum of all account balances = Bank reserves
```

```sql
START TRANSACTION;
  UPDATE accounts SET balance = balance - 100000 WHERE id = 1001;  -- -100,000
  UPDATE accounts SET balance = balance + 100000 WHERE id = 1002;  -- +100,000
COMMIT;

-- Result: Total balance unchanged! ✅ Consistency maintained (총 잔액은 변하지 않음! ✅ 일관성 유지됨)
```

**Why Is This Important? (왜 중요한가?)**

- Employees cannot be assigned to a department that doesn't exist. (부서가 없는데 직원이 그 부서로 배정될 수 없음)
- Negative amounts or impossible values cannot be stored. (음수 금액이나 불가능한 값이 저장될 수 없음)
- Data always remains in valid state. (데이터가 항상 타당한 상태를 유지)

---

### I - Isolation (격리성)

**Definition**: When multiple transactions are executed simultaneously, each transaction is isolated so they do not interfere with each other.   
정의: 동시에 여러 트랜잭션이 수행될 때, 각 트랜잭션이 서로 방해하지 못하도록 격리하는 성질

**Why Is This Important? (왜 중요한가?)**

If isolation is not guaranteed, the following accidents can occur. (고립성이 보장되지 않는다면 다음과 같은 사고가 발생할 수 있다)
- Double withdrawal: balance is 100,000 won but two places withdraw 100,000 won simultaneously, resulting in negative balance. (이중 출금: 잔액이 10만원인데 동시에 두 곳에서 10만원씩 출금되어 잔액이 마이너스가 되는 상황)
- Data evaporation: when two people click edit simultaneously on a post, only the later person's content remains and the first person's work disappears. (데이터 증발: 두 명이 동시에 게시글 수정 버튼을 눌렀을 때, 나중에 저장한 사람의 내용만 남고 앞사람의 작업은 사라지는 상황)

**Solution (격리성으로 보호) (Protection with Isolation):**

```
Session A                          Session B
─────────────────────────────────────────────
START TRANSACTION;
  SELECT balance;  -- 1,000,000 (locking starts) (잠금 시작)
  [This row cannot be seen by other sessions during A's transaction] (A의 트랜잭션 동안 이 행을 다른 세션이 볼 수 없음)

                                START TRANSACTION;
                                  SELECT balance;  -- Waiting... 🔄
                                  -- Waiting for A's transaction to end (A의 트랜잭션이 끝날 때까지 기다림)
  UPDATE accounts 
  SET balance = 900,000;
  COMMIT;  -- Locking released (잠금 해제)

                                  -- Now can finally read data (이제 비로소 데이터를 읽을 수 있음)
                                  SELECT balance;  -- 900,000
                                  UPDATE accounts 
                                  SET balance = 800,000;
                                  COMMIT;

Result: Safe! ✅ (안전함! ✅)
```

---

### D - Durability (지속성)

**Definition**: Results of successfully completed (Committed) transactions must be permanently preserved even if system errors occur.   
정의: 성공적으로 완료(Commit)된 트랜잭션의 결과는 시스템에 오류가 발생하더라도 영구적으로 보존되어야 한다는 성질

**Example (예시):**

```sql
START TRANSACTION;
  INSERT INTO employees VALUES (10, 'New Employee', 1, 3500000);
COMMIT;  -- Data is now permanently saved ✅ (데이터가 이제 영구적으로 저장됨 ✅)

-- At this moment:
-- - Server reboots
-- - Power outage occurs
-- - Disk breaks
-- → Data is still safe! (이 순간 서버가 재부팅됨, 정전이 발생함, 디스크가 깨짐 → 데이터는 여전히 안전함!)
```

**Saving Guarantee Method (저장 보장 방식):**

```
Memory (volatile)
    ↓
    ↓ COMMIT time
    ↓
Disk (non-volatile) ← Permanently saved! (영구 저장됨!)
```

**Why Is This Important? (왜 중요한가?)**

- Committed data is never lost. (COMMIT한 데이터는 절대 손실되지 않음)
- Protected from system failures. (시스템 장애로부터 보호됨)
- Business continuity guaranteed. (업무 연속성 보장)
- Simply put, if you complete a transfer at the bank and the bank server suddenly loses power, when it restarts your money should not disappear and the transfer should remain completed. (쉽게 말해, 은행에서 송금을 완료했는데 갑자기 은행 서버의 전원이 꺼지더라도, 다시 켰을 때 내 돈이 사라지지 않고 제대로 송금된 상태로 남아있어야 한다는 뜻)

---

### 9.6 COMMIT and ROLLBACK

**COMMIT (COMMIT):**

**Role**: Permanently save all changes of a transaction (역할: 트랜잭션의 모든 변경사항을 영구적으로 저장)

```sql
START TRANSACTION;
  UPDATE employees SET salary = 5000000 WHERE employee_id = 1;
  -- At this point, changes are visible only in my session (이 시점에서는 나 자신의 세션에서만 변경사항을 볼 수 있음)
  
COMMIT;  -- Now everyone can see the changes (이제 모든 사람이 변경사항을 볼 수 있음)
```

**ROLLBACK (ROLLBACK):**

**Role**: Cancel all changes of a transaction and restore to previous state (역할: 트랜잭션의 모든 변경사항을 취소하고 이전 상태로 복원)

```sql
START TRANSACTION;
  INSERT INTO employees VALUES (10, 'New Employee', 1, 3500000);
  -- New employee is added (temporary) (새 직원이 추가됨 임시)
  
  -- Problem found! Wrong information! (문제 발견! 잘못된 정보다!)
  
ROLLBACK;  -- Insertion is cancelled, employee is not created (삽입이 취소됨, 직원이 생성되지 않음)
```

**Practical Use Cases (실제 사용 사례):**

```sql
START TRANSACTION;
  UPDATE employees SET salary = 5500000 WHERE employee_id = 1;
  UPDATE employees SET dept_id = 2 WHERE employee_id = 1;
COMMIT;  -- Both changes are saved ✅ (두 변경사항이 모두 저장됨 ✅)
```

---

### 9.7 SAVEPOINT (Partial Rollback)

**Purpose**: Can rollback only to a specific point within a transaction (용도: 트랜잭션 내에서 특정 지점까지만 롤백할 수 있음)

**Problem Situation (Without SAVEPOINT) (문제 상황 SAVEPOINT 없이):**

```sql
START TRANSACTION;
  INSERT INTO employees VALUES (10, 'Employee1', 1, 3000000);  -- ✅ Success
  INSERT INTO employees VALUES (11, 'Employee2', 1, 3500000);  -- ✅ Success
  INSERT INTO employees VALUES (12, 'Employee3', 99, 3700000); -- ❌ Error!

ROLLBACK;  -- All cancelled (first two also!) (모두 취소됨 처음 두 개도!)
-- But I wanted to keep the first two... (하지만 처음 두 개는 지키고 싶었는데...)
```

**Solution (Using SAVEPOINT) (해결책 SAVEPOINT 사용):**

```sql
START TRANSACTION;
  INSERT INTO employees VALUES (10, 'Employee1', 1, 3000000);  -- ✅ Success
  INSERT INTO employees VALUES (11, 'Employee2', 1, 3500000);  -- ✅ Success
  
  SAVEPOINT sp1;  -- Mark this point (이 지점을 표시해둠)
  
  INSERT INTO employees VALUES (12, 'Employee3', 99, 3700000); -- ❌ Error!
  
  -- Rollback only to sp1 (first two are kept) (sp1까지만 롤백 처음 두 개는 유지)
  ROLLBACK TO sp1;
  
  -- Now try again with correct data (이제 올바른 데이터로 다시 시도)
  INSERT INTO employees VALUES (12, 'Employee3', 1, 3700000);  -- ✅ Success!
  
COMMIT;  -- All three are inserted! ✅ (세 명 모두 삽입됨! ✅)
```

**Using Multiple SAVEPOINTs (여러 SAVEPOINT 사용):**

```sql
START TRANSACTION;
  DELETE FROM logs WHERE created_date < '2024-01-01';  -- Delete logs (로그 삭제)
  SAVEPOINT sp1;
  
  UPDATE employees SET salary = salary * 1.1;  -- Raise salary (급여 인상)
  SAVEPOINT sp2;
  
  DELETE FROM old_data WHERE archived = true;  -- Delete old data (오래된 데이터 삭제)
  -- Problem occurs in this operation! (이 작업에서 문제 발생!)
  
  -- Rollback to sp2: salary raise is kept, data deletion is cancelled (sp2로 롤백: 급여 인상은 유지, 데이터 삭제는 취소)
  ROLLBACK TO sp2;
  
COMMIT;  -- Only log deletion and salary raise are saved (로그 삭제와 급여 인상만 저장됨)
```

---

## 📚 Part 2: Sample Data

### Essential Table Structure (필수 테이블 구성)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch9_dml CHARACTER SET utf8mb4;
USE ch9_dml;

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

-- Create accounts table (transaction examples) (accounts 테이블 트랜잭션 예시용)
CREATE TABLE accounts (
    account_id INT PRIMARY KEY,
    account_name VARCHAR(50),
    balance DECIMAL(10, 2)
);
```

---

## 💻 Part 3: Hands-on Practice (20 Problems)

### What You'll Learn in This Section

In this section, you will practice safely using INSERT, UPDATE, DELETE, and ensuring data integrity through transactions. (이 섹션에서는 INSERT, UPDATE, DELETE를 안전하게 사용하고, 트랜잭션을 통해 데이터 무결성을 보장하는 다양한 기법을 실습합니다.)

```sql
-- =====================================================
-- Section 1: INSERT (Problems 1-3) (섹션 1: INSERT 1-3번)
-- =====================================================

-- 1. Basic INSERT (safe method - specify column names) (기본 INSERT 안전한 방법 - 열 이름 명시)
INSERT INTO employees (name, dept_id, salary)
VALUES ('Jennifer Miller', 1, 4100000);

-- 2. Bulk INSERT (efficient - faster than individual) (대량 INSERT 효율적 - 개별보다 빠름)
INSERT INTO employees (name, dept_id, salary) VALUES
('Robert Taylor', 1, 3900000),
('Jessica Anderson', 2, 4100000),
('Christopher Thomas', 1, 3700000);

-- 3. INSERT using subquery (data copy) (서브쿼리를 이용한 INSERT 데이터 복사)
CREATE TABLE IF NOT EXISTS employee_archive AS 
SELECT * FROM employees LIMIT 0;

INSERT INTO employee_archive
SELECT * FROM employees
WHERE salary >= (SELECT AVG(salary) FROM employees WHERE dept_id = 1);

-- =====================================================
-- Section 2: UPDATE (Problems 4-8) (섹션 2: UPDATE 4-8번)
-- =====================================================

-- 4. Basic UPDATE (WHERE condition is mandatory!) (기본 UPDATE WHERE 조건 필수!)
UPDATE employees
SET salary = 5200000
WHERE employee_id = 1;

-- 5. UPDATE multiple columns simultaneously (여러 열을 동시에 UPDATE)
UPDATE employees
SET salary = 5500000, dept_id = 2
WHERE employee_id = 2;

-- 6. UPDATE using expression (based on current value) (수식을 사용한 UPDATE 현재값 기반 계산)
UPDATE employees
SET salary = salary * 1.1
WHERE dept_id = 1;

-- 7. Conditional UPDATE using CASE (different raise by department) (CASE를 사용한 조건부 UPDATE 부서별 다른 인상률)
UPDATE employees
SET salary = CASE 
    WHEN dept_id = 1 THEN salary * 1.15
    WHEN dept_id = 2 THEN salary * 1.12
    ELSE salary * 1.10
END;

-- 8. Safe UPDATE procedure (verify with SELECT first) (안전한 UPDATE 절차 먼저 SELECT로 확인)
-- Step 1: Verify (단계 1: 확인)
SELECT * FROM employees WHERE dept_id = 2;
-- Step 2: Execute UPDATE (단계 2: UPDATE 실행)
UPDATE employees
SET salary = salary * 1.05
WHERE dept_id = 2;

-- =====================================================
-- Section 3: DELETE (Problems 9-10) (섹션 3: DELETE 9-10번)
-- =====================================================

-- 9. Basic DELETE (WHERE condition is mandatory!) (기본 DELETE WHERE 조건 필수!)
DELETE FROM employees
WHERE employee_id = 7;

-- 10. Safe DELETE procedure (verify with SELECT first) (안전한 DELETE 절차 먼저 SELECT로 확인)
-- Step 1: Verify data to be deleted (단계 1: 삭제될 데이터 확인)
SELECT * FROM employees WHERE salary < 3600000;
-- Step 2: Execute DELETE (단계 2: DELETE 실행)
DELETE FROM employees WHERE salary < 3600000;

-- =====================================================
-- Section 4: Transaction Basics (Problems 11-13) (섹션 4: 트랜잭션 기본 11-13번)
-- =====================================================

-- 11. Simple transaction - COMMIT (save all) (간단한 트랜잭션 - COMMIT 모두 저장)
START TRANSACTION;
  INSERT INTO employees (name, dept_id, salary) 
  VALUES ('Nicole Martinez', 1, 4300000);
  UPDATE employees 
  SET salary = salary * 1.05 
  WHERE dept_id = 1;
COMMIT;

-- 12. Transaction - ROLLBACK (cancel all) (트랜잭션 - ROLLBACK 모두 취소)
START TRANSACTION;
  INSERT INTO employees (name, dept_id, salary) 
  VALUES ('Kevin Jackson', 2, 4400000);
ROLLBACK;

-- 13. Bank transfer simulation (importance of transaction) (은행 송금 시뮬레이션 트랜잭션의 중요성)
INSERT INTO accounts VALUES
(1001, 'Account of Alex Johnson', 1000000),
(1002, 'Account of Sarah Williams', 500000);

START TRANSACTION;
  UPDATE accounts SET balance = balance - 100000 WHERE account_id = 1001;
  UPDATE accounts SET balance = balance + 100000 WHERE account_id = 1002;
COMMIT;

-- =====================================================
-- Section 5: Advanced Transaction and SAVEPOINT (Problems 14-16) (섹션 5: 고급 트랜잭션 및 SAVEPOINT 14-16번)
-- =====================================================

-- 14. SAVEPOINT - partial rollback (부분 롤백)
START TRANSACTION;
  INSERT INTO employees (name, dept_id, salary) 
  VALUES ('Lisa White', 1, 4100000);
  
  SAVEPOINT sp1;
  
  INSERT INTO employees (name, dept_id, salary) 
  VALUES ('Brian Harris', 2, 4300000);
  
  ROLLBACK TO sp1;
  
  INSERT INTO employees (name, dept_id, salary) 
  VALUES ('Brian Harris', 1, 4300000);
  
COMMIT;

-- 15. Data validation before INSERT (데이터 검증 후 INSERT)
INSERT INTO employees (name, dept_id, salary)
SELECT 'New Employee', 1, 4100000
WHERE NOT EXISTS (SELECT 1 FROM employees WHERE name = 'New Employee');

-- 16. INSERT IGNORE (continue on error with warning) (INSERT IGNORE 에러가 발생해도 작업을 중단하지 말고 경고만 발생하고 넘어가라)
INSERT IGNORE INTO employees (employee_id, name, dept_id, salary)
VALUES (1, 'Alex Johnson', 1, 5000000);

-- =====================================================
-- Section 6: Real-world Practice (Problems 17-20) (섹션 6: 실무 활용 17-20번)
-- =====================================================

-- 17. Data migration (protected by transaction) (데이터 마이그레이션 트랜잭션으로 보호)
START TRANSACTION;
  INSERT INTO employee_archive 
  SELECT * FROM employees WHERE employee_id >= 10;
  
  DELETE FROM employees WHERE employee_id >= 10;
  
COMMIT;

-- 18. Row locking (SELECT FOR UPDATE - concurrency control) (행 잠금 SELECT FOR UPDATE - 동시성 제어)
-- Write lock - declare that I will modify this data, don't touch it until I finish (쓰기 잠금 내가 이 데이터를 수정할 거니까, 내가 끝낼 때까지 아무도 손대지 마라고 선언)
START TRANSACTION;
  SELECT * FROM employees WHERE employee_id = 1 FOR UPDATE;
  UPDATE employees SET salary = 5500000 WHERE employee_id = 1;
COMMIT;

-- 19. Validation before change (best practice) (변경 전 검증 베스트 프랙티스)
SELECT * FROM employees WHERE dept_id = 1 AND salary < 4000000;

START TRANSACTION;
  UPDATE employees 
  SET salary = salary * 1.15
  WHERE dept_id = 1 AND salary < 4000000;
COMMIT;

-- 20. TRUNCATE vs DELETE comparison (DELETE supports transaction rollback) (TRUNCATE vs DELETE 비교 DELETE는 트랜잭션 보호 가능)
START TRANSACTION;
  DELETE FROM employees WHERE dept_id = 4;
COMMIT;
-- TRUNCATE TABLE employees;  -- Delete all rows (rollback not possible!) (모든 행 삭제 롤백 불가!)
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain INSERT, UPDATE, DELETE statements in detail. Explain when each should be used and provide real-world examples.

INSERT, UPDATE, DELETE 문을 상세히 설명하세요. 각각이 언제 사용되어야 하는지 설명하고, 실제 사례를 들어주세요.

**Assignment 2**: Explain transaction concept and ACID properties in detail. Explain why transactions are important in databases using a bank transfer example.

트랜잭션의 개념과 ACID 특성을 상세히 설명하세요. 데이터베이스에서 트랜잭션이 중요한 이유를 은행 송금 예시로 설명하세요.

**Assignment 3**: Explain COMMIT, ROLLBACK, SAVEPOINT in detail. Explain when each is used and how they work with examples.

COMMIT, ROLLBACK, SAVEPOINT를 상세히 설명하세요. 각각이 언제 사용되며, 어떻게 동작하는지 예시와 함께 설명하세요.

**Assignment 4**: Discuss data consistency problems that can occur without transactions. Describe possible scenarios and explain how to solve them.

트랜잭션 없이 발생할 수 있는 데이터 일관성 문제를 논의하세요. 실제 발생 가능한 상황을 들어 설명하고, 어떻게 해결할 수 있는지 제시하세요.

**Assignment 5**: Compare safe DML practice and dangerous DML practice. Explain best practices for protecting data integrity.

안전한 DML 실습과 위험한 DML 실습을 비교하세요. 데이터 무결성을 보호하기 위한 베스트 프랙티스를 설명하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Practice various forms of INSERT: basic INSERT, bulk INSERT, INSERT using subquery.

INSERT 문의 여러 형태를 실습하세요: 기본 INSERT, 대량 INSERT, 서브쿼리를 이용한 INSERT.

**Assignment 2**: Practice safe use of UPDATE: verify WHERE condition, conditional UPDATE, UPDATE using CASE.

UPDATE 문의 안전한 사용법을 실습하세요: WHERE 조건 확인, 조건부 UPDATE, CASE를 사용한 UPDATE.

**Assignment 3**: Practice safe use of DELETE: verify first with SELECT, include WHERE condition, use transaction.

DELETE 문의 안전한 사용법을 실습하세요: SELECT로 먼저 확인, WHERE 조건 포함, 트랜잭션 사용.

**Assignment 4**: Write transaction examples: successful COMMIT, failing ROLLBACK, partial rollback using SAVEPOINT.

트랜잭션 예시를 작성하세요: 성공하는 COMMIT, 실패하는 ROLLBACK, SAVEPOINT를 사용한 부분 롤백.

**Assignment 5**: Execute all practices (9-1 ~ 9-20) from Part 3 and attach result screenshots. Additionally, create 5 or more business scenarios, implement with transactions, and explain the purpose and practical application of each scenario.

Part 3의 모든 실습(9-1 ~ 9-20)을 직접 실행하고 결과 스크린샷을 첨부하세요. 추가로 5개 이상의 비즈니스 시나리오를 만들어 트랜잭션으로 구현하고, 각 시나리오의 목적과 실무 활용 방법을 설명하세요.

**Submission Format**: SQL file(Ch9_DML_Transaction_[StudentID].sql) and result screenshots

제출 형식: SQL 파일(Ch9_DML_Transaction_[학번].sql) 및 결과 스크린샷

---

Thank you for your attention.

Cho Jeonghyun (peterchokr@gmail.com). Yeungnam University College
