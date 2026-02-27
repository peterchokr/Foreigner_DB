# Chapter 2. DDL Commands - Practice Problems

Dear students! After completing Chapter 2, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

2장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 2, you should understand the following:

- Understanding DDL commands (CREATE, ALTER, DROP) (DDL 명령어의 이해)
- Criteria for choosing data types (VARCHAR vs CHAR, INT vs DECIMAL) (데이터 타입 선택의 기준)
- Types and purposes of constraints (PRIMARY KEY, UNIQUE, NOT NULL, DEFAULT) (제약조건의 종류와 용도)
- Table structure design and modification (테이블 구조 설계 및 수정)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** Between VARCHAR(50) and CHAR(50), which is suitable for storing variable-length characters? (VARCHAR(50)과 CHAR(50) 중 가변길이 문자를 저장하는 데 적합한 것은?)

- ① VARCHAR(50) - Variable-length, storage efficient (가변길이, 저장공간 효율적)
- ② CHAR(50) - Fixed-length, always 50 bytes (고정길이, 항상 50바이트)
- ③ Both are variable-length (둘 다 가변길이임)
- ④ It depends on the situation (상황에 따라 다름)

---

**Question 2** When storing currency amounts, which is the correct choice between DECIMAL(10,2) and FLOAT? (금액을 저장할 때 DECIMAL(10,2)와 FLOAT 중 올바른 선택은?)

- ① FLOAT is accurate (부동소수점) (부동소수점이 정확함)
- ② DECIMAL(10,2) is accurate (고정소수점) (고정소수점이 정확함)
- ③ Both have the same precision (둘 다 같은 정밀도)
- ④ Floating-point is safer (부동소수점이 더 안전)

---

**Question 3** What is the biggest difference between PRIMARY KEY and UNIQUE? (PRIMARY KEY와 UNIQUE의 가장 큰 차이점은?)

- ① PRIMARY KEY does not allow NULL and only one per table (NULL을 허용하지 않고, 테이블당 1개만 가능)
- ② UNIQUE allows multiple NULLs and multiple per table (NULL을 여러 개 허용하고, 여러 개 가능)
- ③ Functionally identical (기능상 완전히 같음)
- ④ PRIMARY KEY is slower (PRIMARY KEY가 더 느림)

---

**Question 4** What is the purpose of the NOT NULL + UNIQUE combination? (NOT NULL + UNIQUE 조합의 목적은?)

- ① Value must exist and must not be duplicated (값이 반드시 있고 중복되지 않아야 함)
- ② Value can be absent but duplication is not allowed (값이 없을 수도 있지만 중복 불가)
- ③ Multiple NULLs allowed (NULL은 여러 개 허용)
- ④ Identical to PRIMARY KEY (PRIMARY KEY와 동일)

---

**Question 5** What is the role of the DEFAULT constraint? (DEFAULT 제약조건의 역할은?)

- ① Specify a default value to automatically save when not entered (기본값을 지정하여 입력하지 않을 때 자동으로 저장)
- ② Prevent data modification (데이터 수정을 방지)
- ③ Prevent deletion (삭제를 방지)
- ④ Restrict query permissions (조회 권한을 제한)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which of the following is correct CREATE TABLE syntax? (다음 중 올바른 CREATE TABLE 문법은?)

```sql
① CREATE TABLE student (
    student_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(30) NOT NULL,
    gpa FLOAT,
    enrollment_date DATE DEFAULT CURRENT_DATE
);

② CREATE TABLE student (
    student_id INT,
    name VARCHAR(30) NOT NULL,
    gpa FLOAT PRIMARY KEY
);

③ CREATE TABLE student (
    student_id INT PRIMARY KEY NULL,
    name VARCHAR(30),
    gpa FLOAT
);
```

- ① Correct (all constraints appropriate) (올바름 - 모든 제약조건 적절)
- ② Correct (gpa as PRIMARY KEY) (올바름 - gpa가 PRIMARY KEY)
- ③ Correct (NULL allowed for PRIMARY KEY) (올바름 - PRIMARY KEY에 NULL 가능)
- ④ Only ① is correct (①만 올바름)

---

**Question 7** To change the salary column in the employee table from INT to DECIMAL(12,2), which command should you use? (employee 테이블에서 salary 열을 INT에서 DECIMAL(12,2)로 변경하려면?)

- ① Only DROP TABLE and CREATE TABLE are possible (DROP TABLE과 CREATE TABLE 반복만 가능)
- ② ALTER TABLE employee MODIFY salary DECIMAL(12,2);
- ③ ALTER TABLE employee CHANGE salary salary DECIMAL(12,2);
- ④ Both ② and ③ are possible (②와 ③ 모두 가능)

---

**Question 8** Why is AUTO_INCREMENT used? (AUTO_INCREMENT를 사용하는 이유는?)

- ① Automatically generates IDs that increment by 1 (자동으로 1씩 증가하는 ID를 생성)
- ② Prevent duplicate IDs (중복된 ID 방지)
- ③ No need to manually enter ID when adding new rows (새 행 추가 시 ID를 직접 입력 안 해도 됨)
- ④ All are correct (모두 맞음)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Which of the following two table designs is better? (다음 두 테이블 설계 중 더 나은 것은?)

```
Design A:
student (student_id INT, name VARCHAR(100), 
         phone VARCHAR(15) NOT NULL,
         email VARCHAR(50) NOT NULL UNIQUE,
         major VARCHAR(50))

Design B:
student (student_id INT PRIMARY KEY AUTO_INCREMENT, 
         name VARCHAR(30) NOT NULL,
         phone VARCHAR(15),
         email VARCHAR(50) UNIQUE,
         major VARCHAR(30))
```

- ① Design A is better (all fields required) (설계 A가 더 좋음 - 모든 필드가 필수)
- ② Design B is better (explicit PRIMARY KEY, flexibility) (설계 B가 더 좋음 - PRIMARY KEY 명시적 정의, 유연성)
- ③ Design A is better (all fields NOT NULL) (설계 A가 더 좋음 - 모든 필드가 NOT NULL)
- ④ Both are the same (둘 다 같음)

---

**Question 10** What is the most appropriate basis for determining VARCHAR length when designing table structures? (테이블 구조를 설계할 때 VARCHAR의 길이를 결정하는 기준으로 가장 적절한 것은?)

- ① Make it as long as possible unconditionally (무조건 최대한 길게)
- ② Consider the maximum length of data to be stored + extra space (저장될 데이터의 최대 길이를 고려 + 여유분)
  (e.g., max name 30 characters → VARCHAR(50)) (예: 이름 최대 30글자 → VARCHAR(50))
- ③ Any length is fine (no performance impact) (아무거나 - 성능 영향 없음)
- ④ Always use CHAR instead (항상 CHAR 사용이 나음)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain the difference in storage space when VARCHAR(30) and CHAR(30) each store 'Alex Kim' (8 characters). (VARCHAR(30)과 CHAR(30)이 각각 'Alex Kim'(8글자)를 저장할 때 차지하는 저장공간의 차이를 설명하시오.)

---

**Question 12** Explain in which situation each of the following 4 data types is used: INT, DECIMAL(10,2), VARCHAR(50), DATE (다음 4개의 데이터 타입 중 각각 어떤 상황에 사용하는지 설명하시오.)

---

**Question 13** Explain 3 or more differences between PRIMARY KEY and UNIQUE. (PRIMARY KEY와 UNIQUE의 차이를 3가지 이상 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** If you were to design a user registration system, create a user table that stores the following information: User ID (auto-increment), Username (required), Email (no duplication), Phone number, Sign-up date (auto current date), Salary (2 decimal places) (회원 가입 시스템을 설계한다면, 다음 정보를 저장하는 user 테이블을 만드시오: 사용자ID(자동증가), 사용자명(필수), 이메일(중복불가), 전화번호, 가입일자(자동 현재날짜), 월급(소수점 2자리))

Write the table creation SQL and explain why each constraint was chosen. (테이블 생성 SQL을 작성하고 각 제약조건을 선택한 이유를 설명하시오.)

---

## Advanced Level (1 Question)

**Question 15** The following changes are needed for an existing employee table: 1) Add a new department column (VARCHAR(30)), 2) Change salary from INT to DECIMAL(12,2), 3) Add a new hire_date column (DATE, default: current date) (기존 employee 테이블에서 다음과 같은 변경이 필요합니다: 1) department 열을 새로 추가(VARCHAR(30)), 2) salary를 INT에서 DECIMAL(12,2)로 변경, 3) hire_date 열을 새로 추가(DATE, 기본값: 현재날짜))

Write SQL using ALTER TABLE and analyze how these changes will affect existing data. (ALTER TABLE을 사용하는 SQL을 작성하고, 이러한 변경이 기존 데이터에 미칠 영향을 분석하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database and table (데이터베이스 생성 및 테이블 생성)
CREATE DATABASE ch2_practice CHARACTER SET utf8mb4;
USE ch2_practice;

-- Create professor table (교수 테이블 생성)
CREATE TABLE professor (
    prof_id INT PRIMARY KEY AUTO_INCREMENT,
    prof_name VARCHAR(30) NOT NULL,
    department VARCHAR(30),
    position VARCHAR(20),
    salary DECIMAL(10,2)
);

-- Verify table structure (테이블 구조 확인)
DESC professor;
```

Submission: Screenshot showing DESC professor result (1 screenshot) (제출: DESC professor 결과가 보이는 스크린샷 1장)

---

**Question 17** Insert 5 professors' data into the professor table as follows and verify the results. (professor 테이블에 5명의 교수 데이터를 다음과 같이 입력하고 결과를 확인하시오.)

```sql
-- Insert professor data (교수 데이터 입력)
INSERT INTO professor VALUES
(1, 'Alex Kim', 'Computer Science', 'Professor', 7500000),
(2, 'Sarah Lee', 'Software Engineering', 'Associate Professor', 6800000),
(3, 'David Park', 'Information Security', 'Assistant Professor', 5900000),
(4, 'Emily Choi', 'Data Science', 'Professor', 7800000),
(5, 'Michael Kang', 'Computer Science', 'Associate Professor', 6500000);

-- Query all data (모든 데이터 조회)
SELECT * FROM professor;
```

Submission: Screenshot showing all 5 professors' information (1 screenshot) (제출: 입력된 5명의 교수 정보가 모두 보이는 스크린샷 1장)

---

## Intermediate Level (2 Questions)

**Question 18** Perform the following changes to the professor table and provide a screenshot. (professor 테이블에 다음 변경을 수행하고 스크린샷을 제시하시오.)

1. Add phone column (VARCHAR(15)) (phone 열 추가)
2. Modify salary to DECIMAL(12,2) (salary를 DECIMAL(12,2)로 수정)
3. Verify the modified table structure (변경된 테이블 구조 확인)

```sql
-- Add phone column (phone 열 추가)
ALTER TABLE professor ADD phone VARCHAR(15);

-- Modify salary data type (salary 데이터 타입 수정)
ALTER TABLE professor MODIFY salary DECIMAL(12,2);

-- Verify modified table structure (수정된 테이블 구조 확인)
DESC professor;
```

Submission: Screenshot showing the final table structure (DESC result) (1 screenshot) (제출: 최종 테이블 구조(DESC 결과)가 보이는 스크린샷 1장)

---

**Question 19** Design a bank_account table for the following situation. (다음 상황에서 bank_account 테이블을 설계하시오.)

```
Information:
- Account number (auto-increment, primary key) (계좌번호 - 자동증가, 기본키)
- Customer name (required) (고객명 - 필수)
- Account type (required: Savings, Time Deposit, Loan) (계좌타입 - 필수: 보통예금, 적금, 대출)
- Balance (2 decimal places, default 0) (잔액 - 소수점 2자리, 기본값 0)
- Opening date (default: current date) (개설일자 - 현재날짜 기본값)
- Last transaction date (NULL allowed) (최종거래일 - NULL 가능)

Requirements:
1. Explain the reasons for choosing appropriate data types (적절한 데이터 타입 선택 이유 설명)
2. Explain the reasons for choosing constraints (제약조건 선택 이유 설명)
3. Write CREATE TABLE SQL (CREATE TABLE SQL 작성)
4. Insert 3 sample account data and take screenshot (3개 계좌 샘플 데이터 입력 후 스크린샷)

Submission: SQL and execution result screenshot (SQL과 실행 결과 스크린샷)
```

---

## Advanced Level (1 Question)

**Question 20** Improve the existing simple product table as follows. (기존의 단순한 product 테이블을 다음과 같이 개선하시오.)

```
Current table:
product (product_id, product_name, price, stock)

Improvement requirements:
1. product_id is PRIMARY KEY + AUTO_INCREMENT (product_id는 PRIMARY KEY + AUTO_INCREMENT)
2. product_name is NOT NULL + UNIQUE (product_name은 NOT NULL + UNIQUE)
3. price is DECIMAL(10,2) (no negative numbers CHECK) (price는 DECIMAL(10,2) - 음수 불가 CHECK)
4. stock defaults to 0, no negative numbers CHECK (stock은 기본값 0, 음수 불가 CHECK)
5. Add category column (VARCHAR(30)) (category 열 추가)
6. Add created_date column (default: current date) (created_date 열 추가 - 현재날짜 기본값)
7. Add description column (text, NULL allowed) (description 열 추가 - 텍스트, NULL 가능)

Questions:
1. Write improved CREATE TABLE SQL (개선된 CREATE TABLE SQL 작성)
2. Explain why each constraint was chosen (각 제약조건을 선택한 이유)
3. Insert 5 sample product data (5개 샘플 상품 데이터 입력)
4. Verify final table structure and data (최종 테이블 구조와 데이터 확인)

Submission: Complete SQL code and execution result screenshot (전체 SQL 코드와 실행 결과 스크린샷)
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                                                                                                               |
| :------: | :----: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|    1    |   ①   | VARCHAR is variable-length and storage efficient (VARCHAR는 가변길이로 효율적 - VARCHAR(50)에 5글자면 6바이트 사용)                                                       |
|    2    |   ②   | DECIMAL is accurate fixed-point, essential for finance/accounting (DECIMAL은 정확한 고정소수점, 금융/회계에 필수)                                                         |
|    3    |   ①   | PRIMARY KEY: no NULL + only 1 per table, UNIQUE: allows multiple NULLs + multiple per table (PRIMARY KEY는 NULL 불가 + 1개만, UNIQUE는 NULL 여러 개 허용 + 여러 개)       |
|    4    |   ①   | NOT NULL + UNIQUE = value must exist and not duplicate (completely unique) (NOT NULL + UNIQUE = 값이 반드시 있고 중복 불가 - 완전 고유)                                   |
|    5    |   ①   | DEFAULT automatically saves specified value when not entered (DEFAULT는 입력하지 않을 때 자동으로 지정값 저장)                                                            |
|    6    |   ①   | Correct syntax (② has gpa as PK error, ③ has PRIMARY KEY NULL error) (올바른 문법 - ②는 gpa를 PK로 하는 오류, ③는 PK에 NULL 지정 오류)                                |
|    7    |   ④   | Both MODIFY and CHANGE work (MODIFY changes type only, CHANGE can change name too) (MODIFY와 CHANGE 모두 가능 - MODIFY는 타입만, CHANGE는 이름도 변경 가능)               |
|    8    |   ④   | AUTO_INCREMENT satisfies all reasons (AUTO_INCREMENT는 모든 이유를 만족)                                                                                                  |
|    9    |   ②   | Design B is better (explicit PRIMARY KEY, phone/email optional, appropriate VARCHAR sizes) (설계 B가 나음 - PRIMARY KEY 명시적, phone/email 선택 가능, VARCHAR 크기 적절) |
|    10    |   ②   | Correct design principle is to consider maximum length + extra space (최대 길이 고려 + 여유분이 올바른 설계 원칙)                                                         |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Storage Space Difference between VARCHAR(30) and CHAR(30)

**Model Answer (모범 답안):**

- **CHAR(30):** Always uses 30 bytes (fixed-length) (항상 30바이트 - 고정길이)
- **VARCHAR(30):** When storing 'Alex Kim' (5 characters), uses approximately 6-7 bytes (includes 1-2 bytes for length information) (5글자 저장 시 약 6~7바이트 - 길이정보 1~2바이트 포함)
- **Difference:** CHAR wastes 24 bytes, VARCHAR wastes nothing (CHAR는 24바이트 낭비, VARCHAR는 낭비 없음)
- **Conclusion:** For variable-length data, VARCHAR is more storage-efficient (가변길이 데이터는 VARCHAR가 저장공간 효율적)

---

### Question 12: Use Cases for Data Types

**Model Answer (모범 답안):**

```
1. INT
   - Store integer data (정수 데이터 저장)
   - Example: Student ID (202401), Age (25), Price (50000)

2. DECIMAL(10,2)
   - Financial amounts requiring decimal precision (소수점 정확도가 필요한 금액)
   - Example: Salary (7500000.00), Interest rate (4.25)

3. VARCHAR(50)
   - Variable-length character strings (가변길이 문자열)
   - Example: Name (Alex Kim), Email (kim@example.com), Address

4. DATE
   - Store dates (날짜 저장)
   - Example: Enrollment date (2024-01-15), Graduation date (2028-02-20)
```

---

### Question 13: Differences between PRIMARY KEY and UNIQUE

**Model Answer (모범 답안)** (3 or more):

1. **NULL handling:** PRIMARY KEY disallows NULL, UNIQUE allows multiple NULLs (NULL 처리: PRIMARY KEY는 NULL 불가, UNIQUE는 NULL 여러 개 허용)
2. **Quantity limit:** PRIMARY KEY only 1 per table, UNIQUE can be multiple (개수 제한: PRIMARY KEY는 테이블당 1개만, UNIQUE는 여러 개 가능)
3. **Performance:** PRIMARY KEY auto-creates index, UNIQUE usually creates index too (성능: PRIMARY KEY는 인덱스 자동 생성, UNIQUE도 보통 인덱스 생성)
4. **Purpose:** PRIMARY KEY identifies rows, UNIQUE prevents duplication (용도: PRIMARY KEY는 행 식별, UNIQUE는 중복 방지)
5. **Foreign keys:** Only PRIMARY KEY can be referenced as foreign key from other tables (외래키: PRIMARY KEY만 다른 테이블의 외래키로 참조 가능)

---

### Question 14: User Table Design

**Model Answer (모범 답안):**

```sql
CREATE TABLE user (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(30) NOT NULL,
    email VARCHAR(50) NOT NULL UNIQUE,
    phone VARCHAR(15),
    signup_date DATE DEFAULT CURRENT_DATE,
    monthly_salary DECIMAL(12,2)
);
```

**Reasons for constraint selection (제약조건 선택 이유):**

- **user_id:** PRIMARY KEY + AUTO_INCREMENT → Auto-increment, no duplication (자동 증가, 중복 없음)
- **username:** NOT NULL → Username is required (사용자명은 반드시 필요)
- **email:** UNIQUE → Prevent duplicate registration, essential for login (중복 가입 방지, 로그인에 필수)
- **phone:** NULL allowed → Optional information (선택 정보)
- **signup_date:** DEFAULT CURRENT_DATE → Automatically save current date (자동으로 현재 날짜 저장)
- **monthly_salary:** DECIMAL(12,2) → Decimal precision required (소수점 정확도 필요)

---

### Question 15: ALTER TABLE Modifications

**Model Answer (모범 답안):**

```sql
-- 1. Add department column (department 열 추가)
ALTER TABLE employee ADD department VARCHAR(30);

-- 2. Change salary from INT to DECIMAL(12,2) (salary를 INT에서 DECIMAL(12,2)로 변경)
ALTER TABLE employee MODIFY salary DECIMAL(12,2);

-- 3. Add hire_date column (hire_date 열 추가)
ALTER TABLE employee ADD hire_date DATE DEFAULT CURRENT_DATE;
```

**Impact on existing data (기존 데이터에 미치는 영향):**

1. **department column added:** Existing rows set to NULL for department (기존 행의 department는 NULL로 설정됨 - 기존 데이터 보존)
2. **salary changed:** INT to DECIMAL(12,2) conversion (소수점 자동 생성, 데이터 안전)
3. **hire_date added:** Existing rows set to NULL for hire_date (기존 행의 hire_date는 NULL로 설정됨 - 추후 UPDATE로 값 입력 필요)

---

## Practical Problem Model Answers (5 Questions)

### Question 16: Professor Table Creation

**Completion Criteria (완료 기준):**

✅ ch2_practice database created (ch2_practice 데이터베이스 생성됨)
✅ professor table created (5 columns) (professor 테이블 생성됨 - 5개 열)
✅ DESC professor result: prof_id, prof_name, department, position, salary all displayed (DESC professor 결과: 모두 표시)
✅ Constraints verified: prof_id PRIMARY KEY AUTO_INCREMENT, prof_name NOT NULL (제약조건 확인)

**Screenshot content includes (스크린샷 포함 내용):**

- DESC professor result (DESC professor 결과)
- All column data types and constraints displayed (모든 열의 데이터 타입과 제약조건 표시)

---

### Question 17: Professor Data Entry

**Completion Criteria (완료 기준):**

✅ 5 professors' data inserted (5명의 교수 데이터 입력됨)
✅ SELECT * FROM professor executed (SELECT * FROM professor 실행)
✅ All data correctly saved (모든 데이터가 올바르게 저장됨)

**Screenshot content includes (스크린샷 포함 내용):**

- All 5 rows of professor information displayed (5행의 교수 정보 모두 표시)

**Expected result (예상 결과):**

```
prof_id | prof_name      | department           | position             | salary
1       | Alex Kim       | Computer Science     | Professor            | 7500000.00
2       | Sarah Lee      | Software Engineering | Associate Professor  | 6800000.00
3       | David Park     | Information Security | Assistant Professor  | 5900000.00
4       | Emily Choi     | Data Science         | Professor            | 7800000.00
5       | Michael Kang   | Computer Science     | Associate Professor  | 6500000.00
```

---

### Question 18: ALTER TABLE Modifications

**Completion Criteria (완료 기준):**

✅ ALTER TABLE professor ADD phone VARCHAR(15); executed (ALTER TABLE professor ADD phone VARCHAR(15); 실행됨)
✅ ALTER TABLE professor MODIFY salary DECIMAL(12,2); executed (ALTER TABLE professor MODIFY salary DECIMAL(12,2); 실행됨)
✅ DESC professor result: 6 columns displayed (phone added, salary type changed) (DESC professor 결과: 6개 열 표시 - phone 추가, salary 타입 변경)

**Screenshot content includes (스크린샷 포함 내용):**

- Modified table structure (수정된 테이블 구조)
- New phone column displayed (새로 추가된 phone 열 표시)
- salary type changed to DECIMAL(12,2) (salary 타입이 DECIMAL(12,2)로 변경됨)

---

### Question 19: Bank Account Table Design

**Model Answer (모범 답안):**

```sql
-- Create bank account table (은행 계좌 테이블 생성)
CREATE TABLE bank_account (
    account_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_name VARCHAR(30) NOT NULL,
    account_type VARCHAR(20) NOT NULL,
    balance DECIMAL(15,2) DEFAULT 0,
    opening_date DATE DEFAULT CURRENT_DATE,
    last_transaction_date DATETIME
);

-- Insert sample account data (샘플 계좌 데이터 입력)
INSERT INTO bank_account VALUES
(1, 'Alex Kim', 'Savings', 5000000.00, CURRENT_DATE, NULL),
(2, 'Sarah Lee', 'Time Deposit', 2000000.00, CURRENT_DATE, '2024-12-25 14:30:00'),
(3, 'David Park', 'Loan', 10000000.00, CURRENT_DATE, '2024-12-24 09:15:00');

-- Query all accounts (모든 계좌 조회)
SELECT * FROM bank_account;
```

**Data type selection reasons (데이터 타입 선택 이유):**

- **account_id:** INT PRIMARY KEY AUTO_INCREMENT → Auto-generated account number, no duplication (계좌번호 자동 생성, 중복 없음)
- **customer_name:** VARCHAR(30) NOT NULL → Customer name required (고객명은 필수)
- **account_type:** VARCHAR(20) NOT NULL → Account type required (계좌타입 필수)
- **balance:** DECIMAL(15,2) DEFAULT 0 → Financial amount needs precision, default 0 (금액은 정확도 필요, 기본값 0)
- **opening_date:** DATE DEFAULT CURRENT_DATE → Automatically save current date (자동으로 현재 날짜 저장)
- **last_transaction_date:** DATETIME → Time information needed (NULL allowed) (시간 정보 필요 - NULL 가능)

---

### Question 20: Improved Product Table

**Model Answer (모범 답안):**

```sql
-- Create improved product table (개선된 product 테이블 생성)
CREATE TABLE product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50) NOT NULL UNIQUE,
    price DECIMAL(10,2) CHECK (price >= 0),
    stock INT DEFAULT 0 CHECK (stock >= 0),
    category VARCHAR(30),
    created_date DATE DEFAULT CURRENT_DATE,
    description TEXT
);

-- Insert sample product data (샘플 상품 데이터 입력)
INSERT INTO product VALUES
(1, 'Wireless Mouse', 45000.00, 100, 'Electronics', CURRENT_DATE, 'Comfortable grip wireless mouse'),
(2, 'Mechanical Keyboard', 120000.00, 50, 'Electronics', CURRENT_DATE, 'RGB LED mechanical keyboard'),
(3, 'Monitor Arm', 65000.00, 75, 'Electronics', CURRENT_DATE, 'Stand-type monitor arm'),
(4, 'Desk', 250000.00, 20, 'Furniture', CURRENT_DATE, 'Solid wood study desk'),
(5, 'Chair Cushion', 28000.00, 150, 'Furniture', CURRENT_DATE, 'Breathable mesh chair cushion');

-- Query all products (모든 상품 조회)
SELECT * FROM product;
```

**Reasons for constraint selection (제약조건 선택 이유):**

- **product_id:** PRIMARY KEY + AUTO_INCREMENT → Auto-generate product ID, no duplication (상품ID 자동 생성, 중복 없음)
- **product_name:** NOT NULL + UNIQUE → Product name required, no duplicates (상품명 필수, 중복 불가)
- **price:** DECIMAL(10,2) + CHECK (price >= 0) → Financial amount needs precision, prevent negative (금액 정확도 필요, 음수 방지)
- **stock:** DEFAULT 0 + CHECK (stock >= 0) → Default 0, prevent negative (기본값 0, 음수 방지)
- **category:** VARCHAR(30) NULL allowed → Classification information (분류 정보)
- **created_date:** DEFAULT CURRENT_DATE → Automatically save registration date (자동으로 등록일 저장)
- **description:** TEXT → Detailed product description storage (상세 설명 저장 가능)

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
