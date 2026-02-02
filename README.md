Task 11: Indexing and Query Performance Optimization

## 📌 Project Overview
This task demonstrates how **SQL indexing** improves query performance.  
It shows how to measure execution plans using `EXPLAIN` and compare query behavior before and after indexing.

---

## 🛠 Tools & Technologies
- **Primary:** MySQL Workbench  
- **Alternatives:** PostgreSQL, BigQuery Sandbox, SQLite  

---

## 📂 Repository Structure
- `task11_indexing_performance.sql` → SQL script for index creation and analysis  
- `README.md` → Project documentation (this file)

---

## 🎯 Learning Objectives
- Identify slow queries
- Measure performance using `EXPLAIN`
- Create indexes on search & join columns
- Compare execution plans before/after indexing
- Understand clustered vs non-clustered indexes
- Learn when indexes hurt performance
- Apply best indexing practices

---

## 🗄 Tables Used
- **employees**
- **departments**

---

## 🧪 SQL Code Examples

### 1. Query Without Index
```sql
SELECT * 
FROM employees
WHERE emp_name = 'Ankit Sharma';
2. Analyze Query Plan
EXPLAIN 
SELECT * 
FROM employees
WHERE emp_name = 'Ankit Sharma';
3. Create Index
CREATE INDEX idx_emp_name ON employees(emp_name);
4. Re-Analyze After Index
EXPLAIN 
SELECT * 
FROM employees
WHERE emp_name = 'Ankit Sharma';
5. Join Optimization
CREATE INDEX idx_department_id ON employees(department_id);

EXPLAIN
SELECT e.emp_name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
6. Range Search Optimization
CREATE INDEX idx_salary ON employees(salary);

EXPLAIN
SELECT * 
FROM employees
WHERE salary > 50000;
🔍 Clustered vs Non-Clustered Index
Type	Description
Clustered	Physical order of table data (Primary Key)
Non-Clustered	Separate structure referencing data
⚠️ When Indexes Hurt Performance
Too many indexes slow down INSERT, UPDATE, DELETE

Indexing small tables gives little benefit

Indexing low-cardinality columns is ineffective

🏆 Best Indexing Practices
Index columns used in WHERE, JOIN, ORDER BY

Avoid indexing frequently updated columns

Use composite indexes for multi-column searches

Periodically analyze and drop unused indexes

▶ How to Run
Open MySQL Workbench

Select intern_training_db

Open task11_indexing_performance.sql

Run queries step-by-step

Compare EXPLAIN output

✅ Final Outcome
By completing this task, the intern:

Understands SQL performance tuning

Can analyze execution plans

Applies indexes strategically

Is ready for production database optimization
