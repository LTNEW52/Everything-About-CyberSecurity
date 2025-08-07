# ABSOLUTE PATH TRAVERSAL

IF RELATIVE PATH TRAVERSAL IS BLOCKED, EX: ../../../etc/passwd, WE CAN USE ABSOLUTE PATH TRAVERSAL, AKA DIRECT FILE PATH. SUCH AS: /etc/passwd

<div style="text-align:center">
    <img src="../Path Traversal/image/absPath1.png" width=1000>
    <img src="../Path Traversal/image/absPath2.png" width=1000>
</div>

---

#  NESTED PATH TRAVERSAL

IF THERE IS SOME KIND OF SANITIZATION, SUCH AS IT STRIPS ../ , WE CAN USE ....// . WHICH READ AS ../ , AND CAN BYPASS WEAK SANITIZATION.

<div style="text-align:center">
    <img src="../Path Traversal/image/nestedPath1.png" width=1000>
    <img src="../Path Traversal/image/nestedPath2.png" width=1000>
</div>

---

# ENCODED PATH TRAVERSAL

IF APPLICATION ALWAYS STRIP OR SANITIZE PATH TRAVERSAL, WE CAN USE URL ENCODING OR VARIOUS ENCODING TO BYPASS THAT. WE CAN EVEN MULTIPLY THE ENCODING UNTILL IT WORKS!

<div style="text-align:center">
    <img src="../Path Traversal/image/encodedPath1.png" width=1000>
    <img src="../Path Traversal/image/encodedPath2.png" width=1000>
</div>

---

# REQUIRED FILE PATH TRAVERSAL

SOMETIME APPLICATION NEED SPECIFIC PATH TO START WITH. SO, WE CAN START WITH THE PATH, THEN GO FORWARD OR BACK TO RETRIEVE THE INFORMATION WE WANT!

<div style="text-align:center">
    <img src="../Path Traversal/image/reqPath1.png" width=1000>
    <img src="../Path Traversal/image/reqPath2.png" width=1000>
</div>

---

# REQUIRED EXTENSION PATH TRAVERSAL

APPLICATION SOMETIMES MAY NEED SPECIFIC EXTENSION, SUCH AS ENDING WITH .png OR .jpg . WE CAN USE %00 OR AKA NULL BYTE TO BYPASS THAT, NULL BYTE REMOVES .jpg WHEN PROCESSING. BUT IT IS NOT SUPPORTED ANYMORE IN MODERN PHP OR SIMILAR LANGUAGE.

<div style="text-align:center">
    <img src="../Path Traversal/image/extenPath1.png" width=1000>
    <img src="../Path Traversal/image/extenPath2.png" width=1000>
</div>

---