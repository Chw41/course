---
title: '2023 NISRA社課 C語言'
disqus: hackmd
---

2023 NISRA社課 C語言
===

## Table of Contents

# -----社課提供共筆-----

# C黑魔法

## 判斷奇偶

### Lab 0x0
寫一個判斷奇偶的程式

### 哪一個？
```c=
if(n % 2 == 1)
// 奇數
else
// 偶數
```
```c=
if(n % 2 != 0)
// 奇數
else
// 偶數
```
測試 `-5` 這個測資
- 上面是偶數，下面是奇數！？

### 為甚麼
執行看看下面程式
```c=
#include <stdio.h>

int main() {
    printf("\n");
    printf("-5 %% 2 = %d\n" , -5 % 2);
    printf(" 5 %% -2 = %d\n" , 5 % -2);

    return 0;
}

```

### % 如何定義
a = (a / b) * b + a % b
=> (a % b) = a - (a / b) * b

```
// a=-5, b=2
-5 % 2 = -5 - (-5 / 2) * 2
            = -5 - (-2) * 2
            = -5 - (-4)
            = -5 + 4
            = -1
```

```
// a= 5, b=-2
5 % -2 = 5 - (5 / -2) * -2
            = 5 - (-2) * -2
            = 5 - 4
            = 1
```

## 運算子的優先順序
- 運算子有優先順序
- 遇到同優先級運算子時看Associativity

### 輸出結果是？
```c=
int a = -1, b = 1, c;
c = a+++b;
printf("a, b, c = %d, %d, %d\n", a, b, c);
```

> a, b, c = 0, 1, 0

### 第二個例子
```c=
#include <stdio.h>
int main()
{
    for(int i=1;0<i<10;i++){
    	printf("NISRA");
    }
    return 0;
}

```

> 無窮迴圈

- 第一次迴圈：i=1 → (0<i)=1 → 1<10
- 第二次迴圈：i=2 → (0<i)=1 → 1<10

### 第三個例子
True or False?
```c=
#include <stdio.h>
int main()
{
    int a = 10, b = 20, c = 30;
    if (c > b > a)
        printf("True\n");
    else
        printf("False\n");
}

```
> False!

```
c > b > a
--> (c > b) > a  --> (30>20)>a --> 1 > a
--> 1 > 30 --> 0
```


## for-loop各種寫法

先寫一個 for 印出 `9 8 7 6 5 4 3 2 1 0`

### 其他寫法？
```c=
#include <stdio.h>
int main()
{
    for(int i = 10; 0 <= --i;){
        printf("%d\n",i);
    }
}
```

```c=
#include <stdio.h>
int main()
{
    for(int i = 10;i-->0;){
        printf("%d\n",i);
    }
}
```

```c=
#include <stdio.h>
int main()
{
    for(int i = 10; 0 <= ~~ --i;){
        printf("%d\n",i);
    }
}
```

### 簡單的 Lab
印出下圖
![image](https://hackmd.io/_uploads/rJ4UxIXBT.png)

### 奇奇怪怪寫法
```c=
#include <stdio.h>
int main()
{
    for (int i = 10, j = 0; i > 0 && j < 10; i--, j++){
        printf("%d %d\n",i,j);
    }
}
```

> 珍惜生命，不要亂寫噁心別人
> [name= Du]

## Scope

return 多少？
```c=
int x=0;
int getNum(){
    int x=1214;
    {
    	return x;
    }
}
```

### 變數可視範圍
- 由下而上，由內而外，遇到的第一個
![image](https://hackmd.io/_uploads/rJSfMUXB6.png)

- 如果想要讀取全域變數
    - 使用 extern
    ![image](https://hackmd.io/_uploads/ByDBz87BT.png)
    
### 例子
印出的值是？
```c=
int main(){
	{
    	int x=0;
	}
	printf("%d\n",x);
}
```
- 如果不小心在變數沒有定義的區域使用的話...
    ![pasted-from-clipboard](https://hackmd.io/_uploads/HkM5G8QHp.png)
    
## Random

輸入 key 印出 You got it
```c=
#include <stdio.h>
int main()
{
    unsigned int random, key = 0;
    random = rand();
    printf("Give secret number: ");
    scanf("%d", &key);
    if( (key ^ random) == 0xdeadbeef ){
    printf("You got it!!\n");
    return 0;
    }
    printf("No, keep trying.\n");
    return 0;
}
```
:::warning
不要改動程式碼喔
:::

tips:
A ^ B = C
A = B ^ C

### Random 真的有亂數嗎
多執行幾次看看結果
```c=
int main(){
    for(int i=0;i<10;i++){
        printf("%u\n",rand());
    }
}
```
> 不管執行幾次結果都一樣

- 如果真的想要做到很亂的亂數效果
    - 加上 srand(time(NULL)); 初始化
    ```c=
    #include <stdio.h>
    int main()
    {
        unsigned int random, key = 0;
        srand(time(NULL));
        random = rand();
        printf("Give secret number: ");
        scanf("%d", &key);
        if( (key ^ random) == 0xdeadbeef ){
        printf("You got it!!\n");
        return 0;
        }
        printf("No, keep trying.\n");
    }

    ```
剛剛的 Lab
key ^ random = 0xdeadbeef;
key = random ^ 0xdeadbeef;
```c=
#include <stdio.h>
int main()
{
    unsigned int random, key = 0;
    random = rand();
    printf("key= %d\n",41^ 0xdeadbeef);
    printf("Give secret number: ");
    scanf("%d", &key);
    if( (key ^ random) == 0xdeadbeef ){
    printf("You got it!!\n");
    return 0;
    }
    printf("No, keep trying.\n");
    return 0;
}
```

## 宗教戰爭
哪一個？
```c=
while(1){
/* Do something */
}
for(i = 0 ; i < 10 ; i++){
/* Do something */
}
```

```
while(1)
{
/* Do something */
}
for(i = 0 ; i < 10 ; i++)
{
/* Do something */
}
```
![pasted-from-clipboard](https://hackmd.io/_uploads/BydF98XrT.png)

## C 的安全問題
> ~~寫扣得交作業都來不及了誰還會想到安全問題~~

在不改動程式碼的前提
輸入 input
印出 "Yes you pass it!"
```c=
#include <stdio.h>
#include <string.h>

int main()
{
    char pwd[8] = "NISRA";
    char input[8];
    printf("Give me some input: ");
    scanf("%s", input);
    if (strcmp(pwd, "admin") == 0)
    	printf("Yes you pass it!\n\n");
    else
    	printf("No, keep trying.\n\n");
    return 0;
}
```

下面code有甚麼問題
```c=
#include <stdio.h>
#include <string.h>

int main()
{
    char input[10];
    printf("Give me some input: ");
    scanf("%s", input);

    printf("%s\n", input);

    return 0;
}
```
> input 沒有限制輸入長度

### Buffer Overflow
- 緩衝區溢位
    - 輸入超過 buffer 的資料
- 可能造成
    - 破壞性程式執行
    - 執行期間竄改程式
    - 取得系統控制權


為甚麼是9
```c=
#include <stdio.h>
#include <string.h>

int main()
{
    char input[10];
    printf("Give me some input: ");
    scanf("%9s", input);

    printf("%s\n", input);

    return 0;
}
```
![pasted-from-clipboard](https://hackmd.io/_uploads/SJBLAUXHp.png)

### Memory Layout
![image](https://hackmd.io/_uploads/SJE5A87H6.png)

- 程式碼
    - 程式碼區段(codesection)
    - 又稱為 text section
- 程式全域變數
    - 存放著程式的全域變數
    - 已初始化 / 未初始化
- 動態分配
    - 動態分配的空間
    - C
        - malloc / free
    - C++
         - new / delete
 - 區域變數
 - 系統保留空間

```c=
#include <stdio.h>

int global = 87;  // data
int main()
{
    int a = 10;  // stack
}
```

### Registers of x86
* EIP
    * Instruction Pointer
    * 下一個執行的 instruction 之位址
* ESP
    * Stack Pointer: 儲存 Stack 頭位址
* EBP
    * Base Pointer: 儲存 Stack 基底(base)位址

![image](https://hackmd.io/_uploads/H1OLkDmrT.png)

回頭看前面的 Lab
![image](https://hackmd.io/_uploads/B1vu1vQra.png)
![image](https://hackmd.io/_uploads/SJbK1wQHa.png)
![image](https://hackmd.io/_uploads/B1dY1DXrp.png)
![image](https://hackmd.io/_uploads/Hkkc1wmBT.png)
為甚麼反過來


### Endian
* 位元組存放順序（byte ordering）
* 資料在記憶體中放的順序
* 最常見的有兩種，分別是 Big-Endian 與 Little-Endian
* MSB / LSB
    * most significant bit / least significant bit
    * 最左側 / 最右側的位元組
* Big endian
    * MSB 存在最低的位址
* Little endian
    * LSB 存在最低的位址

![image](https://hackmd.io/_uploads/SJCa1D7Hp.png)

![image](https://hackmd.io/_uploads/Sy9xgvQBa.png)
![image](https://hackmd.io/_uploads/BkWZxP7Hp.png)
![image](https://hackmd.io/_uploads/r1nBzPXST.png)
![image](https://hackmd.io/_uploads/ry9Pfv7HT.png)


###### tags: `ClassNotes` `NISRA` `112` `2023`
