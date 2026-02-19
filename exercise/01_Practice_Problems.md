# Chapter 1. Database Overview - Practice Problems

Dear students! After completing Chapter 1, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

1장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 1, you should understand the following:

- Understanding the difference between data and information (데이터와 정보의 차이 이해)
- Differences between file systems and databases (파일 시스템과 데이터베이스의 차이)
- Characteristics of RDBMS and MySQL (RDBMS와 MySQL의 특징)
- MySQL installation and basic commands (MySQL 설치 및 기본 명령어)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** Which of the following is **information** (정보)?

- ① Student ID: 20240001 (학번: 20240001)
- ② Name: Alex Kim, Student ID: 20240001, Enrollment Year: 2024 (이름: 김철수, 학번: 20240001, 입학년도: 2024)
- ③ Grade Score: 85 (성적 점수: 85)
- ④ Course Code: CS101 (수강강좌 코드: CS101)

---

**Question 2** Which category does MySQL belong to? (MySQL은 다음 중 어느 카테고리에 속하는가?)

- ① File System (파일 시스템)
- ② Relational Database (RDBMS) (관계형 데이터베이스)
- ③ Flat Text Database (평면 텍스트 데이터베이스)
- ④ NoSQL Database (NoSQL 데이터베이스)

---

**Question 3** Which of the following is **NOT** a role of DBMS? (다음 중 DBMS의 역할이 **아닌** 것은?)

- ① Data Definition (Schema Design) (데이터 정의 - 스키마 설계)
- ② Data Manipulation (Input, Modification, Deletion) (데이터 조작 - 입력, 수정, 삭제)
- ③ Hardware Manufacturing (하드웨어 제조)
- ④ Data Security (Access Control) (데이터 보안 - 접근 제어)

---

**Question 4** What is the biggest problem with file systems? (파일 시스템의 가장 큰 문제점은?)

- ① Slow execution speed (실행 속도가 느림)
- ② Data inconsistency due to duplication (데이터 중복으로 인한 불일치 가능성)
- ③ Complex installation (설치가 복잡함)
- ④ Only English support (영어만 지원됨)

---

**Question 5** What is the meaning of NULL? (NULL 값의 의미는?)

- ① Zero (숫자 0)
- ② Empty string ('') (빈 문자열)
- ③ No value or unknown (값이 없거나 알 수 없음)
- ④ False (거짓)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Why is a database better than a file system in the following scenario? (다음 시나리오에서 데이터베이스가 파일 시스템보다 나은 이유는?)

"There is a university student information system. There are 1000 students, and each student takes multiple courses. When a student's name changes, it must be reflected everywhere in the system."

(대학교 학생 정보 시스템이 있습니다. 1000명의 학생이 있고, 학생이 여러 강좌를 수강합니다. 학생의 이름이 변경되면 시스템의 어디든지 반영되어야 합니다.)

- ① Just faster (더 빠르기만 함)
- ② Centralized management - modification in one place reflects everywhere (중앙 집중식 관리로 한 곳에서만 수정하면 모두 반영됨)
- ③ Provides a prettier interface (더 예쁜 인터페이스를 제공함)
- ④ More space = better security (용량을 많이 차지해서 더 안전함)

---

**Question 7** Which is the most inappropriate characteristic of RDBMS? (RDBMS의 특징으로 가장 부적절한 것은?)

- ① Table-based 2D structure (테이블 기반의 2차원 구조)
- ② Relationships between tables defined by foreign keys (테이블 간 관계를 외래키로 정의)
- ③ Use of SQL as a standard language (SQL이라는 표준 언어 사용)
- ④ Only hierarchical data storage (계층 구조의 데이터만 저장 가능)

---

**Question 8** Which is NOT a reason why MySQL is a standard database for web applications? (MySQL이 웹 애플리케이션의 표준 데이터베이스인 이유가 아닌 것은?)

- ① Open source and free (오픈소스로 무료)
- ② Part of the LAMP stack (LAMP 스택의 일부)
- ③ Provides the fastest performance (가장 빠른 성능을 제공)
- ④ Simple installation and operation (설치와 운영이 간단)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** Select all the advantages of database normalization. (다음 중 정규화(데이터베이스 정규화)의 장점을 모두 고르시오. - 복수 선택)

- ① Elimination of data duplication (데이터 중복 제거)
- ② Reduced storage space (저장 공간 절감)
- ③ All query speeds become faster (모든 쿼리 속도가 빨라짐)
- ④ Prevention of anomalies (Insertion, Update, Deletion) (이상 현상 방지 - 삽입, 수정, 삭제)

---

**Question 10** What is the most appropriate data storage method for the following situation? (다음 상황에서 가장 적절한 데이터 저장 방식은?)

"It is a hospital information system. There is patient information, doctor information, prescription information, and medical records. Data accuracy and consistency are very important. Also, only specific doctors can view specific patients' medical records."

(병원 정보 시스템입니다. 환자 정보, 의사 정보, 처방약 정보, 진료 기록 등이 있습니다. 데이터 정확성과 일관성이 매우 중요합니다. 또한 특정 환자의 진료 기록만 특정 의사가 조회할 수 있어야 합니다.)

- ① Excel file (Excel 파일 사용)
- ② Text file storage (텍스트 파일로 저장)
- ③ Relational Database (RDBMS) (관계형 데이터베이스)
- ④ Cloud note application (클라우드 메모장)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Explain the difference between "data" and "information" in your own words. (3-5 lines) ("데이터"와 "정보"의 차이를 자신의 말로 설명하시오. - 3~5줄)

---

**Question 12** List 3 commands you should check first when installing MySQL and explain the purpose of each. (MySQL을 설치했을 때 가장 먼저 확인해야 할 명령어 3개를 나열하고 각각의 목적을 설명하시오.)

---

**Question 13** Explain 2 or more problems that can occur when managing student information using a file system. (파일 시스템으로 학생 정보를 관리할 때 발생할 수 있는 문제점을 2가지 이상 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain the importance of "data security" among the roles of DBMS with real-world examples. (DBMS의 역할 중 "데이터 보안"의 중요성을 실생활 예시로 설명하시오.)

---

## Advanced Level (1 Question)

**Question 15** Compare the advantages and disadvantages of normalized and denormalized databases. Explain when normalization should be a top priority and when slight denormalization can be considered. (정규화된 데이터베이스와 정규화되지 않은 데이터베이스의 장단점을 비교하시오. 언제 정규화를 최우선으로 해야 하고, 언제 약간의 비정규화를 고려할 수 있는지 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Execute MySQL Workbench and perform the following, then provide a screenshot. (MySQL Workbench를 실행하고 다음을 수행한 후 스크린샷을 제시하시오.)

```sql
-- Step 1: Execute the following commands and verify results (1단계: 다음 명령어를 실행하고 결과 확인)
SELECT VERSION();
SELECT USER();

-- Verification Points (결과 확인 사항):
-- - Is the MySQL version displayed? (MySQL 버전이 표시되는가?)
-- - Is the current user information displayed? (현재 사용자 정보가 표시되는가?)

-- Submission: Screenshot showing the above results (제출: 위 결과가 나오는 스크린샷 1장)
```

---

**Question 17** Create the ch1_practice database and product table again, then perform the following. (ch1_practice 데이터베이스와 product 테이블을 다시 만들고, 다음을 수행하시오.)

```sql
-- Step 1: Create database (1. 데이터베이스 생성)
CREATE DATABASE ch1_practice CHARACTER SET utf8mb4;
USE ch1_practice;

-- Step 2: Create product table (2. product 테이블 생성)
CREATE TABLE product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50) NOT NULL,
    price INT NOT NULL,
    stock INT NOT NULL
);

-- Step 3: Verify table structure using DESC command (3. DESC 명령어로 테이블 구조 확인)
DESC product;

-- Step 4: Insert 3 product data (4. 3개 상품 데이터 입력)
INSERT INTO product VALUES
(1, 'Wireless Mouse', 45000, 100),
(2, 'Mechanical Keyboard', 120000, 50),
(3, 'Monitor Arm', 65000, 75);

-- Step 5: Query data using SELECT and take screenshot (5. SELECT로 데이터 조회 후 스크린샷)
SELECT * FROM product;

-- Submission: Screenshot showing table structure and data (제출: 테이블 구조와 데이터가 모두 보이는 스크린샷 1장)
```

---

## Intermediate Level (2 Questions)

**Question 18** Analyze the following situation and propose a database design. (다음 상황을 분석하고 데이터베이스 설계를 제시하시오.)

**Situation (상황):**

"An online bookstore sells books. Required information: Books (Book ID, Title, Author, Price, Stock), Customers (Customer ID, Name, Email, Address), Orders (Order ID, Customer ID, Order Date, Total Price), Order Details (Order ID, Book ID, Quantity, Unit Price)"

(온라인 서점에서 책을 판매합니다. 필요한 정보: 책(책ID, 제목, 저자, 가격, 재고), 고객(고객ID, 이름, 이메일, 주소), 주문(주문ID, 고객ID, 주문일자, 총가격), 주문상세(주문ID, 책ID, 수량, 단가))

**Questions (질문):**

1. How many tables are needed? (몇 개의 테이블이 필요한가?)
2. Explain the relationships between each table. (각 테이블 간의 관계를 설명하시오.)
3. Explain why normalization is necessary. (정규화가 필요한 이유를 설명하시오.)

**Submission:** Answers to the above questions (3-5 lines) (제출: 위 질문에 대한 답변 - 3~5줄)

---

**Question 19** Modify the product table as follows and provide a screenshot. (product 테이블을 다음과 같이 수정하고 스크린샷을 제시하시오.)

```sql
-- Step 1: Current product table (1. 현재 product 테이블)
DESC product;

-- Step 2: Add category column using ALTER TABLE (2. ALTER TABLE로 category 열 추가)
ALTER TABLE product ADD category VARCHAR(30);

-- Step 3: Verify modified product table structure (3. 수정된 product 테이블 구조 확인)
DESC product;

-- Step 4: Update existing data (4. 기존 데이터 업데이트)
UPDATE product SET category = 'Electronics' WHERE product_id IN (1, 2, 3);

-- Step 5: Verify final data (5. 최종 데이터 확인)
SELECT * FROM product;

-- Submission: Screenshot showing modified table structure and data (제출: 수정된 테이블 구조와 데이터가 보이는 스크린샷 1장)
```

---

## Advanced Level (1 Question)

**Question 20** Real-world situation analysis: Discover and improve the problems in the database you designed. (실제 상황 분석: 당신이 설계한 데이터베이스의 문제점을 발견하고 개선하시오.)

**Situation (상황):**

"You designed a student information system with a single table:

student_info table: student_id, name, email, phone, course_id, course_name, professor_name, grade, semester

Problems (문제점):
1. If a student takes 3 courses, the student information is repeated 3 times (학생이 3개 강좌를 수강하면 학생 정보가 3번 반복됨)
2. If the professor's name changes, it must be modified in all course records (교수 이름이 변경되면 모든 강좌 기록에서 수정해야 함)
3. Students without courses cannot be entered into the data (강좌가 없는 학생은 데이터 입력 불가능)"

**Questions (질문):**

1. What are the exact names of these problems? (위 문제점들의 정확한 명칭은? - 이상 현상의 종류)
2. How would you redesign the database? (데이터베이스를 어떻게 재설계할 것인가? - 테이블 분리 및 관계 정의)
3. What are 2 or more advantages of the improved design? (개선된 설계의 장점 2가지 이상?)

**Submission:** Detailed answers to the above questions (제출: 위 질문에 대한 상세 답변)

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation |
|:--------:|:------:|:-----------|
| 1 | ② | Processed and meaningful data = information (가공된 의미 있는 데이터 = 정보) |
| 2 | ② | MySQL is a representative RDBMS (MySQL은 대표적인 RDBMS) |
| 3 | ③ | DBMS is software, not hardware manufacturing (DBMS는 소프트웨어, 하드웨어 제조 아님) |
| 4 | ② | Data duplication → inconsistency when modified (데이터 중복 → 수정 시 일관성 문제) |
| 5 | ③ | NULL represents the state of no value (NULL은 값이 아닌 상태를 나타냄) |
| 6 | ② | Normalization removes duplication, modification in one place reflects everywhere (정규화로 중복 제거, 한 번의 수정으로 모두 반영) |
| 7 | ④ | RDBMS can represent various types of relationships (RDBMS는 다양한 형태의 관계 표현 가능) |
| 8 | ③ | MySQL advantage, but NOT 'fastest' performance (MySQL의 장점이지만 '가장 빠른' 성능은 아님) |
| 9 | ①②④ | ③ is incorrect: JOINs from normalization may slow down speed (③은 오답: 정규화로 JOIN이 많아지면 때론 속도 느려질 수 있음) |
| 10 | ③ | Data integrity + security + relationship expression needed = RDBMS optimal (데이터 무결성 + 보안 + 관계 표현 필요 = RDBMS 최적) |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Difference between "Data" and "Information"

**Model Answer (모범 답안):**

- Data: Unprocessed raw material (numbers, characters, etc.) (데이터: 가공되지 않은 원시 자료 - 숫자, 문자 등)
- Information: Result of meaningfully processing data (정보: 데이터를 의미 있게 처리한 결과)
- Example: 85 (data) → "Alex Kim received 85 points on the Database exam" (information) (예: 85 - 데이터 → "김철수가 데이터베이스 시험에서 85점을 받았다" - 정보)

---

### Question 12: MySQL Verification Commands

**Model Answer (모범 답안):**

```sql
-- Command 1: SELECT VERSION(); 
-- Purpose: Check MySQL version (MySQL 버전 확인)

-- Command 2: SELECT USER();     
-- Purpose: Check current user (현재 사용자 확인)

-- Command 3: SELECT DATABASE(); 
-- Purpose: Check currently selected database (현재 선택된 데이터베이스 확인)
```

---

### Question 13: File System Problems

**Model Answer (모범 답안 - 3가지 예시):**

1. **Update Anomaly (수정 이상):** Student name is stored in multiple files, so all must be modified → data inconsistency problem (학생 이름이 여러 파일에 저장되어 모두 수정해야 함 → 일관성 문제 발생)

2. **Deletion Anomaly (삭제 이상):** Deleting the last course taken by a student also deletes the student information → required data loss (마지막 수강 강좌 삭제 시 학생 정보도 함께 삭제됨 → 필요한 데이터 손실)

3. **Insertion Anomaly (삽입 이상):** Students without courses cannot be entered → difficult to register new students (강좌가 없는 학생은 데이터 입력 불가능 → 새 학생 등록 어려움)

---

### Question 14: Importance of Data Security

**Model Answer (모범 답안 - 실생활 예시):**

- **Hospital (병원):** Only doctors can view patient medical records (의사만 환자 의료 기록 조회 가능 - 환자 프라이버시 보호)
- **Bank (은행):** Employees can only view the account holder's account (직원은 계좌주인 계좌만 볼 수 있음 - 자산 정보 보호)
- **School (학교):** Students can only view their own grades (학생은 자신의 성적만 조회 가능 - 개인 정보 보호)
- **Conclusion (결론):** DBMS automatically controls this, so it is very important (DBMS는 이를 자동으로 제어하므로 매우 중요함 - 법적 준수, 신뢰성 확보)

---

### Question 15: Normalization vs. Denormalization

**Model Answer (모범 답안):**

**Normalized Database (정규화된 데이터베이스)**

- Advantages (장점): Data duplication eliminated (데이터 중복 제거), consistency guaranteed (일관성 보장), reduced storage space (저장공간 절감)
- Disadvantages (단점): Potential performance degradation due to JOINs (JOIN으로 인한 성능 저하 가능)

**Denormalized Database (정규화되지 않은 데이터베이스)**

- Advantages (장점): Fast query performance without JOINs (JOIN 없이 빠른 조회 성능)
- Disadvantages (단점): Data duplication (데이터 중복), consistency problems during modification (수정 시 일관성 문제)

**When to Prioritize Normalization (정규화를 우선할 때)**

- When data accuracy is critical (데이터 정확성이 중요한 업무)
- Example: Finance (banking), healthcare (hospitals), administration (government) (예: 금융 - 은행, 의료 - 병원, 행정 - 정부)

**When to Consider Denormalization (비정규화를 고려할 때)**

- When reading is frequent and speed is important (읽기가 많고 속도가 중요한 경우)
- Example: Analysis (분석), reporting (보고서), bulk queries (대량 조회) (예: 분석, 보고서, 대량 조회)

---

## Practical Problem Model Answers (5 Questions)

### Question 16: MySQL Installation Verification

**Completion Criteria (완료 기준):**

✅ SELECT VERSION() executed → MySQL version displayed (MySQL 버전 표시됨)
✅ SELECT USER() executed → root@localhost displayed (root@localhost 표시됨)
✅ Both commands successful → installation complete (두 명령어 모두 성공하면 설치 완료)

**Screenshot Content Includes (스크린샷 포함 내용):**

- MySQL Workbench Query window (MySQL Workbench 쿼리 창)
- Executed commands and results (실행된 명령어와 결과)

---

### Question 17: Product Table Creation and Data Entry

**Completion Criteria (완료 기준):**

✅ ch1_practice database created (ch1_practice 데이터베이스 생성됨)
✅ product table created (4 columns) (product 테이블 생성됨 - 4개 열)
✅ DESC product result shown: product_id, product_name, price, stock (DESC product 결과 표시)
✅ 3 product data inserted (3개 상품 데이터 입력됨)
✅ SELECT * FROM product result verified (SELECT * FROM product 결과 확인)

**Screenshot Content Includes (스크린샷 포함 내용):**

- Table structure (DESC result) (테이블 구조 - DESC 결과)
- Entered data (3 rows) (입력된 데이터 3행)

**Expected Result (예상 결과):**

```
product_id | product_name      | price  | stock
1          | Wireless Mouse    | 45000  | 100
2          | Mechanical Keyboard | 120000 | 50
3          | Monitor Arm       | 65000  | 75
```

---

### Question 18: Online Bookstore Database Design

**Model Answer (모범 답안):**

**1. Number of Tables Needed (필요한 테이블 수)**

- 4 tables (books, customers, orders, order_details) (4개의 테이블)

**2. Relationships Between Each Table (각 테이블 간의 관계)**

```
Customer (1) ──────→ (N) Order
                       │
                       ↓
Order_Detail (N) ←────┘
    │
    └────→ (1) Book
```

- One customer has multiple orders (1:N) (고객 1명이 여러 주문을 가짐)
- One order contains multiple products (1:N) (주문 1개가 여러 상품을 포함)
- One book can be included in multiple orders (1:N) (책 1권이 여러 주문에 포함될 수 있음)

**3. Why Normalization is Necessary (정규화가 필요한 이유)**

- Elimination of book information duplication (같은 책을 여러 주문에서 반복 저장하지 않음)
- When book price changes, only one place needs modification (book 정보의 중복 제거)
- Reduced storage space (저장 공간 절감)
- Data consistency guaranteed (일관성 보장)

---

### Question 19: ALTER TABLE Product Table Modification

**Completion Criteria (완료 기준):**

✅ ALTER TABLE product ADD category VARCHAR(30); executed (ALTER TABLE product ADD category VARCHAR(30); 실행됨)
✅ DESC product result shows 5 columns: product_id, product_name, price, stock, category (DESC product 결과: 5개 열 표시)
✅ UPDATE category values added (UPDATE로 category 값 추가됨)
✅ SELECT * FROM product final result verified (SELECT * FROM product 최종 결과 확인)

**Screenshot Content Includes (스크린샷 포함 내용):**

- Modified table structure (수정된 테이블 구조)
- Data with added category (category가 추가된 데이터)

**Expected Result (예상 결과):**

```
product_id | product_name      | price  | stock | category
1          | Wireless Mouse    | 45000  | 100   | Electronics
2          | Mechanical Keyboard | 120000 | 50    | Electronics
3          | Monitor Arm       | 65000  | 75    | Electronics
```

---

### Question 20: Database Design Improvement

**Model Answer (모범 답안):**

**1. Problem Names (Anomalies) (문제점의 명칭 - 이상 현상의 종류)**

- **Repeating Group (반복 그룹):** Student information is repeated as many times as the number of courses taken (학생 정보가 강좌 수만큼 반복됨)
- **Modification Anomaly (수정 이상):** When professor's name changes, modification needed in all records (교수 이름 변경 시 모든 기록에서 수정 필요)
- **Insertion Anomaly (삽입 이상):** Students without courses cannot be registered (강좌 없는 학생은 등록 불가능)

**2. Improved Redesign (Normalization) (개선된 재설계 - 정규화)**

Original table (has problems) (원본 테이블 - 문제 있음):

```sql
student_info (student_id, name, email, phone, course_id, course_name, 
professor_name, grade, semester)
```

Improved design (4 tables) (개선된 설계 - 4개 테이블):

```sql
student (student_id, name, email, phone)
course (course_id, course_name, professor_id)
professor (professor_id, professor_name)
enrollment (student_id, course_id, grade, semester)
```

Relationship diagram (관계도):

```
student (1) ────────→ (N) enrollment ←────── (1) course
                         │                      │
                         └─ grade, semester     │
                                            professor
```

**3. Advantages of Improved Design (개선된 설계의 장점)**

- **Data Duplication Eliminated (데이터 중복 제거):** Student information stored only once (학생 정보가 한 번만 저장됨)
- **Consistency Guaranteed (일관성 보장):** Modifying professor name in professor table only (교수 이름 수정 시 professor 테이블만 수정하면 됨)
- **Easy Insertion (삽입 용이):** Students without courses can be registered immediately in student table (강좌 없는 학생도 student 테이블에 바로 등록 가능)
- **Reduced Storage Space (저장 공간 절감):** Elimination of repeating information increases efficiency (반복되는 정보 제거로 효율성 증대)
- **Easier Maintenance (유지보수 간편):** Each table has a clear purpose (각 테이블이 명확한 목적을 가짐)

---

---

Thank you for your attention.

Jeonghyun Cho (peterchokr@gmail.com)
Yeungnam University College
