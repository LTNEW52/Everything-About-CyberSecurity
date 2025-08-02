# FIND COLUMN USING SQL INJECTION

WE CAN FIND OUT HOW MANY COLUMN IS BEING EXTRACTED FROM DATABASE USING SEVERAL METHOD. ONE IS: ' order by 1/2/3/etc AND OTHER ONE IS: ' union select null/null,null/etc. IN THIS LAB, WE USED THE SECOND ONE TO FIND HOW MANY COLUMN IS OUT THERE. IF null EXCEED THE EXTRACTED COLUMN, IT SHOWS SERVER ERROR.

<div style="text-align:center">
    <img src="../SQL Injection/image/findCol.png" width=1000>
</div>

---

# FIND COLUMN WITH USEFUL DATA TYPE

WE CAN FIND OUT WHICH COLUMN HAS WHICH DATA TYPE BY INSERTING DATA OF THAT TYPE INSTEAD OF NULL. USUALLY WE WANT TO FIND STRING DATA TYPE, AND TO CHECK IF A COLUMN SUPPORTS STRING, WE CAN USE THIS COMMAND: ' union select null,'a',null --

<div style="text-align:center">
    <img src="../SQL Injection/image/checkingCol.png" width=1000>
</div>

---

# RETRIEVING DATA FROM ANOTHER TABLE

IF WE KNOW WHICH TABLES EXIST IN THE DATABASE, WE CAN USE THE union select TO RETRIVE DATA FROM OUTSIDE TABLES.

<div style="text-align:center">
    <img src="../SQL Injection/image/retrieveData1.png" width=1000>
    <img src="../SQL Injection/image/retrieveData2.png" width=1000>
</div>

---

# CONCATING DATA IN A SINGLE COLUMN

IF ONLY ONE COLUMN CAN SHOW STRING, WE CAN CONCAT INFORMATION IN THAT COLUMN. CONCATING COLUMNS CAN BE DONE BY || || , + + , OR ONLY SPACE!

<div style="text-align:center">
    <img src="../SQL Injection/image/concatCol1.png" width=1000>
    <img src="../SQL Injection/image/concatCol2.png" width=1000>
</div>

---

# EXAMINING THE DATABASE 1

IT IS ACTUALLY THE SAME AS BEFORE, TO SEE DATABASE VERSION, WE CAN USE union select @@version, union select * from v$version or union select version(). THE PROBLEM WAS THAT THIS DATABASE WAS DIFFERENT, SO IT DIDN'T ACKNOWLEDGE -- ! AS IT IS MYSQL, IT TOOK # ! I HAD TO CHECK THE ANSWER FOR THIS.

<div style="text-align:center">
    <img src="../SQL Injection/image/version1.png" width=1000>
    <img src="../SQL Injection/image/version2.png" width=1000>
</div>

---

# EXAMINING THE DATABASE 2

IN SOME DATABASES, WE CAN FIND WHAT TABLES ARE INSIDE DATABASE BY USING information_schema.tables. WE ALSO CAN FIND WHICH COLUMN THE TABLES HAVE BY USING informatation.schema.columns. THIS IS A GOOD WAY TO FIND HIDDEN TABLES OR IN THIS CASE, UNKNOWN USER TABLES WHICH IS HARD TO GUESS.

<div style="text-align:center">
    <img src="../SQL Injection/image/findingTables1.png" width=1000>
    <img src="../SQL Injection/image/findingTables2.png" width=1000>
    <img src="../SQL Injection/image/findingTables3.png" width=1000>
    <img src="../SQL Injection/image/findingTables4.png" width=1000>
</div>

---

# BLIND SQL 

ug8o41fbq03oeub3ki4m | THIS WAS INTERESTING. BLIND SQL MEANS NO VISIBLE ERRORS OR DATA, BUT WE CAN SEE VISIBLE CHANGES, SUCH AS FOR THIS, IF COOKIE IS RIGHT, IT SHOWS WELCOME BACK. WE CAN USE THIS VULNERABILITY TO FIND OUT DATA. WE CANT SEE THE DATA RETRIVED FROM USER. SO WE BRUTEFORCE IT BY CHECKING IT WITH EACH CHARACTER EACH POSITION. THE COMMAND IS:

something' and substring((select password from users where username = 'administrator') , n , 1) = 'a/b/c/etc'

HERE n MEANS POSITION. FOR THIS LAB IT WAS UPTO 20. WE CAN USE BURPSUIT INTRUDER TO SEMI AUTOMATE THE PROCESS!

<div style="text-align:center">
    <img src="../SQL Injection/image/blindSQL1.png" width=1000>
    <img src="../SQL Injection/image/blindSQL2.png" width=1000>
</div>

---

# ERROR BASED SQL INJECTION