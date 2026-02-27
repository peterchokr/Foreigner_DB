# Chapter 13. Normalization and Database Design - Practice Problems

Dear students! After completing Chapter 13, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

13장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 13, you should understand the following:

- Normalization concept and objectives (정규화의 개념과 목표)
- Anomaly identification and resolution (이상 현상 식별 및 해결)
- Functional dependency (함수 종속성)
- First through third normal forms, BCNF (1차~3차 정규형, BCNF)
- ER diagram creation (ER 다이어그램 작성)
- Database design process (데이터베이스 설계 프로세스)
- Foreign keys and referential integrity (외래키와 관계 무결성)

---

# Multiple Choice Questions (10 Questions)

## Beginner Level (5 Questions) - Basic Concepts

**Question 1** Primary objective of normalization? (정규화의 주요 목적은?)

- ① Increase database size (데이터베이스 크기 증가)
- ② Minimize data redundancy and eliminate anomalies (데이터 중복 최소화 및 이상 현상 제거)
- ③ Speed up query retrieval (조회 속도 빠르게 하기)
- ④ Unify programming language (프로그래밍 언어 통일)

---

**Question 2** Which is NOT type of anomaly? (이상 현상의 종류로 옳지 않은 것은?)

- ① Insertion Anomaly (삽입 이상)
- ② Update Anomaly (수정 이상)
- ③ Deletion Anomaly (삭제 이상)
- ④ Processing Anomaly (처리 이상)

---

**Question 3** Condition for First Normal Form (1NF)? (1차 정규형의 조건은?)

- ① All attributes are atomic values (모든 속성이 원자값)
- ② Remove partial function dependency (부분 함수 종속 제거)
- ③ Remove transitive function dependency (이행 함수 종속 제거)
- ④ Define superkey (슈퍼키 정의)

---

**Question 4** Which is NOT basic element of ER diagram? (ER 다이어그램의 기본 요소로 옳지 않은 것은?)

- ① Entity (엔티티)
- ② Attribute (속성)
- ③ Relationship (관계)
- ④ Function (함수)

---

**Question 5** Example of 1:N (one-to-many) relationship? (1:N 관계의 예시는?)

- ① Student and student ID (학생과 학번)
- ② Professor and courses (교수와 강의)
- ③ Department and department name (부서와 부서명)
- ④ Employee and national ID (직원과 주민등록번호)

---

## Intermediate Level (3 Questions) - Concept Application

**Question 6** Which violates Second Normal Form (2NF)? (다음 중 2차 정규형 위반은?)

```
enrollment (student_id, course_id, course_name, grade)
```

- ① course_name depends only on course_id (강의명이 강의번호에만 종속)
- ② grade depends on student_id and course_id (성적이 학번과 강의번호에 종속)
- ③ student_id is candidate key (학번이 주요 속성)
- ④ course_id is candidate key (강의번호가 주요 속성)

---

**Question 7** Condition for Third Normal Form (3NF)? (3차 정규형의 조건으로 옳은 것은?)

- ① Satisfy 2NF (2NF를 만족)
- ② All non-key attributes not transitively dependent on PK (모든 비주요 속성이 기본키에 이행적으로 함수 종속하지 않음)
- ③ Both ① and ② (①과 ② 모두)
- ④ Depend only on superkey (슈퍼키에만 종속)

---

**Question 8** Purpose of Foreign Key (FK)? (외래키의 목적은?)

- ① Encrypt data (데이터 암호화)
- ② Define table relationships and ensure referential integrity (테이블 간 관계 정의 및 참조 무결성 보장)
- ③ Improve query speed (쿼리 속도 향상)
- ④ Replicate data (데이터 복제)

---

## Advanced Level (2 Questions) - Critical Thinking

**Question 9** When to use normalization vs denormalization? (정규화와 비정규화의 상황은?)

- ① Always use normalization only (항상 정규화만 사용)
- ② Normalization theory, denormalization practice (정규화는 이론, 비정규화는 실무)
- ③ Design normalized, consider denormalization if performance needed (정규화 후 성능 필요시 비정규화)
- ④ Always use denormalization regardless (상황 무관 비정규화)

---

**Question 10** Meaning of functional dependency X → Y? (함수 종속성 X → Y의 의미는?)

- ① X depends on Y (X가 Y에 종속)
- ② Y depends on X (Y가 X에 종속)
- ③ When X determined, Y uniquely determined (X가 결정되면 Y도 유일하게 결정됨)
- ④ Relationship between X and Y unclear (X와 Y의 관계 불명)

---

# Short Answer Questions (5 Questions)

## Beginner Level (3 Questions)

**Question 11** Define normalization and explain insertion, update, deletion anomalies. (정규화의 정의와 이상 현상을 설명하시오.)

---

**Question 12** Explain conditions for 1NF, 2NF, 3NF. (1차, 2차, 3차 정규형의 조건을 각각 설명하시오.)

---

**Question 13** Explain ER diagram elements (entity, attribute, relationship) and cardinality (1:1, 1:N, M:N). (ER 다이어그램의 기본 요소와 카디널리티를 설명하시오.)

---

## Intermediate Level (1 Question)

**Question 14** Explain functional dependency, complete/partial/transitive dependency with examples. (함수 종속성과 완전/부분/이행 함수 종속을 설명하고 예시하시오.)

---

## Advanced Level (1 Question)

**Question 15** Describe database design process and explain when normalization is applied. (데이터베이스 설계 프로세스를 설명하고, 정규화가 어느 단계에서 적용되는지 설명하시오.)

---

# Practical Problems (5 Questions)

## Beginner Level (2 Questions)

**Question 16** Convert unnormalized data to 1NF. (다음 비정규형 데이터를 1NF로 변환하시오.)

```
Problem data (phone numbers are complex values):
students (student_id, name, phone_number)
001, Alex Kim, 02-123-4567 / 010-1111-2222
002, Sarah Lee, 031-456-7890 / 010-2222-3333

Requirements:
1. Explain unnormalized problems
2. Design 1NF table
3. Implement with CREATE TABLE
4. Insert data
```

Submission: Conversion explanation and 1NF table SQL (제출: 변환 과정 설명 및 1NF 테이블 SQL)

---

**Question 17** Convert 1NF data to 2NF. (다음 1NF 데이터를 2NF로 변환하시오.)

```
Problem data (partial function dependency):
enrollment (student_id, course_id, course_name, credit, grade)
001, CS101, Data Structure, 3, A
001, CS102, Algorithm, 4, B

Problem: course_name, credit depend only on course_id (not on student_id+course_id)

Requirements:
1. Explain partial dependency
2. Convert to 2NF (table separation)
3. Set foreign keys
4. Insert data
```

Submission: 2NF table structure and SQL (제출: 2NF 테이블 구조 및 SQL)

---

## Intermediate Level (2 Questions)

**Question 18** Convert 2NF data to 3NF. (다음 2NF 데이터를 3NF로 변환하시오.)

```
Problem data (transitive function dependency):
students (student_id, name, department, dept_office)
001, Alex Kim, Computer Science, Room 301
002, Sarah Lee, Computer Science, Room 301
003, David Park, Electronics, Room 302

Problem: dept_office depends on department (not directly on student_id)
         student_id → department → dept_office (transitive)

Requirements:
1. Explain transitive dependency
2. Convert to 3NF (table separation)
3. Define foreign keys
4. Insert all data
5. Confirm normalization benefits
```

Submission: 3NF structure, SQL, normalization effect analysis (제출: 3NF 테이블 구조, SQL, 정규화 효과 분석)

---

**Question 19** Design online shopping database with ER diagram and implement. (온라인 쇼핑몰 데이터베이스를 ER 다이어그램으로 설계하고 구현하시오.)

```
Requirements:
1. ER Diagram Design
   - Entities: Customers, Products, Categories, Orders, OrderDetails
   - Relationships:
     * Customer 1:N Orders
     * Order 1:N OrderDetails
     * Product M:N Orders (via OrderDetails)
     * Category 1:N Products

2. Create Tables (apply 3NF)
   - Customers
   - Categories
   - Products (FK: category_id)
   - Orders (FK: customer_id)
   - OrderDetails (FK: order_id, product_id)

3. Insert Sample Data
   - 2 customers
   - 2 categories
   - 3 products
   - 2 orders
   - 3 order details

4. Verify Relationships
   - JOIN queries for customer orders
   - Category products retrieval
```

Submission: ER diagram explanation, SQL code, execution results (제출: ER 다이어그램 설명, SQL 코드, 실행 결과)

---

## Advanced Level (1 Question)

**Question 20** Design and implement complex database. (다음의 복잡한 데이터베이스 설계를 수행하시오.)

```
Requirements:
1. University Academic Management System Design
   - Entities: Students, Professors, Departments, Courses, Enrollments
   - Requirements:
     * Student belongs to one department (1:N)
     * Professor teaches multiple courses (1:N)
     * Course taught by one professor (1:1)
     * Course belongs to department (1:N)
     * Student takes multiple courses (M:N)

2. Apply Normalization
   - Each entity 3NF or higher
   - Functional dependency analysis
   - Eliminate anomalies

3. Set Data Integrity
   - Define primary keys
   - Constraint foreign keys
   - Data validation rules

4. Sample Data and Queries
   - Students per department
   - Courses per professor
   - Courses per student

Submission:
   - ER diagram explanation
   - Normalization analysis (1NF → 3NF process)
   - Complete SQL code
   - Sample data and validation queries

요구사항:

1. 대학 학사 관리 시스템 설계
   - 엔티티: Students, Professors, Departments, Courses, Enrollments

2. 정규화 적용
   - 각 엔티티 3NF 이상 적용
   - 함수 종속성 분석
   - 이상 현상 제거

3. 데이터 무결성 설정
   - 기본키 정의
   - 외래키 제약
   - 데이터 검증 규칙

4. 샘플 데이터 및 쿼리
   - 학과별 학생 수
   - 교수별 담당 강의
   - 학생별 수강 강의
```

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (10 Questions)

| Question | Answer | Explanation                                                                        |
| :------: | :----: | :--------------------------------------------------------------------------------- |
|    1    |   ②   | Normalization removes redundancy and anomalies (중복 제거와 이상 현상 제거)        |
|    2    |   ④   | Processing Anomaly not normalization anomaly (정규화 이상 아님)                    |
|    3    |   ①   | 1NF condition: atomic values (원자값 조건)                                         |
|    4    |   ④   | Function not ER element (ER 요소 아님)                                             |
|    5    |   ②   | One professor teaches multiple courses (여러 강의 담당)                            |
|    6    |   ①   | course_name depends only on course_id = 2NF violation (강의명이 강의번호에만 종속) |
|    7    |   ③   | Both ① and ② are conditions (①과 ② 모두 조건)                                  |
|    8    |   ②   | FK defines relationships and ensures integrity (관계 정의 및 참조 무결성)          |
|    9    |   ③   | Normalize first, denormalize if needed (정규화 후 필요시 비정규화)                 |
|    10    |   ③   | When X determined, Y uniquely determined (X 결정 시 Y 결정)                        |

---

## Short Answer Model Answers (5 Questions)

### Question 11: Normalization and Anomalies

**Model Answer (모범 답안):**

```
Normalization:
- Process of systematically decomposing tables to eliminate 
  anomalies and ensure data integrity

Objectives:
- Minimize data redundancy
- Eliminate anomalies
- Maintain data consistency

Anomalies:

1. Insertion Anomaly
   - Cannot insert new data without unnecessary information
   Example: Cannot register professor without course assignment

2. Update Anomaly
   - Must modify same info in multiple places
   Example: Changing professor name requires updating all courses
   Result: Inconsistency if only partial update

3. Deletion Anomaly
   - Unwanted data disappears when deleting needed data
   Example: Deleting only course also deletes professor info
```

---

### Question 12: Normal Form Conditions

**Model Answer (모범 답안):**

```
First Normal Form (1NF):
Condition:
- All attribute values are atomic (indivisible)
- No repeated attribute values

Example:
❌ Unnormalized:
students(student_id, phone_number: [02-123, 010-111])

✅ 1NF:
students(student_id, phone_number, type)
001, 02-123, home
001, 010-111, mobile

Second Normal Form (2NF):
Condition:
- Satisfy 1NF
- All non-key attributes completely dependent on primary key
  (no partial dependency on composite key part)

Example:
❌ 2NF violation:
enrollment(student_id, course_id, course_name, grade)
Problem: course_name depends only on course_id

✅ 2NF:
enrollment(student_id, course_id, grade)
courses(course_id, course_name)

Third Normal Form (3NF):
Condition:
- Satisfy 2NF
- All non-key attributes not transitively dependent on PK
  (X → Y, Y → Z means eliminate indirect Z dependency)

Example:
❌ 3NF violation:
students(student_id, department, dept_office)
Problem: dept_office → department → student_id (transitive)

✅ 3NF:
students(student_id, department)
departments(department, dept_office)
```

---

### Question 13: ER Diagram Elements and Cardinality

**Model Answer (모범 답안):**

```
Basic Elements:

1. Entity
   - Definition: Target holding information
   - ER notation: Rectangle
   - Example: Student, Course, Professor

2. Attribute
   - Definition: Entity characteristic
   - ER notation: Oval
   - Example: Student ID, name, department

3. Relationship
   - Definition: Connection between entities
   - ER notation: Diamond
   - Example: "Student takes Course"

Cardinality:

1:1 (One-to-One)
Example: Student and ID
- One student has exactly one ID
- One ID belongs to exactly one student

1:N (One-to-Many)
Example: Professor and Courses
- One professor can teach multiple courses
- Each course taught by one professor

M:N (Many-to-Many)
Example: Student and Courses
- One student can take multiple courses
- One course taken by multiple students
- Requires junction table (enrollment)
```

---

### Question 14: Functional Dependency Types

**Model Answer (모범 답안):**

```
Functional Dependency:
- Notation: X → Y (when X determined, Y uniquely determined)
- Meaning: X value determines Y value

Types:

1. Complete Function Dependency
   - Y depends on entire X
   - Y not dependent on X partial
   Example: (student_id, course_id) → grade
            grade needs both student_id and course_id

2. Partial Function Dependency ⚠️ 2NF violation
   - Y depends on X partial only
   Example: (student_id, course_id) → course_name
            course_name depends only on course_id

3. Transitive Function Dependency ⚠️ 3NF violation
   - X → Y, Y → Z therefore X → Z
   Example: student_id → department → dept_office
            student_id indirectly determines dept_office

Normalization Treatment:
- 1NF: Atomic values only
- 2NF: Eliminate partial dependencies
- 3NF: Eliminate transitive dependencies
```

---

### Question 15: Design Process and Normalization

**Model Answer (모범 답안):**

```
Database Design Process (5 Stages):

Stage 1: Requirements Analysis
- Understand business requirements
- Data collection
- User interviews

Stage 2: Conceptual Design
- Create ER diagram
- Define entities and relationships
- Design logical structure

Stage 3: Logical Design ← Normalization applied!
- Apply normalization stages (1NF → 3NF+)
- Analyze functional dependencies
- Finalize table structure

Stage 4: Physical Design
- Determine storage structure
- Index design
- Performance optimization

Stage 5: Implementation & Verification
- Create tables with DDL
- Validate data integrity
- Set constraints

Normalization Role:
✅ Applied in logical design stage
✅ Eliminate anomalies
✅ Ensure data consistency
✅ Improve storage efficiency

Flow:
Unnormalized → 1NF → 2NF → 3NF → BCNF
```

---

## Practical Problem Model Answers (5 Questions)

### Question 16: 1NF Conversion

**Completion Criteria (완료 기준):**

✅ Explain unnormalized problem (complex values)
✅ Convert to 1NF (atomic values only)
✅ Separate table (phone_numbers)

---

### Question 17: 2NF Conversion

**Completion Criteria (완료 기준):**

✅ Identify partial dependency
✅ Separate tables (enrollments, courses)
✅ Define foreign keys

---

### Question 18: 3NF Conversion

**Completion Criteria (완료 기준):**

✅ Identify transitive dependency
✅ Separate tables (students, departments)
✅ Analyze normalization benefits

---

### Question 19: ER Diagram Implementation

**Completion Criteria (완료 기준):**

✅ 5 table structures defined
✅ Foreign key relationships set
✅ Sample data inserted
✅ JOIN queries executed

---

### Question 20: Complex System Design

**Completion Criteria (완료 기준):**

✅ 5 entity ER diagram
✅ Normalization analysis per stage
✅ All constraints applied
✅ Validation queries written

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
