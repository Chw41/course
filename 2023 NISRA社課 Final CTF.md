---
title: '2023 NISRA社課 Final CTF'
disqus: hackmd
---

2023 NISRA社課 Final CTF
===

## Table of Contents

[TOC]

# Total
![image](https://hackmd.io/_uploads/rJdKlT3Sp.png)

# Web1

## Web1: 0x0 Welcome Topic 
![image](https://hackmd.io/_uploads/H12XSIoST.png)

https://x10101.github.io/WebI_CTF/0x0_Welcome/
![image](https://hackmd.io/_uploads/S12Vr8sHp.png)


### Web1: 0x0 Welcome Solution
```html=
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome</title>
    <link rel = "stylesheet" href = "main.css">
    <script src="all.js"></script>
</head>
<body>
    <div class = "main">
        <div id = "question">
            <h1>Welcome</h1>
            <p>Can u find the flag?</p>
            <input type="text">
            <input type="submit" onclick = "showAnswer()">
        </div>
        <div id = "answer" style = "visibility: hidden;">
            <p>Not here :(</p>
            <!--NISRA{Y0u_F1Nd_Th3_FL3GGGGG}-->
        </div>
    </div>
</body>
</html>
```
> **Flag: NISRA{Y0u_F1Nd_Th3_FL3GGGGG}**

## Web1: 0x1 Cat Topic 
![image](https://hackmd.io/_uploads/rJWIHY2ra.png)
https://x10101.github.io/WebI_CTF/0x1_Cats/
![image](https://hackmd.io/_uploads/Bk0-IFnB6.png)

### Web1: 0x1 Cat Solution
https://x10101.github.io/WebI_CTF/0x1_Cats/images/pic01.jpg
![image](https://hackmd.io/_uploads/H16mLt3ra.png)

https://x10101.github.io/WebI_CTF/0x1_Cats/images/flag.jpg
![image](https://hackmd.io/_uploads/SyOrIYnST.png)
> **Flag: NISRA{93wr4nq5}**

## Web1: 0x2 Doors Topic 
![image](https://hackmd.io/_uploads/S1qJDKhSp.png)

https://x10101.github.io/WebI_CTF/0x2_Doors/
![image](https://hackmd.io/_uploads/S1gfvF3Sa.png)

### Web1: 0x2 Doors Solution
```html=
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rooms</title>
    <link rel="stylesheet" href = "main.css">
    <script src = "secret.js"></script>
</head>
<body>
    <div id = "title" onclick = "Flag()">
        <h1>Find the flag!</h1>
    </div>

    <div id = "main">
        <!--outside-->
        <div id = "door0" style = "display: block;" onclick = "enterDoor0()">
            <p class = "card">000</p>
            <p>Open</p>
        </div>

        <!--Space 1-->
        <div id = "door101" onclick = "enterDoor101()">
            <p class = "card">101</p>
            <p>Open</p>
        </div>
        <div id = "door102" onclick = "enterDoor102()">
            <p class = "card">102</p>
            <p>Open</p>
        </div>

        <!--Space 2-1-->
        <div id = "door201" onclick = "enterDoor201()">
            <p class = "card">201</p>
            <p>Open</p>
        </div>
        <div id = "door202" onclick = "enterDoor202()">
            <p class = "card">202</p>
            <p>Open</p>
        </div>

        <!--Space 2-2-->
        <div id = "door203" onclick = "enterDoor203()">
            <p class = "card">203</p>
            <p>Open</p>
        </div>
        <div id = "door204" onclick = "enterDoor204()">
            <p class = "card">204</p>
            <p>Open</p>
        </div>

        <!--Space 3-1-->
        <div id = "door304" onclick = "enterDoor304()">
            <p class = "card">304</p>
            <p>Open</p>
        </div>
        <div id = "door305" onclick = "enterDoor305()">
            <p class = "card">305</p>
            <p>Open</p>
        </div>

        <!--Space 3-2-->
        <div id = "door301" onclick = "enterDoor301()">
            <p class = "card">301</p>
            <p>Open</p>
        </div>
        <div id = "door302" onclick = "enterDoor302()">
            <p class = "card">302</p>
            <p>Open</p>
        </div>

        <!--Space 3-3-->
        <div id = "nothing">
            <p>Not Here :(</p>
        </div>
        <div id = exit_332 onclick = "exit_332()">
            Exit
        </div>
        <div id = exit_334 onclick = "exit_334()">
            Exit
        </div>

        <!--Space 4-1-->
        <div id = "door403" onclick = "enterDoor403()">
            <p class = "card">403</p>
            <p>Open</p>
        </div>
        <div id = "door404" onclick = "enterDoor404()">
            <p class = "card">404</p>
            <p>Open</p>
        </div>
    </div>
</body>
</html>
```
●JSFuck:https://jsfuck.com/
secret.js 作JSFuck decode
https://x10101.github.io/WebI_CTF/0x2_Doors/secret.js

secret.js JSFuck Decode
```javascript=
function enterDoor0() {     document.getElementById("door0").style.display = "none";     document.getElementById("door101").style.display = "block";     document.getElementById("door102").style.display = "block"; }  function enterDoor101() {     document.getElementById("door101").style.display = "none";     document.getElementById("door102").style.display = "none";     document.getElementById("door201").style.display = "block";     document.getElementById("door202").style.display = "block"; }  function enterDoor102() {     document.getElementById("door101").style.display = "none";     document.getElementById("door102").style.display = "none";     document.getElementById("door203").style.display = "block";     document.getElementById("door204").style.display = "block"; }  function enterDoor201() {     document.getElementById("door201").style.display = "none";     document.getElementById("door202").style.display = "none";     document.getElementById("nothing").style.display = "block";     document.getElementById("exit_332").style.display = "block"; }  function enterDoor202() {     document.getElementById("door201").style.display = "none";     document.getElementById("door202").style.display = "none";     document.getElementById("door203").style.display = "block";     document.getElementById("door204").style.display = "block"; }  function enterDoor203() {     document.getElementById("door203").style.display = "none";     document.getElementById("door204").style.display = "none";     document.getElementById("door304").style.display = "block";     document.getElementById("door305").style.display = "block"; }  function enterDoor204() {     document.getElementById("door203").style.display = "none";     document.getElementById("door204").style.display = "none";     document.getElementById("door301").style.display = "block";     document.getElementById("door302").style.display = "block"; }  function enterDoor301() {     document.getElementById("door301").style.display = "none";     document.getElementById("door302").style.display = "none";     document.getElementById("door304").style.display = "block";     document.getElementById("door305").style.display = "block"; }  function enterDoor302() {     document.getElementById("door301").style.display = "none";     document.getElementById("door302").style.display = "none";     document.getElementById("door403").style.display = "block";     document.getElementById("door404").style.display = "block"; }  function enterDoor304() {     document.getElementById("door304").style.display = "none";     document.getElementById("door305").style.display = "none";     document.getElementById("door201").style.display = "block";     document.getElementById("door202").style.display = "block"; }  function enterDoor305() {     document.getElementById("door304").style.display = "none";     document.getElementById("door305").style.display = "none";     document.getElementById("door301").style.display = "block";     document.getElementById("door302").style.display = "block"; }  function enterDoor404() {     document.getElementById("door403").style.display = "none";     document.getElementById("door404").style.display = "none";     document.getElementById("nothing").style.display = "block";     document.getElementById("exit_334").style.display = "block"; }  function enterDoor403() {     document.getElementById("door403").style.display = "none";     document.getElementById("door404").style.display = "none";     document.getElementById("door101").style.display = "block";     document.getElementById("door102").style.display = "block"; }  function exit_332() {     document.getElementById("nothing").style.display = "none";     document.getElementById("exit_332").style.display = "none";     document.getElementById("door201").style.display = "block";     document.getElementById("door202").style.display = "block"; }  function exit_334() {     document.getElementById("nothing").style.display = "none";     document.getElementById("exit_334").style.display = "none";     document.getElementById("door403").style.display = "block";     document.getElementById("door404").style.display = "block"; }  function Flag() {     alert("NISRA{H3r3_i5_a_s3cr3t_5pac3}"); }
```
> **Flag: NISRA{H3r3_i5_a_s3cr3t_5pac3}**

# Web

## Web: AdminCookies Topic
![image](https://hackmd.io/_uploads/S1eqdLjHT.png)

http://chall2.nisra.net:41019/
![image](https://hackmd.io/_uploads/By7pOLiST.png)
> Cookie:
Flag=hahahaYouAreNotAdmin
### Web: AdminCookies Solution
Cookie: Flag=admin
![image](https://hackmd.io/_uploads/Hyz-K8iB6.png)

![image](https://hackmd.io/_uploads/BJdBKLir6.png)

> **Flag: NISRA{Ch4n9e_y0U_C00kI3s}**

# Misc

## Misc: Blank Topic
![image](https://hackmd.io/_uploads/HkPkKthBT.png)

### Misc: Blank Solution
> file blank.png

![image](https://hackmd.io/_uploads/HkczOq3ST.png)
> (線上)png convert word

![image](https://hackmd.io/_uploads/S1xMYchBp.png)

> **NISRA{D0CX_fil3_5iGna7URE}**

## Misc: 不要跟我要權限 Topic
![image](https://hackmd.io/_uploads/H1jYXhaST.png)

https://docs.google.com/presentation/d/15JkfSJwMmFsqsyytflViT9Lv3Yh10hByimtR53BJWBI
![image](https://hackmd.io/_uploads/HJiiXnpST.png)

### Misc: 不要跟我要權限 Solution
●WayBackMachine: https://web.archive.org/
![image](https://hackmd.io/_uploads/H1BFV3Tr6.png)

![image](https://hackmd.io/_uploads/B1yoVn6rT.png)

> **NISRA{W3B5ItE_h15TorY}**

## Misc: WORD Topic
![image](https://hackmd.io/_uploads/SJfc5c2Sp.png)

### Misc: WORD Solution
![image](https://hackmd.io/_uploads/Hkf8Fn6ra.png)

![image](https://hackmd.io/_uploads/S1ihO2aBT.png)



## Misc: Binwalk Topic
![image](https://hackmd.io/_uploads/SJfc5c2Sp.png)


### Misc: Binwalk Solution
> binwalk finalfalg.png

![image](https://hackmd.io/_uploads/B1Wn59nSp.png)
> file finalfalg.png

![image](https://hackmd.io/_uploads/B1KA9qhBp.png)
> uzip finalfalg.png

![image](https://hackmd.io/_uploads/BkGls9hS6.png)
> cat hint.txt

![image](https://hackmd.io/_uploads/HJBWi9hrp.png)
image: 600 x 408

> sudo apt install graphicsmagick-imagemagick-compat
> convert finalflag.png -resize 600*408

![image](https://hackmd.io/_uploads/ryYDa5hBp.png)
> binwalk -e --size=600*408 finalflag.png

(都無解)

●010editor全新的十六進制編輯器: https://www.sweetscape.com/010editor/
![image](https://hackmd.io/_uploads/HJUYTnTS6.png)

![image](https://hackmd.io/_uploads/SybwChpB6.png)
(Ref: [Not able to read IHDR chunk of a PNG file](https://stackoverflow.com/questions/54845745/not-able-to-read-ihdr-chunk-of-a-png-file))

![image](https://hackmd.io/_uploads/HkVC0hTra.png)
更改00 00 02 00 00 00 01 98 (Weight & Height)
![image](https://hackmd.io/_uploads/rkTPzapST.png)
> 00 00 02 58 00 00 01 98

![image](https://hackmd.io/_uploads/Bktiz6aBp.png)


> **NISRA{B1nw4LK_3XTR4cTIn9_IMAge5}**

## Misc: RGB?Pixel? Topic
![image](https://hackmd.io/_uploads/S140xihBa.png)

### Misc: RGB?Pixel? Solution
> binwalk finalfalg.png

# OS

## OS: Linux Topic
![image](https://hackmd.io/_uploads/B1SUHcnHT.png)

![image](https://hackmd.io/_uploads/HJycB9nBa.png)

### OS: Linux Solution
> chmod 777 CTF/
> ls

![image](https://hackmd.io/_uploads/Bk33r9hr6.png)
> cat flag.txt
> Permission denied

![image](https://hackmd.io/_uploads/BkGkLqhBT.png)
> ls -al
> chmod 777 flag.txt
> Operation not permitted

![image](https://hackmd.io/_uploads/BkaXLc3Ba.png)
> sudo cat flag.txt

> **Flag: NISRA{Th1s_1s_fiNaL_CTF_flAG}**

# Python

## Python: Python Topic
![image](https://hackmd.io/_uploads/B119i3hHT.png)
main.py
```python=
class Test():
	def __init__(self, email='test@nisra.net'):
		self.info = 'test'
		self.email = email

class Secret():
	flag = open("flag.txt", "r").read().strip()


if __name__ == '__main__':
	email = input('Your email: ')

	if email:
		test = Test(email)
	else:
		test = Test()

	msg = ('this is for {test.info}, please contact ' + email + '.').format(test=test)

	print(msg)
```

### Python: Python Solution

# C magic

## C magic: enter username Topic
![image](https://hackmd.io/_uploads/rJPYgATr6.png)

enterusername.c
```c=
#include <stdio.h>
#include <string.h>
int main()
{
    int pass = 0;
    char pw[5];
    char user[5];

    printf("Enter the username:\n");
    gets(user);

    if (strncmp(user, "NISRA", 5) == 0)
    {
        if (strncmp(pw, "12345", 5) == 0)
        {
            printf("Hello NISRA\n");
            if (pass != 0)
            {
                printf("You are root now.\n");
            }
        }
        else
            printf("You did not enter password or password is wrong .\n");
    }
    else
        printf("You are not user.\n");

    return 0;
}
```

### C magic: enter username Solution
> nc chall2.nisra.net 44006

![image](https://hackmd.io/_uploads/H1Jg-0pBp.png)

![image](https://hackmd.io/_uploads/r1kMbA6Ba.png)    

## C magic: Cmagic_integer_overflow Topic

### C magic: Cmagic_integer_overflow Solution