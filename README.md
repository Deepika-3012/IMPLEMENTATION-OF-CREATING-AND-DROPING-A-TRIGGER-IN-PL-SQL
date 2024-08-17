# IMPLEMENTATION-OF-CREATING-AND-DROPING-A-TRIGGER-IN-PL-SQL

AIM:

To create and drop triggers in PL/SQL

PROCEDURE:

TRIGGER :A Trigger is a stored procedure that defines an action that the database automatically take when some database-related event such as Insert, Update or Delete occur.

TYPES OF TRIGGERS:The various types of triggers are as follows,

• Before: It fires the trigger before executing the trigger statement.

• After: It fires the trigger after executing the trigger statement.

• For each row: It specifies that the trigger fires once per row.

• For each statement: This is the default trigger that is invoked. It specifies that the trigger fires once per statement.

VARIABLES USED IN TRIGGERS:

:new

:old

These two variables retain the new and old values of the column updated in the database. The values in these variables can be used in the database triggers for data manipulation

Syntax:

Create or replace trigger <trg_name> Before /After Insert/Update/Delete

[of column_name, column_name....]

on <table_name>

[for each row]

[when condition]

begin

---statement

end;

Create a trigger that insert current user into a username column of an existing table

Procedure for doing the experiment:

1. Create a table student4 with name and username as arguments

2. Create a trigger for each row that insert the current user as user name into a table

3. Execute the trigger by inserting value into the table

 COMMANDS:

SQL> create table itstudent4(name varchar2(15),username varchar2(15));

Table created.

SQL> create or replace trigger student4 before insert on student4 for each row

2 declare

3 name varchar2(20);

4 begin

5 select user into name from dual;

6 :new.username:=name;

7 end;

8 /

Trigger created.

Output:

SQL> insert into student4 values('&name','&username');

Enter value for name: akbar

Enter value for username: ranjani

old 1: insert into student4 values('&name','&username')

new 1: insert into student4 values('akbar','ranjani')

1 row created.

SQL> /

Enter value for name: suji

Enter value for username: priya

old 1: insert into student4 values('&name','&username')

new 1: insert into student4 values('suji','priya')

1 row created.

SQL> select * from itudent4;

NAME USERNAME
--------------- ---------------

akbar SCOTT

suji SCOTT

Develop a query to Drop the Created Trigger

SQL> drop trigger ittrigg;

Trigger dropped.

RESULT:

Thus the creation and dropping of triggers was performed and executed successfully
