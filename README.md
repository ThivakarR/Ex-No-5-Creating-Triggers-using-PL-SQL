# Ex. No: 5 Creating Triggers using PL/SQL

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
  empid NUMBER,
  empname VARCHAR2(10),
  dept VARCHAR2(10),
  salary NUMBER
);
```
```sql
CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
```
### Create employee tableCREATE TABLE employed(

![272145143-1ead8347-785b-4ab7-bc46-f1d813fda80a](https://github.com/ThivakarR/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118707074/c4b56b0e-231b-4574-8d33-883e48bbf9fb)

### Create salary_log table
![272145127-1124dd0a-1de3-4857-9a06-ef6d707be40f](https://github.com/ThivakarR/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118707074/de97dd9d-57f1-4ed0-863c-37996c2f1f47)


### PLSQL Trigger code
```sql
->Create the trigger
Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
```
->Update the salary of an employee
```sql
UPDATE employed
SET salary = 60000
WHERE empid = 1;
->Display the employee table
```
```sql
SELECT * FROM employed;


->Display the salary_log table
SELECT * FROM sal_log;
```
### Output:
![272145197-405f3cd9-c8b1-4d52-91a1-89fb52311f84](https://github.com/ThivakarR/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118707074/59bde202-3103-4ab6-acac-440d1b98b2cd)
### Result:
program has been successfully executed
