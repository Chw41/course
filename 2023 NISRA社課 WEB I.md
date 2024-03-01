---
title: '2023 NISRA社課 WEB I'
disqus: hackmd
---

2023 NISRA社課 WEB I
===

## Table of Contents

# -----社課提供共筆-----

# Web I

## WWW

**W**orld **W**ide **W**eb
* 全球資訊網

## 如何看到網頁

- URL 在哪裡
- HTML 長甚麼樣
- HTTP 如何傳輸

### Web如何運作
![1](https://hackmd.io/_uploads/SkUJ8Cx46.png)


### URL

統一資料定位符

`協定://網域:埠號/檔案路徑?參數#片段ID`
ex. `https://nisra.net:420/tmp/test.php?q=1#1`

### HTTP/HTTPS

HyperText Transfer Protocol
- 傳輸超媒體文件
- 應用層協定
- 明文傳遞訊息
- HTTPS: 加密傳遞訊息

### 常用的資料請求方式: GET & POST

- GET: 參數在請求網址內
    - 格式：網址?參數名稱1=參數內容1&參數名稱2=參數內容2

- POST: 參數在請求封包內
    - 封包攔截可查詢到相關資訊
    - 相較 GET 已經無法直接用URL取得隱私資料


### HTTP狀態碼

- 1xx 訊息提示
- 2xx 請求成功
- 3xx 重新導向
- 4xx 用戶端錯誤
- 5xx 伺服器錯誤



### cookies

- 記錄使用者狀態資料
- 儲存在用戶端
- 用來解決HTTP協定的網頁互動問題

* 記憶體 Cookie
    * 非持久性，瀏覽器關了就沒了
* 硬碟 Cookie
    * 持久性，瀏覽器關掉不會消失

### robots.txt

- 放在網路根目錄 (`/robots.txt`) 下的機器人指令
- 管理機器人活動
- 限制網站爬取
- **非強制**

```
User-agent:
Disallow: *
```

### 前端&後端

![image](https://hackmd.io/_uploads/SJSCLClV6.png)

#### 前端

- 介面
- HTML CSS Javascript

#### 後端

- 資料庫
- PHP Python

## 網頁三兄弟

圖解三兄弟
![image](https://hackmd.io/_uploads/S14MwAxE6.png)
- HTML 定義有哪些元素
- CSS 定義元素長甚麼樣
- JS 定義元素的行為

### 元素 Element

- 空元素
  只有一個標籤
  沒有內容
  具開始與結束的性質
- 塊級元素
  顯示以新的一行開始
- 內聯元素
  顯示時不會換行
  
 ### 結構
 - `<!DOCTYPE html>`：表示本頁面是由 HTML5 編成
- `<html>`：HTML文件會被包含在這個標籤之中
- `<head>`：裡面多為基礎設定，不會顯示在網頁中
- `<body>`：包含所有網頁瀏覽者看得到的內容

### `<head>`常用標籤

- `<title>` 定義文檔標題
- `<base>` 定義連結的默認連結位址
- `<link>` 定義文檔與外部資源的關係
- `<meta>` 描述網頁屬性 e.g.搜索關鍵字、網頁描述
- `<script>` 定義客戶端腳本事件(Javascript)
- `<style>` 定義HTML文檔的樣式文件(CSS)


### `<body>`常用標籤

- 標題: `<h1></h1>...<h6></h6>`
- 段落: `<p></p>`
- 圖片: `<img src="圖片路徑" alt="替代文字" width="圖片寬度" height="圖片高度">`
- 超連結：
    `<a href = "連結位址" target = "開啟方式" title = "提示文字">有超連結功能的文字或圖片</a>`
- 註釋：`<!--註釋內容-->`
- 有序清單:
```xml=
<ol>
  <li>有序清單1</li>
  <li>有序清單2</li>
  <li>有序清單3</li>
</ol>
```
網頁顯示結果:
![有序](https://hackmd.io/_uploads/HJzMyybVa.png)


- 無序清單:
``` xml=
<ul>
  <li>無序清單1</li>
  <li>無序清單2</li>
  <li>無序清單3</li>
</ul>
```
網頁顯示結果:
![無序](https://hackmd.io/_uploads/HyiBJJZ4T.png)


- 表格:
```xml=
<table>
  <th>MON</th>
  <th>TUE</th>
  <th>WED</th>
  <th>THU</th>
  <th>FRI</th>
  <th>SAT</th>
  <th>SUN</th>
  <tr>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
  </tr>
  <tr>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
      <td>14</td>
  </tr>
</table>
```
![pasted-from-clipboard](https://hackmd.io/_uploads/ByrV00lE6.png)
網頁顯示結果:
![表格](https://hackmd.io/_uploads/H1R2kkZNa.png)




### 文本標籤

- `<b>` 文字加粗
- `<em>` 定義重點文字
- `<i>` 斜體
- `<strong>` 定義加重語氣
- `<small>` 定義小號文字
- `<sub>` 定義下標字
- `<sup>` 定義上標字
- `<ins>` 定義插入字(有底線)
- `<del>` 定義刪除字(字有刪除線)

### CSS
-  **C**ascading **S**tyle **S**heets
-  階層樣式表
-  一種風格頁面語言
### 引入方式
- inline style 內聯樣式
```
<h1 style="color: blue;"></h1>
```
- internal style 內部樣式表
```
<head>
    <style>
        /*CSS內容*/
    </style>
<head>
```
- external style 外部樣式表
```
<link rel="stylesheet" type="text/css" href="檔案位置">
```
### 寫法
- 屬性 + 聲明 
### Selector
- id選擇器
```
1.將標有特定id的HTML元素指定特定的樣式
2.寫法為#選擇器名稱，在html中以"id"表示
```
- class選擇器
```
定義一組的元素樣式，可在多個元素中使用
在html以"class"表示，CSS文檔中以"."小數點表示
```
### 常用屬性

- 背景
    1. 背景顏色
       e.g. background-color:black;
    2. 背景圖片
       e.g. `background-image:url("圖片位址");`
- 文本
    1. 顏色
       e.g. `color:white;`
    2. 字體
       e.g.font-family:sans-serif
    3. 字體大小
       e.g. font-size:20px;
    4. 對齊方式
       e.g. text-align:right;

### JavaScript

- 直譯式程式語言
- 可以直接嵌入HTML中
- 讓網頁與使用者互動
- 動態型別
    - Javascript 自己會決定變數的型態

### 寫在哪


- 1.寫在HTML裡
```
<html>
    <head>
        <script>
        //你的JScode
            <script>
        </head>
        <body>
        </body>
    </html>
```
- 2.外部檔案引入
```
<head>
    <script src="./js/XXX.js"></script>
</head>
```

### 運算子

- 四則運算 `+`,`-`,`*`,`/`
- 取餘數 ``%``
- 次方 `**`
- 比較 `>`,`<`,`>=`,`<=`,`==`,`!=`
- 嚴格比較(比較值 + 型態) `===`, `!===`
- 邏輯 `&&`,`||`

* onevent
    * `onclick`:當滑鼠點擊時
    * `onerror`:當出現error時(載入失敗)
    * `onload`:當載入成功時

### DOM

- **D**ocument **O**bject **M**odel
- 一種讓文件以樹狀結構表式的模型
- 瀏覽器會將HTML解析為DOM樣式



## Lab
HTML
```htmlmixed=
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href = "main_0x2.css">
    <script src = "hello_0x2.js"></script>
    <title>101</title>
</head>
<body>
    <div class = "card">
        <h1>101</h1>
        <div style = "height: 150px;">
            <img id = "pic" src="https://i.pinimg.com/originals/99/bb/33/99bb33d0439bc0cf3808fb41b61fdc8a.png">
        </div>
        <p>輔大資工大二</p>
        <h2>Interest</h2>
        <ul>
            <li>畫畫</li>
            <li>看漫畫</li>
            <li>看小說</li>
            <li>手作</li>
        </ul>
        <h2>Who are u?</h2>
        <input id = "Name" type = "text" placeholder = "Name">
        <input type = "submit" value = "Hi!" onclick = "showHello()">
    </div>
    <div id = "hello" style = "visibility: hidden;">
        <p>Hello, <span id = "unknow"></span>.</p>
    </div>
</body>
</html>
```

CSS
```css=
.card {
    background-color: rgb(235, 225, 211);
    height: 500px;
    width: 300px;
    margin: auto;
    position: relative;
    text-align: center;
}

.card ul {
    margin: 0 25%;
}

.card li {
    text-align: left;
}

#pic{
    width: 150px;
    height: 150px;
    border-radius: 100px;
    position: absolute; /*絕對定位*/
    left: 25%;
    animation-name: MovePic; /*動畫名稱*/
    animation-duration: 3s; /*動畫時間*/
    animation-delay: 0s; /*動畫延遲時間*/
    animation-iteration-count: infinite; /*動畫重複次數，infinite 無限重複*/
}

@keyframes MovePic{ /*@keyframe 自訂動畫名稱、屬性變化*/
    from{
        transform:rotate(0deg);
        /*transfom讓元素可以被平移、旋轉、縮放和傾斜*/
        /*rotate() 旋轉*/
        /*deg 旋轉角度*/
    }
    to{
        transform:rotate(360deg);
    }
}
```

JS
```javascript=
function showHello () {
    var name = document.getElementById ("Name");
    document.getElementById("hello").style.visibility = "visible";
    document.getElementById("unknow").innerText = name.value;
}
```

###### tags: `ClassNotes` `NISRA` `112` `2023`
