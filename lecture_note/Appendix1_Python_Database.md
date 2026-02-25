# Appendix 1: Learning Database with Python

---

## 📚 Overview

In this appendix, you will learn how to directly handle databases with Python. Using SQLite database, let's create a simple **Todo Manager** application.

이 부록에서는 파이썬으로 데이터베이스를 직접 다루는 방법을 배웁니다. SQLite 데이터베이스를 사용하여 간단한 할일 관리(Todo Manager) 애플리케이션을 만들어봅시다.

### Learning Goals (학습 목표)

- Connect to SQLite in Python (파이썬에서 SQLite 연결)
- Execute CREATE, INSERT, SELECT, UPDATE, DELETE (CREATE, INSERT, SELECT, UPDATE, DELETE 실행)
- Manage database transactions (데이터베이스 트랜잭션 관리)
- Gain practical application development experience (실제 애플리케이션 개발 경험)

---

## 📖 Part 1: Python and SQLite Basics

### 1.1 What is SQLite? (SQLite란?)

SQLite is a light and simple database.

SQLite는 가볍고 간단한 데이터베이스입니다.

- File-based (no server required) (파일 기반 서버 불필요)
- Built-in to Python (sqlite3 module) (파이썬에 기본 내장 sqlite3 모듈)
- Optimal for initial learning (초기 학습에 최적)

### 1.2 Connecting to SQLite (SQLite 연결하기)

```python
import sqlite3

# Create/connect database file (데이터베이스 파일 생성/연결)
conn = sqlite3.connect('todo.db')

# Create cursor to execute SQL (커서 생성 SQL 실행)
cursor = conn.cursor()

# Close database (데이터베이스 종료)
conn.close()
```

### 1.3 Create Table (테이블 생성)

```python
import sqlite3

conn = sqlite3.connect('todo.db')
cursor = conn.cursor()

# Create table (테이블 생성)
sql = '''
CREATE TABLE IF NOT EXISTS todos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    description TEXT,
    status TEXT DEFAULT 'Not Completed',
    created_date DATE
)
'''

cursor.execute(sql)
conn.commit()  # Save changes (변경사항 저장)
conn.close()
```

---

## 💻 Part 2: Todo Manager Application

### 2.1 Complete Code (완전한 코드)

```python
import sqlite3
from datetime import datetime

class TodoManager:
    def __init__(self, db_name='todo.db'):
        self.conn = sqlite3.connect(db_name)
        self.cursor = self.conn.cursor()
        self.create_table()
  
    def create_table(self):
        '''Create table (테이블 생성)'''
        sql = '''
        CREATE TABLE IF NOT EXISTS todos (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            title TEXT NOT NULL,
            description TEXT,
            status TEXT DEFAULT 'Not Completed',
            created_date TEXT
        )
        '''
        self.cursor.execute(sql)
        self.conn.commit()
  
    def add_todo(self, title, description=''):
        '''Add todo (할일 추가)'''
        sql = '''
        INSERT INTO todos (title, description, created_date)
        VALUES (?, ?, ?)
        '''
        self.cursor.execute(sql, (title, description, datetime.now().date()))
        self.conn.commit()
        print(f"✅ Todo '{title}' has been added.")
  
    def view_todos(self, status='All'):
        '''View todos (할일 조회)'''
        if status == 'All':
            sql = 'SELECT * FROM todos'
        else:
            sql = 'SELECT * FROM todos WHERE status = ?'
            return self.cursor.execute(sql, (status,)).fetchall()
    
        return self.cursor.execute(sql).fetchall()
  
    def update_status(self, todo_id, new_status):
        '''Change todo status (할일 상태 변경)'''
        sql = 'UPDATE todos SET status = ? WHERE id = ?'
        self.cursor.execute(sql, (new_status, todo_id))
        self.conn.commit()
        print(f"✅ Todo #{todo_id} has been changed to '{new_status}'.")
  
    def delete_todo(self, todo_id):
        '''Delete todo (할일 삭제)'''
        sql = 'DELETE FROM todos WHERE id = ?'
        self.cursor.execute(sql, (todo_id,))
        self.conn.commit()
        print(f"✅ Todo #{todo_id} has been deleted.")
  
    def close(self):
        '''Close database (데이터베이스 종료)'''
        self.conn.close()

# Usage example (사용 예제)
if __name__ == '__main__':
    manager = TodoManager()
  
    # 1. Add todos (할일 추가)
    manager.add_todo('Study Python', 'Complete database chapter')
    manager.add_todo('Complete Project', 'Finish Todo Manager')
    manager.add_todo('Exercise', 'Go to gym')
  
    # 2. View all todos (모든 할일 조회)
    print("\n[All Todos]")
    todos = manager.view_todos()
    for todo in todos:
        print(f"{todo[0]}. {todo[1]} - {todo[3]}")
  
    # 3. Change todo status (할일 상태 변경)
    manager.update_status(1, 'Completed')
  
    # 4. Delete todo (할일 삭제)
    manager.delete_todo(3)
  
    # 5. View only completed todos (완료된 할일만 조회)
    print("\n[Completed Todos]")
    completed = manager.view_todos('Completed')
    for todo in completed:
        print(f"✓ {todo[1]}")
  
    manager.close()
```

### 2.2 Execution Result (실행 결과)

```
✅ Todo 'Study Python' has been added.
✅ Todo 'Complete Project' has been added.
✅ Todo 'Exercise' has been added.

[All Todos]
1. Study Python - Not Completed
2. Complete Project - Not Completed
3. Exercise - Not Completed

✅ Todo #1 has been changed to 'Completed'.
✅ Todo #3 has been deleted.

[Completed Todos]
✓ Study Python
```

---

## 📝 Part 3: Basic SQL Commands (Python Version)

### 3.1 CREATE (생성)

```python
# Create table (테이블 생성)
sql = '''
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    age INTEGER,
    email TEXT UNIQUE
)
'''
cursor.execute(sql)
```

### 3.2 INSERT (삽입)

```python
# Insert one row (1개 행 삽입)
sql = 'INSERT INTO users (name, age, email) VALUES (?, ?, ?)'
cursor.execute(sql, ('Alex Johnson', 25, 'alex@email.com'))

# Insert multiple rows (여러 행 삽입)
data = [
    ('Sarah Williams', 23, 'sarah@email.com'),
    ('David Brown', 26, 'david@email.com')
]
cursor.executemany(sql, data)

conn.commit()  # Save (저장)
```

### 3.3 SELECT (조회)

```python
# View all rows (모든 행 조회)
sql = 'SELECT * FROM users'
cursor.execute(sql)
results = cursor.fetchall()

# Conditional view (조건부 조회)
sql = 'SELECT * FROM users WHERE age > ?'
cursor.execute(sql, (25,))
results = cursor.fetchall()

# View only first row (첫 번째 행만 조회)
cursor.execute(sql)
first = cursor.fetchone()
```

### 3.4 UPDATE (수정)

```python
# Modify age of specific user (특정 사용자 나이 수정)
sql = 'UPDATE users SET age = ? WHERE name = ?'
cursor.execute(sql, (26, 'Alex Johnson'))
conn.commit()

print(f"Modified rows: {cursor.rowcount}")
```

### 3.5 DELETE (삭제)

```python
# Delete specific user (특정 사용자 삭제)
sql = 'DELETE FROM users WHERE age < ?'
cursor.execute(sql, (20,))
conn.commit()

print(f"Deleted rows: {cursor.rowcount}")
```

---

## 🎓 Part 4: Advanced Features

### 4.1 Transaction Processing (트랜잭션 처리)

```python
try:
    cursor.execute('INSERT INTO users VALUES (?, ?, ?)', ...)
    cursor.execute('UPDATE accounts SET balance = ? WHERE id = ?', ...)
    conn.commit()  # Save all if success (모두 성공 시 저장)
    print("Transaction succeeded")
except Exception as e:
    conn.rollback()  # Cancel on error (오류 시 취소)
    print(f"Error occurred: {e}")
```

### 4.2 Data Validation (데이터 검증)

```python
def add_user(name, age, email):
    # Input validation (입력 검증)
    if not name or len(name) < 2:
        print("❌ Name must be 2 or more characters.")
        return False
  
    if age < 0 or age > 150:
        print("❌ Age must be between 0 and 150.")
        return False
  
    if '@' not in email:
        print("❌ Please enter valid email.")
        return False
  
    # Save to database (데이터베이스 저장)
    sql = 'INSERT INTO users (name, age, email) VALUES (?, ?, ?)'
    try:
        cursor.execute(sql, (name, age, email))
        conn.commit()
        print(f"✅ {name} has been added.")
        return True
    except sqlite3.IntegrityError:
        print(f"❌ '{email}' is already registered.")
        return False
```

### 4.3 Join Query (조인 쿼리)

```python
# Students table (학생 테이블)
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT,
    grade INTEGER
);

# Grades table (성적 테이블)
CREATE TABLE grades (
    student_id INTEGER,
    subject TEXT,
    score INTEGER,
    FOREIGN KEY (student_id) REFERENCES students(id)
);

# Join query (조인 조회)
sql = '''
SELECT s.name, g.subject, g.score
FROM students s
JOIN grades g ON s.id = g.student_id
WHERE s.grade = 1
'''
cursor.execute(sql)
results = cursor.fetchall()

for name, subject, score in results:
    print(f"{name}: {subject} {score} points")
```

---

## 💡 Part 5: Practice Examples

### 5.1 Student Grade Management System (학생 성적 관리 시스템)

```python
class StudentGradeManager:
    def __init__(self):
        self.conn = sqlite3.connect('grades.db')
        self.cursor = self.conn.cursor()
        self.setup()
  
    def setup(self):
        '''Create tables (테이블 생성)'''
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS students (
                id INTEGER PRIMARY KEY,
                name TEXT NOT NULL UNIQUE
            )
        ''')
    
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS grades (
                id INTEGER PRIMARY KEY,
                student_id INTEGER,
                subject TEXT,
                score INTEGER,
                FOREIGN KEY (student_id) REFERENCES students(id)
            )
        ''')
        self.conn.commit()
  
    def add_student(self, name):
        '''Add student (학생 추가)'''
        try:
            self.cursor.execute('INSERT INTO students (name) VALUES (?)', (name,))
            self.conn.commit()
            print(f"✅ {name} has been added.")
        except sqlite3.IntegrityError:
            print(f"❌ {name} already exists.")
  
    def add_grade(self, student_name, subject, score):
        '''Add grade (성적 추가)'''
        # Find student ID (학생 ID 찾기)
        self.cursor.execute('SELECT id FROM students WHERE name = ?', (student_name,))
        result = self.cursor.fetchone()
    
        if not result:
            print(f"❌ Cannot find {student_name}.")
            return
    
        student_id = result[0]
        self.cursor.execute(
            'INSERT INTO grades (student_id, subject, score) VALUES (?, ?, ?)',
            (student_id, subject, score)
        )
        self.conn.commit()
        print(f"✅ {student_name}'s {subject} grade ({score} points) has been added.")
  
    def get_average(self, student_name):
        '''Get average grade (평균 성적 조회)'''
        sql = '''
        SELECT AVG(g.score)
        FROM students s
        JOIN grades g ON s.id = g.student_id
        WHERE s.name = ?
        '''
        self.cursor.execute(sql, (student_name,))
        result = self.cursor.fetchone()
        return result[0] if result[0] else 0
  
    def print_report(self):
        '''Print grade report (성적 보고서 출력)'''
        sql = '''
        SELECT s.name, g.subject, g.score
        FROM students s
        JOIN grades g ON s.id = g.student_id
        ORDER BY s.name, g.subject
        '''
        self.cursor.execute(sql)
    
        print("\n📊 Grade Report")
        print("-" * 40)
    
        current_student = None
        for name, subject, score in self.cursor.fetchall():
            if name != current_student:
                if current_student:
                    avg = self.get_average(current_student)
                    print(f"Average: {avg:.1f}\n")
                print(f"\n{name}:")
                current_student = name
        
            print(f"  {subject}: {score} points")

# Usage (사용)
manager = StudentGradeManager()
manager.add_student('Alex Johnson')
manager.add_student('Sarah Williams')
manager.add_grade('Alex Johnson', 'Math', 95)
manager.add_grade('Alex Johnson', 'English', 87)
manager.add_grade('Sarah Williams', 'Math', 92)
manager.add_grade('Sarah Williams', 'English', 90)

manager.print_report()
```

---

## 🔍 Part 6: Common Errors and Solutions

### 6.1 Error Handling (오류 처리)

```python
try:
    cursor.execute('SELECT * FROM nonexistent_table')
except sqlite3.OperationalError:
    print("❌ Table does not exist.")

try:
    cursor.execute('INSERT INTO users VALUES (?, ?, ?)', ('Alex Johnson', 25))
    # Need 3 values but only 2 provided (값이 2개인데 3개 필요)
except sqlite3.ProgrammingError:
    print("❌ SQL syntax is incorrect.")
```

### 6.2 Precautions (주의사항)

```python
# ❌ SQL Injection risk (do not use) (SQL 인젝션 위험 사용 금지)
name = "'; DROP TABLE users; --"
sql = f"SELECT * FROM users WHERE name = '{name}'"

# ✅ Safe method (use) (안전한 방법 사용)
sql = "SELECT * FROM users WHERE name = ?"
cursor.execute(sql, (name,))
```

---

## 📚 Part 7: Key Functions Summary

|         Function         | Description                                 |
| :----------------------: | :------------------------------------------ |
|  `sqlite3.connect()`  | Connect database (데이터베이스 연결)        |
|   `cursor.execute()`   | Execute one SQL (SQL 한 개 실행)            |
| `cursor.executemany()` | Execute multiple SQL (SQL 여러 개 실행)     |
|  `cursor.fetchone()`  | Return first row (첫 번째 행 반환)          |
|  `cursor.fetchall()`  | Return all rows (모든 행 반환)              |
|    `conn.commit()`    | Save changes (변경사항 저장)                |
|   `conn.rollback()`   | Cancel changes (변경사항 취소)              |
|     `conn.close()`     | Close connection (연결 종료)                |
|   `cursor.rowcount`   | Number of affected rows (영향을 받은 행 수) |

---

## 🎯 Practice Problems

### 1. Implement Basic CRUD (기본 CRUD 구현)

Create a contact book application.

전화번호부 애플리케이션을 만드시오.

- Add contact (name, phone number) (연락처 추가 이름, 전화번호)
- View contact (연락처 조회)
- Update contact (연락처 수정)
- Delete contact (연락처 삭제)

### 2. Data Analysis (데이터 분석)

From student grade data:

학생 성적 데이터로부터:

- Average score by subject (과목별 평균 점수)
- Highest and lowest scores (최고 점수와 최저 점수)
- Students with 90 or more points (90점 이상 학생 명단)

### 3. Advanced Features (고급 기능)

- Add search functionality (검색 기능 추가)
- Add sorting features (sort by name, score) (정렬 기능 이름순, 점수순)
- Add data backup functionality (데이터 백업 기능)

---

Thank you for your attention.   
Cho Jeonghyun ([peterchokr@gmail.com](mailto:peterchokr@gmail.com)). Yeungnam University College

"Produced in collaboration with Claude and Gemini."
