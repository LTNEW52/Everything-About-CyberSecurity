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

# ERROR BASED SQL INJECTION 1

tuh5k79c29rlags5xuut | THIS WAS TOUGH. SOME DATABASE DOESNT GIVE BACK INFORMATION, NOT EVEN CHANGES USING BLIND SQL. BUT CAN GIVE INFORMATION IF FACED WITH ERROR. THIS IS CALLED BLIND SQL WITH CONDITIONAL ERROR. MANY DATABASE HAVE MANY WAY TO WRITE CONDITIONAL SQL, WE CAN SEE IT IN SQL INJECTION CHEAT SHEET. THIS LAB WAS FOR ORACLE DATABASE, SO WE USED ORACLE CONDITION. THE PROBLEM WAS, IT SHOULD BE from TABLE_NAME where ... WHICH I HAD TO FIGURE IT OUT.

<div style="text-align:center">
    <img src="../SQL Injection/image/blindWithError1.png" width=1000>
    <img src="../SQL Injection/image/blindWithError2.png" width=1000>
</div>

---

# ERROR BASED SQL INJECTION 2

THIS WAS VERY TOUGH. I HAD TO SEE THE ANSWER. THE PROCESS IS LIKE THIS:
1. WHEN CAST(1 as int), WE CAN SEE THAT IT NEEDS BOOLEAN. SO, WE USE 1=cast(SOMETHING). WE CAN SEE IF ANY USERNAME CAN BE LEAKED BY USING THIS COMMAND.
    and 1=(cast(select username from users) as int)
2. WE CAN NOW SEE THAT IT RETRIEVE MORE THAN 1 ROW. SO WE CAN USE THE limit 1 TO LIMIT IT TO FIRST ONE.
3. NOW WE CAN SEE THE FIRST USER IS ADMINISTRATOR. SO ITS EASY NOW, WE CHANGE USERNAME TO PASSWORD.

<div style="text-align:center">
    <img src="../SQL Injection/image/errorSQL1.png" width=1000>
    <img src="../SQL Injection/image/errorSQL2.png" width=1000>
    <img src="../SQL Injection/image/errorSQL3.png" width=1000>
    <img src="../SQL Injection/image/errorSQL4.png" width=1000>
    <img src="../SQL Injection/image/errorSQL5.png" width=1000>
    <img src="../SQL Injection/image/errorSQL6.png" width=1000>
    <img src="../SQL Injection/image/errorSQL7.png" width=1000>
</div>

---

# EXPLOITATION BLIND SQL WITH TIME TRIGGER 

44gb04d00idrqdb5jlmv, THIS IS THE MOST HARDEST AND MOST PAINFUL ONE. DIDN'T FIGURE OUT WHAT TO DO, ALSO IT WAS NOT POSSIBLE WITH BURPSUITE COMMUNITY, NEEDED BURPSUITE PROFESSIONAL! WELL, THIS IS HOW IT GOES,
1. FIRST WE HAVE TO FIGURE OUT WHICH DATABASE IT IS, THERE ARE SOME GREAT SQL CHEAT SHEET OUT THERE WHICH WE CAN USE.
2. FOR TIME DELAY, IT IS BLIND SQL, WHERE DATABASE DOESN'T GIVE BACK ANYTHING, NO ERROR, NO SUCCESS. SO WE USE TIME DELAY TO CONFIRM SOMETHING.
3. THIS WAS POSTGRES SQL AND WE USED THE TIME DELAY TO FIGURE OUT THE PASSWORD.

<div style="text-align:center">
    <img src="../SQL Injection/image/timeDelay1.png" width=1000>
    <img src="../SQL Injection/image/timeDelay2.png" width=1000>
</div>

---

# BLIND SQL INJECTION WITH OUT OF BAND 1

SO BEFORE WE USED THE THEORY THAT SQL IS TRIGGERED STEP BY STEP AND APPLICATION IS WAITING AT THAT TIME. BUT IF IT IS ASYNCHRONUS, THEN IT WONT WORK. SO WE CAN USE OUT OF BAND TECHNIQUE, SUCH AS DNS LOOKUP WITH BURPSUITE COLLBARATOR. WE HAVE TO OPEN THE COLLABARATOR, COPY THE DOMAIN AND PASTE IT IN SUBDMOMAIN PART, USEFULL ONES ARE ALREADY GIVEN IN SQL CHEAT SHEET.

<div style="text-align:center">
    <img src="../SQL Injection/image/outOfBand1.png" width=1000>
    <img src="../SQL Injection/image/outOfBand2.png" width=1000>
</div>

---

# BLIND SQL INJECTION WITH OUT OF BAND 2

pnbqjejmeu7ghsspft54, IF WE CAN ENSURE THAT THERE IS OUT OF BAND BLIND SQL OPTION, WE CAN USE THAT TO RETRIEVE INFORMATION. WE CAN EXTRACT INFORMATION, APPEND IT TO DNS LOOKUP, AND CAN SEE THE INFORMATION IN BURP COLLABARATOR.

<div style="text-align:center">
    <img src="../SQL Injection/image/outOfBand3.png" width=1000>
    <img src="../SQL Injection/image/outOfBand4.png" width=1000>
    <img src="../SQL Injection/image/outOfBand5.png" width=1000>
</div>

---

# SQL INJECTION WITH FILTER BYPASS

SOMETIMES WAF CAN BLOCK SQL ATTACK, WE CAN ENCODE OUR ATTACK TO BYPASS IT. ONE WAY IS USING HACKVERTOR FROM BURP SUITE. IT CAN ENCODE SQL INJECTION IN VARIOUS WAYS.

<div style="text-align:center">
    <img src="../SQL Injection/image/xmlSql1.png" width=1000>
    <img src="../SQL Injection/image/xmlSql2.png" width=1000>
    <img src="../SQL Injection/image/xmlSql3.png" width=1000>
    <img src="../SQL Injection/image/xmlSql4.png" width=1000>
    <img src="../SQL Injection/image/xmlSql5.png" width=1000>
    <img src="../SQL Injection/image/xmlSql6.png" width=1000>
</div>

---