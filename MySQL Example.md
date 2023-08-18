

**1. Creating a Database:**

```sql
CREATE DATABASE School;
```

**2. Switch to the `School` database:**

```sql
USE School;
```

**3. Creating a Table - `Students`:**

```sql
CREATE TABLE Students (
    studentID INT AUTO_INCREMENT PRIMARY KEY,
    firstName VARCHAR(50) NOT NULL,
    lastName VARCHAR(50) NOT NULL,
    age INT,
    gradeLevel VARCHAR(50)
);
```

**4. Inserting data into the `Students` table:**

```sql
INSERT INTO Students (firstName, lastName, age, gradeLevel)
VALUES ('John', 'Doe', 18, 'Senior'),
       ('Jane', 'Smith', 17, 'Junior'),
       ('Tom', 'Brown', 16, 'Sophomore');
```

**5. Selecting data from the `Students` table:**

```sql
SELECT * FROM Students;
```

This will show all students in the table.

**6. Using `WHERE` clause to filter data:**

```sql
SELECT * FROM Students WHERE gradeLevel='Senior';
```

This will only show students who are in the 'Senior' grade level.

**7. Using `WHERE` with multiple conditions:**

```sql
SELECT * FROM Students WHERE age > 16 AND gradeLevel='Senior';
```

This will show students who are older than 16 and are in the 'Senior' grade level.

You can build on these basics by exploring more advanced queries and SQL functionalities such as JOINs, GROUP BY, ORDER BY, etc.