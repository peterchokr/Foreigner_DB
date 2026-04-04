# Chapter 5. JOIN Basics - Practice Problems

Dear students! After completing Chapter 5, please test your understanding through the following practice problems. Check the difficulty level of each section and study step by step.

5장을 완료한 후 다음 연습문제를 통해 개념을 확인해보세요. 각 섹션의 난이도를 확인하고 단계별로 공부하시면 됩니다.

---

## 📌 Learning Goals Verification (학습 목표 확인)

After completing Chapter 5, you should understand the following:

- Basic concept and syntax of INNER JOIN (INNER JOIN의 기본 개념과 문법)
- Role of ON clause (table connection conditions) (ON 절의 역할 - 테이블 연결 조건)
- Multiple table JOIN (3 or more) (다중 테이블 JOIN)
- Necessity and applications of JOIN (JOIN의 필요성과 활용)

---

# Multiple Choice Questions (6 Questions)

## Beginner Level (3 Questions) - Basic Concepts

**Question 1** What is the basic characteristic of INNER JOIN? (INNER JOIN의 기본 특징은?)

- ① Only rows matching both tables (양쪽 테이블 모두에 매칭되는 행만 결과)
- ② All rows from left table (왼쪽 테이블의 모든 행 포함)
- ③ All rows from right table (오른쪽 테이블의 모든 행 포함)
- ④ All rows displayed with duplication (모든 행을 중복으로 표시)

---

**Question 2** What is the role of ON clause? (ON 절의 역할은?)

- ① Specify condition to connect tables (테이블을 연결할 조건 지정)
- ② Filter results (same as WHERE) (결과를 필터링 - WHERE와 동일)
- ③ Sort data (데이터를 정렬)
- ④ Limit number of rows (행의 개수를 제한)

---

**Question 3** What is the most important reason for JOIN? (다음 중 JOIN의 가장 중요한 이유는?)

- ① Database operates faster (데이터베이스가 빠르게 작동)
- ② Recombine normalized data to create meaningful information (정규화된 데이터를 다시 조합하여 의미 있는 정보 생성)
- ③ Convert data types (데이터 타입을 변환)
- ④ Enhance security (보안을 강화)

---

## Intermediate Level (2 Questions) - Concept Application

**Question 4** When JOINing 3 tables, what is the correct order? (3개 테이블을 JOIN할 때 올바른 순서는?)

```sql
① SELECT s.name, c.course_name, e.grade
   FROM student s
   INNER JOIN enrollment e ON s.student_id = e.student_id
   INNER JOIN course c ON e.course_id = c.course_id;

② SELECT s.name, c.course_name, e.grade
   FROM student s
   INNER JOIN course c ON s.student_id = c.course_id
   INNER JOIN enrollment e ON e.course_id = c.course_id;
```

- ① Only ① is correct
- ② Only ② is correct
- ③ Both ① and ② are correct
- ④ Both ① and ② are incorrect 

---

**Question 5** What is the difference between ON and WHERE clauses? (ON 절과 WHERE 절의 차이는?)

- ① Functionality is identical (기능이 완전히 같음)
- ② ON at JOIN time, WHERE filters after JOIN (ON은 JOIN 시점, WHERE는 JOIN 이후 필터링)
- ③ ON has better performance (ON은 성능이 더 좋음)
- ④ Only WHERE uses indexes (WHERE만 인덱스를 사용)

---

## Advanced Level (1 Question) - Critical Thinking

**Question 6** Why is JOIN necessary when database is normalized into multiple tables? (데이터베이스를 정규화하여 여러 테이블로 분리했을 때 JOIN이 필요한 이유는?)

- ① Faster speed (더 빠른 속도)
- ② Data duplication removed, so tables must recombine to create meaningful information (데이터 중복을 제거했기 때문에 의미 있는 정보를 만들려면 다시 조합 필요)
- ③ Enhance security (보안 강화)
- ④ Reduce memory usage (메모리 절감)

---

# Short Answer Questions (3 Questions)

## Beginner Level (2 Questions)

**Question 7** Explain the role of ON clause and its difference from WHERE clause. (ON 절의 역할을 설명하고 WHERE 절과의 차이를 설명하시오.)

---

**Question 8** Explain why JOIN should be used in the following situation: "Display students' courses and their instructors together" (다음 상황에 JOIN을 사용해야 하는 이유를 설명하시오. "학생이 수강한 강좌와 그 강좌의 담당 교수를 함께 표시해야 한다")

---

## Advanced Level (1 Question)

**Question 9** Explain considerations when JOINing 3 or more tables, and analyze the impact of NULL values on JOIN results. (3개 이상의 테이블을 JOIN할 때 고려해야 할 사항들을 설명하고, NULL 값이 JOIN 결과에 미치는 영향을 분석하시오.)

---

# Practical Problems (3 Questions)

## Beginner Level (2 Questions)

**Question 10** Execute the following SQL and provide a screenshot. (다음 SQL을 실행하고 결과 스크린샷을 제시하시오.)

```sql
-- Create database (데이터베이스 생성)
CREATE DATABASE ch5_join CHARACTER SET utf8mb4;
USE ch5_join;

-- Create professor table (교수 테이블 생성)
CREATE TABLE professor (
    professor_id INT PRIMARY KEY AUTO_INCREMENT,
    professor_name VARCHAR(30) NOT NULL,
    department VARCHAR(30)
) CHARACTER SET utf8mb4;

-- Create course table (강좌 테이블 생성)
CREATE TABLE course (
    course_id INT PRIMARY KEY AUTO_INCREMENT,
    course_name VARCHAR(30) NOT NULL,
    credits INT,
    professor_id INT,
    FOREIGN KEY (professor_id) REFERENCES professor(professor_id)
) CHARACTER SET utf8mb4;

-- Insert professor data (교수 데이터 입력)
INSERT INTO professor VALUES
(1, 'Alex Park', 'AI Software'),
(2, 'Sarah Lee', 'AI Software'),
(3, 'Michael Choi', 'AI Software');

-- Insert course data (강좌 데이터 입력)
INSERT INTO course VALUES
(1, 'Database', 3, 1),
(2, 'Web Programming', 3, 2),
(3, 'Artificial Intelligence', 3, 1),
(4, 'Cloud Computing', 3, 3);

-- Query all data (모든 데이터 조회)
SELECT * FROM professor;
SELECT * FROM course;
```

Submission: Screenshot showing professor and course table data (제출: professor와 course 테이블 데이터가 모두 보이는 스크린샷)

---

**Question 11** INNER JOIN professor and course tables to perform the following queries. (professor와 course 테이블을 INNER JOIN하여 다음을 조회하시오.)

```sql
-- 1. Query courses and instructors (강좌와 담당 교수 조회)
SELECT c.course_name, p.professor_name
FROM course c
INNER JOIN professor p ON c.professor_id = p.professor_id;

-- 2. Course name, professor name, credits (강좌명, 교수명, 학점)
SELECT c.course_name, p.professor_name, c.credits
FROM course c
INNER JOIN professor p ON c.professor_id = p.professor_id;
```

Submission: Screenshot showing both query results (제출: 2개 쿼리 결과가 모두 보이는 스크린샷)

---

## Intermediate Level (1 Question)

**Question 12** Create student and enrollment tables and perform the following. (student와 enrollment 테이블을 생성하고 다음을 수행하시오.)

```sql
-- Create student table (학생 테이블 생성)
CREATE TABLE student (
    student_id INT PRIMARY KEY AUTO_INCREMENT,
    student_name VARCHAR(30) NOT NULL,
    major VARCHAR(30)
) CHARACTER SET utf8mb4;

-- Create enrollment table (수강 테이블 생성)
CREATE TABLE enrollment (
    enrollment_id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    course_id INT,
    grade VARCHAR(2),
    FOREIGN KEY (student_id) REFERENCES student(student_id),
    FOREIGN KEY (course_id) REFERENCES course(course_id)
) CHARACTER SET utf8mb4;

-- Insert student data (학생 데이터 입력)
INSERT INTO student VALUES
(1, 'Student A', 'AI Software'),
(2, 'Student B', 'AI Software'),
(3, 'Student C', 'Computer Science'),
(4, 'Student D', 'AI Software');

-- Insert enrollment data (수강 데이터 입력)
INSERT INTO enrollment VALUES
(1, 1, 1, 'A'),
(2, 1, 2, 'B'),
(3, 2, 1, 'A'),
(4, 2, 3, 'B'),
(5, 3, 2, 'C'),
(6, 4, 1, 'A');

-- Query students, courses, grades (학생, 강좌, 성적 조회)
SELECT s.student_name, c.course_name, e.grade
FROM student s
INNER JOIN enrollment e ON s.student_id = e.student_id
INNER JOIN course c ON e.course_id = c.course_id;
```

Submission: Screenshot showing 3-table JOIN result (제출: student, enrollment 테이블 생성 후 3개 테이블 JOIN 결과 스크린샷)

---

---

# 📋 Answer Key and Model Answers

## Multiple Choice Answer Key (6 Questions)

| Question | Answer | Explanation                                                                                                                 |
| :------: | :----: | :-------------------------------------------------------------------------------------------------------------------------- |
|    1    |   ①   | INNER JOIN returns only rows matching both tables (양쪽 모두에 매칭되는 행만)                                               |
|    2    |   ①   | ON specifies condition to connect two tables (두 테이블 연결 조건 지정)                                                     |
|    3    |   ②   | Creates meaningful information by recombining normalized data (정규화된 데이터를 조합하여 의미 있는 정보 생성)              |
|    4    |   ①   | Only ① is correct (student_id and course_id connection) (①만 올바름)                                                      |
|    5    |   ②   | ON at JOIN execution, WHERE filters after JOIN (ON은 JOIN 시점, WHERE는 이후 필터링)                                        |
|    6    |   ②   | Duplication removed, so tables must recombine for meaningful information (정규화로 중복 제거했기에 JOIN으로 다시 조합 필요) |

---

## Short Answer Model Answers (3 Questions)

### Question 7: Role of ON vs WHERE

**Model Answer (모범 답안):**

```
ON Clause:
- Role: Specify how to connect two tables
- Timing: At JOIN execution
- Feature: Determines which rows are combined

WHERE Clause:
- Role: Additional filtering after JOIN
- Timing: After JOIN
- Feature: Can exclude rows from the JOIN result

Difference Example:
INNER JOIN ... ON: Determines matched rows
INNER JOIN ... WHERE: Further narrows the matched result
```

---

### Question 8: Why JOIN is Needed

**Model Answer (모범 답안):**

```
Situation: Student, enrollment, course, professor in separate tables

Problem without normalization:
- Same course and professor info repeated per student row
- All rows modified when professor info changes
- Data consistency issues

Solution with JOIN:
SELECT s.student_name, c.course_name, p.professor_name
FROM student s
JOIN enrollment e ON s.student_id = e.student_id
JOIN course c ON e.course_id = c.course_id
JOIN professor p ON c.professor_id = p.professor_id;

Benefits:
- Maintains normalization advantages
- Combine info only when needed
- Create meaningful information in single query
```

---

### Question 9: Multiple Table JOIN and NULL Handling

**Model Answer (모범 답안):**

```
Considerations:

1. Select base table
   - Place most important data in FROM

2. JOIN order
   - Sequential based on relationships

3. NULL handling
   - INNER JOIN: NULL in join condition → no match → row excluded

4. Performance
   - Use indexes on conditions
   - Minimize join conditions

NULL Impact:
SELECT * FROM student s
INNER JOIN enrollment e ON s.student_id = e.student_id
- If enrollment has student_id = NULL, JOIN fails → row excluded
- Only students with matching enrollment records appear
```

---

## Practical Problem Model Answers (3 Questions)

### Question 10: Professor, Course Table Creation

**Completion Criteria (완료 기준):**

✅ ch5_join database created (ch5_join 데이터베이스 생성됨)
✅ professor table: 3 professors (3명 교수)
✅ course table: 4 courses (4개 강좌)
✅ FOREIGN KEY set for relationship (FOREIGN KEY로 관계 설정)

---

### Question 11: INNER JOIN Query

**Completion Criteria (완료 기준):**

✅ Course-professor matching: 4 rows (4개 행)
✅ Credits information included (학점 정보 포함)

**Expected Result (예상 결과):**

```
course_name           | professor_name
Database              | Alex Park
Web Programming       | Sarah Lee
Artificial Intelligence | Alex Park
Cloud Computing       | Michael Choi
```

---

### Question 12: 3-Table JOIN

**Completion Criteria (완료 기준):**

✅ student table created (4 students) (4명)
✅ enrollment table created (6 enrollments) (6개 수강)
✅ 3-table JOIN successful (3개 테이블 JOIN 성공)
✅ student name, course name, grade displayed (학생명, 강좌명, 성적 조회)

**Expected Result (예상 결과):**

```
student_name | course_name            | grade
Student A    | Database               | A
Student A    | Web Programming        | B
Student B    | Database               | A
Student B    | Artificial Intelligence | B
Student C    | Web Programming        | C
Student D    | Database               | A
```

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
