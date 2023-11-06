# Ex. No: 5 Creating Triggers using PL/SQL

## DATE:

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
```sql
SQL> CREATE TABLE emp(empid number, empname varchar(10), dept varchar(10),salary number);

SQL> CREATE TABLE salary_log (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER, empname VARCHAR2(10), old_salary NUMBER, new_salary NUMBER, update_date DATE);

INSERT INTO emp(empid, empname, dept, salary)
values(1,'ajay','IT',100000);
INSERT INTO emp(empid, empname, dept, salary)
values(1,'aswin','HR',600000);
I![ex 5 1](https://github.com/AJAYASWIN-M/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118679692/d212b0a0-740e-4d2c-9119-136454834228)
NSERT INTO emp(empid, empname, dept, salary)
values(1,'ajayaswin','seo',500000);
```
### Create employee table
![ex 5 1](https://github.com/AJAYASWIN-M/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118679692/7fcadf5c-654f-4961-8b68-f07767949fb6)

### Create salary_log table
![ex 5 2](https://github.com/AJAYASWIN-M/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118679692/e6d9c43b-5f24-439a-bed3-40bf8c5713e8)

### PLSQL Trigger code
```sql

CREATE OR REPLACE TRIGGER log_salary__update
BEFORE UPDATE ON emp
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/

SET salary = 50000
WHERE empid = 1;


 SELECT * FROM emp;

SELECT * FROM salary_log;
```

### Output:
![ex 4 dbms](https://github.com/AJAYASWIN-M/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118679692/eca999ae-65eb-4b2c-af80-d5ac6a05eaef)
![ex 5 l](https://github.com/AJAYASWIN-M/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118679692/69ef49ba-9c14-4f18-9968-6cbf007a63d0)


### Result:
The program has been implemented successfully.
