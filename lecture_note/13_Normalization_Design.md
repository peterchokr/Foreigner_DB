# Chapter 13. Normalization and Database Design

---

## 📖 Class Overview

In this chapter, you will learn normalization, the foundation of efficient and integrity-based database design. Normalization is the process of minimizing data duplication and preventing anomalies to maintain data consistency. You will study normalization stages from 1st Normal Form to 3rd Normal Form and BCNF, database design methods through ER diagrams, and practical application of normalization. The goal is to develop the ability to design actual databases based on theoretical foundations.

이 장에서는 효율적이고 무결성 있는 데이터베이스 설계의 기초인 정규화(Normalization)를 학습합니다.    
정규화는 데이터의 중복을 최소화하고 이상 현상(Anomaly)을 방지하여 데이터의 일관성을 유지하는 과정입니다. 1차 정규형부터 3차 정규형, BCNF까지의 정규화 단계와 ER 다이어그램을 통한 데이터베이스 설계 방법, 그리고 실무에서의 정규화 적용을 다룹니다. 이론적 기초를 바탕으로 실제 데이터베이스를 설계할 수 있는 능력을 개발하는 것이 목표입니다.

---

## 📚 Part 1: Theoretical Learning

### What You'll Learn in This Section

- Concept and goals of normalization (정규화의 개념과 목표)
- Functional Dependency (함수 종속성)
- 1st Normal Form (1NF) (1차 정규형)
- 2nd Normal Form (2NF) (2차 정규형)
- 3rd Normal Form (3NF) (3차 정규형)
- BCNF (Boyce-Codd Normal Form) (BCNF)
- ER Diagram and design principles (ER 다이어그램 및 설계 원칙)
- De-normalization considerations (비정규화 고려사항)

---

### 13.1 Normalization Concept

Normalization is the process of systematically decomposing tables to eliminate anomalies in databases and ensure data integrity.

정규화는 데이터베이스의 이상 현상을 제거하고 데이터 무결성을 보장하기 위해 테이블을 체계적으로 분해하는 과정입니다.

**Goals (목표):**

- Minimize data duplication (데이터 중복 최소화)
- Eliminate anomalies (insertion, update, deletion) (이상 현상 제거 삽입, 수정, 삭제 이상)
- Maintain data integrity (데이터 무결성 유지)
- Storage space efficiency (저장 공간 효율성)

**Anomalies (이상 현상):**

**1. Insertion Anomaly (삽입 이상):**

New data insertion requires unnecessary information to be entered together (새로운 데이터 삽입 시 불필요한 정보도 함께 삽입해야 함)

**2. Update Anomaly (수정 이상):**

When updating data, multiple rows of the same information must be updated (데이터 수정 시 같은 정보의 여러 행을 수정해야 함)

**3. Deletion Anomaly (삭제 이상):**

When deleting necessary data, unwanted information is also deleted (필요한 데이터를 삭제할 때 원하지 않는 정보까지 삭제됨)

---

### 13.2 Functional Dependency

Functional dependency represents dependency relationships between attributes.

함수 종속성은 속성 간의 종속 관계를 나타냅니다.

**Notation (표기):** X → Y (When X is determined, Y is uniquely determined) (X가 결정되면 Y도 유일하게 결정됨)

**Example (예시):**

- Student ID → Student Name, Major, Grade (학번 → 학생명, 학과, 학년)
- Employee ID → Employee Name, Department, Salary (사원번호 → 사원명, 부서, 급여)

**Full Functional Dependency (완전 함수 종속):**

- Y depends on entire X (not on partial X) (Y가 X 전체에 종속 X의 일부에는 종속되지 않음)

**Partial Functional Dependency (부분 함수 종속):**

- Y depends only on part of X (undesirable) (Y가 X의 일부에만 종속 불바람직)

**Transitive Functional Dependency (이행 함수 종속):**

- If X → Y and Y → Z, then X → Z (goal of 3NF is to remove this) (X → Y, Y → Z이면 X → Z 이를 제거하는 것이 3NF의 목표)

---

### 13.3 1st Normal Form (1NF)

**1NF Condition (1NF의 조건):**

All attribute values must be atomic values (cannot be further decomposed) (모든 속성 값이 원자값 더 이상 분해할 수 없는 값)

**Incorrect Example (잘못된 예시):**

| Student ID | Name | Phone Number |
|-----------|------|--------------|
| 001 | Alex Johnson | 02-1234-5678, 010-1111-2222 |

**Normalized Example (정규형 예시):**

| Student ID | Name | Phone Number | Phone Type |
|-----------|------|--------------|------------|
| 001 | Alex Johnson | 02-1234-5678 | Home |
| 001 | Alex Johnson | 010-1111-2222 | Mobile |

---

### 13.4 2nd Normal Form (2NF)

**2NF Condition (2NF의 조건):**

- Satisfies 1NF (1NF를 만족)
- All non-key attributes have complete functional dependency on entire primary key (모든 비주요 속성이 기본키 전체에 완전 함수 종속)

**Composite Key Table Example (복합키 테이블 예시):**

**Incorrect Example (잘못된 예):**

| Student ID | Course ID | Course Name | Credits | Grade |
|-----------|-----------|-------------|---------|-------|
| 001 | CS101 | Data Structures | 3 | A |

Problem: Course Name and Credits depend only on Course ID (not on Student ID + Course ID) (강의명, 학점은 강의번호에만 종속 학번+강의번호에 완전 종속하지 않음)

**Normalized Example (정규형 예):**

**Enrollment Table (수강 테이블):**

| Student ID | Course ID | Grade |
|-----------|-----------|-------|
| 001 | CS101 | A |

**Course Table (강의 테이블):**

| Course ID | Course Name | Credits |
|-----------|-------------|---------|
| CS101 | Data Structures | 3 |

---

### 13.5 3rd Normal Form (3NF)

**3NF Condition (3NF의 조건):**

- Satisfies 2NF (2NF를 만족)
- No non-key attribute has transitive functional dependency on primary key (모든 비주요 속성이 기본키에 이행적으로 함수 종속하지 않음)

**Incorrect Example (잘못된 예):**

| Student ID | Name | Major | Department Office |
|-----------|------|-------|------------------|
| 001 | Alex Johnson | Computer Science | Room 301 |

Problem: Department Office depends on Major (transitive dependency) (학과사무실은 학과에 종속 이행적 함수 종속)

**Normalized Example (정규형 예):**

**Student Table (학생 테이블):**

| Student ID | Name | Major |
|-----------|------|-------|
| 001 | Alex Johnson | Computer Science |

**Major Table (학과 테이블):**

| Major | Department Office |
|-------|------------------|
| Computer Science | Room 301 |

---

### 13.6 BCNF (Boyce-Codd Normal Form)

**BCNF Condition (BCNF의 조건):**

For every functional dependency X → Y, X must be a superkey (모든 함수 종속 X → Y에서 X가 슈퍼키)

**Difference between 3NF and BCNF (3NF와 BCNF의 차이):**

- 3NF: Only non-key attributes depend on primary key (3NF: 비주요 속성만 기본키에 종속)
- BCNF: All attributes depend only on superkey (BCNF: 모든 속성이 슈퍼키에만 종속)

**BCNF Violation Example (BCNF 위반 예시):**

| Professor | Subject | Time |
|-----------|---------|------|
| Prof. Kim | Data Structures | Monday, Wednesday, Friday |

Problem: Subject → Professor is false, but Subject → Time exists where Subject is not a superkey (과목 → 교사는 아니지만, 과목 → 시간에서 과목은 슈퍼키가 아님)

---

### 13.7 ER Diagram (Entity-Relationship Diagram)

ER diagram is a visual representation of database design.

ER 다이어그램은 데이터베이스 설계의 시각적 표현입니다.

**Basic Elements (기본 요소):**

- **Entity (엔티티):** Target for storing information (e.g., Student, Course) (정보를 저장할 대상 예: 학생, 강의)
- **Attribute (속성):** Characteristics of entity (e.g., Student ID, Student Name) (엔티티의 특성 예: 학번, 학생명)
- **Relationship (관계):** Association between entities (엔티티 간의 연관 관계)

**Cardinality (카디널리티):**

- 1:1 (One-to-One): One student has one student ID (한 명의 학생은 하나의 학번)
- 1:N (One-to-Many): One professor teaches multiple courses (한 명의 교수는 여러 강의)
- M:N (Many-to-Many): Students take multiple courses, courses have multiple students (학생은 여러 강의, 강의는 여러 학생)

---

### 13.8 Database Design Process

**Step 1: Requirements Analysis (1단계: 요구사항 분석)**

- Collect and analyze data (데이터 수집 및 분석)
- Identify business rules (비즈니스 규칙 파악)

**Step 2: Conceptual Design (2단계: 개념적 설계)**

- Create ER diagram (ER 다이어그램 작성)
- Define entities and relationships (엔티티와 관계 정의)

**Step 3: Logical Design (3단계: 논리적 설계)**

- Apply normalization (정규화 적용)
- Define schema (스키마 정의)

**Step 4: Physical Design (4단계: 물리적 설계)**

- Determine storage structure (저장소 구조 결정)
- Design indexes (인덱스 설계)

**Step 5: Implementation and Verification (5단계: 구현 및 검증)**

- Create tables with DDL (DDL로 테이블 생성)
- Verify data integrity (데이터 무결성 검증)

---

### 13.9 Foreign Key and Relationships

**Foreign Key (외래키):**

- References primary key of another table (다른 테이블의 기본키를 참조)
- Guarantees referential integrity (관계 무결성 보장)
- Control cascade tasks with ON DELETE, ON UPDATE options (ON DELETE, ON UPDATE 옵션으로 연쇄 작업 제어)

**Example (예시):**

```sql
-- Create enrollment table with foreign keys (외래키를 가지는 수강 테이블 생성)
CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

---

### 13.10 De-normalization

De-normalization intentionally reverses normalization for performance.

비정규화는 성능을 위해 의도적으로 정규화를 역행합니다.

**Situations (상황):**

- Performance degradation due to complex JOINs (복잡한 JOIN으로 인한 성능 저하)
- When read performance optimization is needed (읽기 성능 최적화가 필요할 때)
- When queries are very frequent (조회가 매우 빈번할 때)

**Example (예시):**

Store department name directly in student table (originally department name only in department table) (학생 테이블에 학과명을 직접 저장 원래는 학과명은 학과 테이블에만)

**Precautions (주의사항):**

- Data consistency problems may occur (데이터 일관성 문제 발생 가능)
- Multiple rows must be updated when modifying (수정 시 여러 행을 업데이트해야 함)

---

## 📚 Part 2: Sample Data

### Online Shopping Mall Database

**Customers Table (고객 테이블):**

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch13_normal CHARACTER SET utf8mb4;
USE ch13_normal;

-- Create customers table (고객 테이블 생성)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    email VARCHAR(50),
    city VARCHAR(30)
);
```

**Products Table (상품 테이블):**

```sql
-- Create products table (상품 테이블 생성)
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(50),
    category_id INT,
    price DECIMAL(10, 2)
);
```

**Categories Table (카테고리 테이블):**

```sql
-- Create categories table (카테고리 테이블 생성)
CREATE TABLE categories (
    category_id INT PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(30)
);
```

**Orders Table (주문 테이블):**

```sql
-- Create orders table (주문 테이블 생성)
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

**OrderDetails Table (주문 상세 테이블):**

```sql
-- Create order details table (주문 상세 테이블 생성)
CREATE TABLE order_details (
    order_detail_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
```

---

## 💻 Part 3: Learning and Practice

### What You'll Learn in This Section

- Practical application of normalization stages (정규화 단계의 실제 적용)
- Identification and resolution of anomalies (이상 현상의 식별과 해결)
- ER diagram creation (ER 다이어그램 작성)
- Database design practice (데이터베이스 설계 실습)

**13-1. 1NF Identification (1NF 식별)**

Convert non-normalized data to 1NF.

비정규형 데이터를 1NF로 변환하세요.

```sql
-- Problem table: Phone numbers are not atomic values (문제 테이블: 전화번호가 원자값이 아님)
-- Solution: Separate phone numbers into multiple rows (해결: 전화번호를 여러 행으로 분리)

CREATE TABLE students (
    student_id VARCHAR(5),
    name VARCHAR(50)
);

CREATE TABLE phone_numbers (
    student_id VARCHAR(5),
    phone_number VARCHAR(20)
);
```

**13-2. 2NF Conversion (2NF 변환)**

Convert 1NF data to 2NF.

1NF 데이터를 2NF로 변환하세요.

```sql
-- Problem: Partial functional dependency - course name and credits depend only on course ID
-- (부분 함수 종속 - 강의명과 학점은 강의번호에만 종속)

CREATE TABLE enrollment (
    student_id VARCHAR(5),
    course_id VARCHAR(5),
    grade CHAR(1),
    PRIMARY KEY (student_id, course_id)
);

CREATE TABLE courses (
    course_id VARCHAR(5),
    course_name VARCHAR(50),
    credits INT,
    PRIMARY KEY (course_id)
);
```

**13-3. 3NF Conversion (3NF 변환)**

Convert 2NF data to 3NF.

2NF 데이터를 3NF로 변환하세요.

```sql
-- Problem: Transitive functional dependency - department chairman depends on major
-- (이행 함수 종속 - 학과장은 학과에 종속)

CREATE TABLE students (
    student_id VARCHAR(5),
    name VARCHAR(50),
    major_id INT,
    PRIMARY KEY (student_id)
);

CREATE TABLE majors (
    major_id INT,
    major_name VARCHAR(50),
    chairman VARCHAR(50),
    PRIMARY KEY (major_id)
);
```

**13-4. BCNF Verification (BCNF 확인)**

Verify if data satisfies BCNF.

데이터가 BCNF를 만족하는지 확인하세요.

```sql
-- Problem: Subject → Time but Subject is not a superkey
-- (문제: 과목 → 시간이지만 과목은 슈퍼키가 아님)

-- BCNF form conversion (BCNF 형태로 변환)
CREATE TABLE professor_assignment (
    professor_id INT,
    course_id INT,
    PRIMARY KEY (professor_id, course_id)
);

CREATE TABLE course_schedule (
    course_id INT,
    time_slot VARCHAR(20),
    PRIMARY KEY (course_id, time_slot)
);
```

**13-5. Functional Dependency Identification (함수 종속성 식별)**

Find functional dependencies in a table.

테이블에서 함수 종속성을 찾아내세요.

```sql
-- Employee table functional dependencies (직원 테이블의 함수 종속성)
-- Employee ID → Name, Department, Job Title
-- Department → Department Name, Location
-- Job Title → Salary Range

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    job_id INT
);

CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50),
    location VARCHAR(50)
);

CREATE TABLE jobs (
    job_id INT PRIMARY KEY,
    job_title VARCHAR(50),
    min_salary DECIMAL(10, 2),
    max_salary DECIMAL(10, 2)
);
```

---

## 📝 Part 4: Assignment Guidelines

### Theoretical Assignments

**Assignment 1**: Explain the goals and conditions of each normalization stage (1NF, 2NF, 3NF, BCNF) in detail. Describe the problems eliminated at each normal form with specific examples.

정규화의 목표와 각 단계(1NF, 2NF, 3NF, BCNF)의 조건을 상세히 설명하세요. 각 정규형에서 제거되는 문제점을 구체적인 예시와 함께 서술하세요.

**Assignment 2**: Explain the concepts of insertion, update, and deletion anomalies and discuss how each is resolved through normalization. Present cases that can occur in actual business.

삽입 이상, 수정 이상, 삭제 이상의 개념을 설명하고, 각각이 정규화로 어떻게 해결되는지 논의하세요. 실제 비즈니스에서 발생할 수 있는 사례를 제시하세요.

**Assignment 3**: Explain the concept of functional dependency and the differences between partial and transitive functional dependency. Clearly describe how they are eliminated during normalization.

함수 종속성의 개념과 부분 함수 종속, 이행 함수 종속의 차이점을 설명하세요. 정규화 과정에서 이들이 어떻게 제거되는지 명확히 서술하세요.

**Assignment 4**: Explain the concept and components of ER diagram. Discuss the role and importance of ER diagram in database design process.

ER 다이어그램의 개념과 구성 요소를 설명하세요. 데이터베이스 설계 프로세스에서 ER 다이어그램의 역할과 중요성을 논의하세요.

**Assignment 5**: Analyze the trade-off between normalization and de-normalization. Present how to balance between normalization and performance in real-world practice.

정규화와 비정규화의 트레이드오프를 분석하세요. 실무에서 정규화와 성능 사이의 균형을 어떻게 맞춰야 하는지 제시하세요.

**Submission Format**: Word or PDF document (2-3 pages)

제출 형식: Word 또는 PDF 문서 (2-3페이지)

---

### Practical Assignments

**Assignment 1**: Perform normalization practice: Convert non-normalized table to 1NF, 1NF to 2NF, 2NF to 3NF. Explain how anomalies are eliminated at each stage.

정규화 실습을 수행하세요: 비정규형 테이블을 1NF로, 1NF를 2NF로, 2NF를 3NF로 변환하세요. 각 단계에서 이상 현상이 어떻게 제거되는지 설명하세요.

**Assignment 2**: Analyze functional dependencies: Identify all functional dependencies in a table, find partial and transitive dependencies, and create a normalization plan to eliminate each.

함수 종속성을 분석하세요: 테이블의 모든 함수 종속성 식별, 부분 함수 종속과 이행 함수 종속 찾기, 각각을 제거하기 위한 정규화 계획 수립하세요.

**Assignment 3**: Design a complex database: Create ER diagram, define entities and relationships, convert to normalized schema, and implement with SQL.

복잡한 데이터베이스를 설계하세요: ER 다이어그램 작성, 엔티티와 관계 정의, 정규화된 스키마로 변환, SQL로 구현하세요.

**Assignment 4**: Design real business systems: Choose from online shopping mall, university information system, or hospital management system. Analyze requirements, create ER diagram, apply normalization, write complete DDL.

실제 비즈니스 시스템을 설계하세요: 온라인 쇼핑몰, 대학 정보 시스템, 병원 관리 시스템 중 선택. 요구사항 분석 및 ER 다이어그램 작성, 정규화 적용, 완전한 DDL 작성하세요.

**Assignment 5**: Execute all queries provided from 13-1 to 13-40 in Part 3 and attach result screenshots for each. Additionally, design a comprehensive information system (optional) database completely, including design process, final ER diagram, normalization analysis, and completed DDL in detailed design document. Verify that design results satisfy each normal form condition.

Part 3의 실습 13-1부터 13-40까지 제공된 모든 쿼리를 직접 실행하고, 각 결과를 스크린샷으로 첨부하세요. 추가로 종합적인 정보 시스템(선택 사항)의 데이터베이스를 완전히 설계하여, 설계 과정, 최종 ER 다이어그램, 정규화 분석, 완성된 DDL을 포함한 상세한 설계 문서를 제출하세요. 설계 결과물이 각 정규형 조건을 만족하는지 검증하세요.

**Submission Format**: SQL file (Ch13_Normalization_Design_[StudentID].sql), design document, and ER diagram

제출 형식: SQL 파일 (Ch13_Normalization_Design_[학번].sql), 설계 문서, 및 ER 다이어그램

---

Thank you for your attention.

Cho Jeonghyun (peterchokr@gmail.com). Yeungnam University College
