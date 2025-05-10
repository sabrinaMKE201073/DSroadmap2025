## 🧠 Introduction to SQL

In SQL, all data is stored in the server's hard disk, where Servers are powerful computers that store information and perform services via requests made over a network.

---

## 1) Components of SQL

- **Database** = in Table form  
- **Fields** = Columns  
- **Records** = Rows

---

## 2) Field Naming in SQL Format

- **lowercase**
- **use underscores**
- **singular**
- Different from the table and other fields

---

## 3) Data Types

In SQL, we refer to the data type by schema,  
Example as follows: 
<p align="center">
  <img src="schema.JPG" alt="Schema Example" width="500">
</p>


## 🖋️ INTRODUCING QUERIES

### SQL Script

<pre>
<code>
SELECT column1, column2
FROM table_name;
</code>
</pre>

- **Wildcard (to select all)**:
  <pre>
  <code>
  SELECT * FROM table_name;
  </code>
  </pre>

---

## 📝 WRITING QUERIES

**1) AS** (Aliasing)  
– make column names easier to read or more meaningful.

<pre>
<code>
SELECT name AS first_name
FROM employees;
</code>
</pre>

**2) DISTINCT** (Unique values) 
– Used to avoid repetitive data
  
<pre>
<code>
SELECT DISTINCT dept_id, year_hired 
FROM employees;
</code>
</pre>

**3) CREATE VIEW**
  – Used to save an SQL query
  - by creating view, it only save it for view purposes only, it didn't store data
  
<pre>
<code>
CREATE VIEW employee_hire_years AS
SELECT id, name, year_hired
FROM employees;
</code>
</pre>

---

## 🍽️ SQL FLAVORS

<p align="center">
  <img src="postgresql_vs_sqlserver.JPG" alt="PostgreSQL vs SQL Server" width="500">
</p>
