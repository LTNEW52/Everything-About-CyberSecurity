# PATH TRAVERSAL

IF WEBSITE ARE NOT SECURE ENOUGH, WE CAN FIND INFORMATION BY ALTERING FILE PATH, IN EXAMPLE, IMAGE PATH. IN THIS LAB, IF WE ALTER THE IMAGE PATH FROM SAY filepath = image1 TO filepath = ../../../etc/passwd, IT SHOWS ALL STORED PASSWORD IN passwd!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/pathTraversal.png" width=1000>
</div>

---

# ACCESS CONTROL 1

OPEN ADMIN PANEL CAN SOMETIMES BE FOUND IN robots.txt , OR WE CAN USE BRUTE FORCE TO FIND HIDDEN PATHS. IF NOT PROTECTED, ONCE INSIDE WE CAN HARM THE SYSTEM. ONE EXAMPLE IS THIS LAB!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint1a.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint1b.png" width=1000>
</div>

---

# ACCESS CONTROL 2

SOMETIMES DEVS CAN HIDE URL BY USING RANDOM NAMES. BUT IF THEY USE IT IN CODE, THEN NO MATTER WHAT THEY NAMED IT, WE CAN FIND IT!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint2a.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint2b.png" width=1000>
</div>

---

# ACCESS CONTROL 3

IF ADMIN PANEL IS PROTECTED BY COOKIES, BUT IT ONLY CHECKS IF admin == true OR role == 1 , THEN WE CAN CAPTURE THE TRAFFIC WITH BURPSUITE, ALTER THE REQUEST FROM admin = false TO admin = true AND CAN EASILY GET ACCESS!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint3a.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint3b.png" width=1000>
</div>

---

# ACCESS CONTROL 4

INTERESTING! FIRST RULE OF BREAKING, DONT RUSH! READ, ANALYZE, THEN GO AHEAD. IN THIS LAB WE HAD TO FIND CARLOS API. BUT CARLOS HAD A GUID, WHICH IS A RANDOM UID. BUT HE WRITES BLOG. SO WE CAN INTERCEPT HIS BLOG POST, FIND THE GUID, AND THEN, JUST PASTE IT IN myid! BUT PATIENCE IS THE KEY HERE.

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint4a.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint4b.png" width=1000>
</div>

---

# ACCESS CONTROL 5

THIS WAS EASY. WE ALREADY HAVE OUR OWN ID PASS, AND IT USES DIRECT NAME! ALSO ADMINISTRATOR IS ADMINISTRATOR, NO WONDER IT IS VULNERABLE! SO CHANGE THE ID, NOTE THE PASSWORD AND GO TO ADMIN PANEL!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint5a.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/accesspoint5b.png" width=1000>
</div>

---

# AUTHENTICATION 1

IF NO BRUTE FORCE ATTACK CHECK IS IMPLIMENTED, IT IS EASY TO GET USERNAME AND PASSWORD FROM DOING THAT. IN THIS LAB, WE CAN FIRST SEE WHICH USERNAME IS VALID, THEN USING THAT USERNAME WE CAN BRUTE FORCE PASSWORD, WHICH SAVES A LOT OF TIME!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/userenum1.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/userenum2.png" width=1000>
</div>

---

# AUTHENTICATION 2

WHEN 2FA IS IMPLEMENTED, SOMETIMES IT IS ASKED ON THE NEXT PAGE. SO USER MAY BE IN A LOGGED IN STATE ALREADY, EVEN BEFORE ENTERING 2FA CODE! WE CAN USE THAT AND CHANGE URL TO /home OR IN THIS LAB, /my-account?id=carlos TO BYPASS 2FA COMPLETLY!

<div style="text-align:center">
    <img src="../Server%20Side%20Vulnerbility/image/2fa1.png" width=1000>
    <img src="../Server%20Side%20Vulnerbility/image/2fa2.png" width=1000>
</div>

---

