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

# EXAMINING THE DATABASE

