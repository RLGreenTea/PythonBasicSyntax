# <center>Python Basic Syntax</center>

## 目錄
* <0> 名詞解釋
* <1> 運算子(Web)
* <2> 資料型態 & 轉換
* <3> 輸入 & 輸出
* <4> 字串
* <5> 串列
* <> 迴圈
* <> 
---

## <0> 名詞解釋

```py
a = 1
```

`a` 為 **變數 (variable)**

`=` 為 **指派運算子 (assign operator)**

`1` 為 **值 (value)**

把 `1` 指派給 `a` 這個動作稱為 **賦值 (assign)**

我們剛剛 **宣告 (declare)** 了一個變數

---

## <1> 運算子
<http://kaiching.org/pydoing/py/python-operator.html#5>

---

## <2> 資料型態 & 轉換

### 數值型態
* 整數 (integer) &rarr; `1`
    
* 浮點數 (floating-point) &rarr; `0.5`

    * 在Python和其他大部分語言中 , `0.1 + 0.2` 不等於 `0.3` , 這是因為二進位制的關係

* 布林值 (boolean) &rarr; `True` | `False`
  
    * 有 `True`(真) 和 `False`(假) 兩種

        其中 `True` 為 **除了0之外的所有數** , `False` 為 **0**

### 字串型態
* 字串 (string) &rarr; `'apple'`

    * 字串用 `'` (單引號) 或 `"` (雙引號) 包起來

    * 多行字串用 `'''` 或 `"""` (三引號) 包起來

        ```py
        text = '''
        這是一個多行字串
        '''
        ```

### 容器型態
* 串列 (list) &rarr; `['banana', 5]`

* 元組 (tuple) &rarr; `(1, 2)`

* 字典 (dictionary) &rarr; ` {'Mon':'一', 'Tue':'二'}`

* 集合 (set) &rarr; `{7, 14}`
  
### 轉換

* `float` &rarr; `int` (無條件捨去小數部分)

    ```py
    v = 1.5
    v = int(v)
    print(v) #output:1
    ```

* 數值 &hArr; 字串

    * `int` &rarr; `str`

        ```py
        a, b = 1, 0.5
        a, b = str(a), str(b)
        print(type(a), type(b))
        #output:<class 'str'> <class 'str'>
        ```

    * `str` &rarr; `int`

        ```py
        x, y = '5', '0.1'
        x, y = int(x), float(y)
        print(type(x), type(y))
        #output:<class 'int'> <class 'float'>
        ```

* 每個型態都可以轉為 **str** , 但不是每個都轉得回來

---

## <3> 輸入 & 輸出

* `print()`

    * 括號裡可以放任意型態的資料

    * 用 `,` 分隔資料 , 輸出時會有一格空格分隔

        ```py
        v = 1
        print(v,v) #output:1 1
        ``` 

    * `f-string` (格式化字串) | 在字串前加上 `f` , 字串內部的資料用 `{}` 包起來 ; 可以賦值給變數

        ```py
        t, f = True, False
        print(f'{t}/{f}') #output:True/False
        ```

    * `sep = ''` | 分隔符號 , 預設為 **一格空白**

        ```py
        print(True, False, sep='|') #output:True|False
        ```

    * `end = ''` | 結尾符號 , 預設為 `\n` **換行符號**

        不想換行可以用 `end=''`

        ```py
        print('abc', end='')
        print('def', end='')
        #output:abcdef
        ```

    * `flush = True` &rArr; 強行重新整理 , 預設為 `False`
    
        當 print() 在迴圈裡且引數 `end` 不為預設值 `\n` 時 , 輸出就會堵塞 , 一次性輸出而非順序輸出 , 這時就需要 `flush=True`

        ```py
        #一次性輸出的Loading bar
        import time
        print('Loading', end='')
        for i in range(6): #重複6次
            print('.', end='')
            time.sleep(0.5) #等待0.5秒
        ```

        ```py
        #正常輸出的Loading bar
        import time
        print('Loading', end='')
        for i in range(6): #重複6次
            print('.', end='', flush=True)
            time.sleep(0.5) #等待0.5秒
        ```

* `input()`

    * 括號內文字的作用為提醒使用者的文字
      
        ```py
        name = input('Enter Your Name : ') #output:Enter Your Name : 
        ```
    
    * 注意 : input() 回傳值皆為 `str` 型態 , 需要時要進行轉換

        ```py
        age = int(input('Enter Your Age : '))
        ```

    * 可以用 `split()` 方法達成一行輸入多個資料

        ```py
        l = input('輸入姓名 & 年齡 (用一格空格分隔)').split(' ') #split()會回傳串列
        name = l[0]
        age = int(l[1])
        ```
    
## <4> 字串
* 合併字串
  
    ```py
    s = 'Hello' + 'World'
    print(s) #output:HelloWorld
    ```

* `f-string` 格式化字串

    ```py
    i = 2
    s = 'a'
    v = f'{i}{s}'
    print(v) #output:2a
    ```

* 位置
  
    * 字元位置
    
        | a | p | p | l | e |
        |---|---|---|---|---|
        | 0 | 1 | 2 | 3 | 4 |
        |-5 |-4 |-3 |-2 |-1 |

    * 取字元
    
        ```py
        l = 'apple'
        print(l[0]) #output:a
        print(l[-1]) #output:e
        ```

    * 取子字串
    
        ```py
        l = 'orange'
        print(l[0:2]) #output:or
        print(l[3:]) #output:nge
        print(l[:4]) #output:oran
        ```
    
    * `find()` | 取得子字串位置 , 括號內放要找的字串(字元)

        ```py
        s = 'abcdef'
        print(s.find('a')) #output:0
        print(s.find('cd')) #output:2 #回傳子字串首字在母字串的位置
        print(s.find('z')) #output:-1 #沒有找到則回傳-1
        ```
    
* `split()` | 分割字串

    ```
    str.split(sep, maxsplit) -> str
    ```

    * 參數
        
        * **sep** (optional) &rarr; 分隔字符 , 預設為 **一格空白**

        * **maxsplit** (optional) &rarr; 分割數量 , 預設為 **-1** (全部)

    * 範例

        ```py
        s = '1 2 3'
        s.split() #return:['1','2','3']
        ```

* `strip()` | 去除字串首尾指定的字符

    ```
    str.strip() -> str
    ```

    * 參數
  
        * 只有一個 (optional) &rarr; 要去除的字符 , 預設為 **空格** & `\n` & `\t`

    * 範例
        ```py
        '  abc  '.strip() #return:abc
        ```

* `upper()` | 將字串轉為大寫

    ```
    str.upper() -> str
    ```

* `lower()` | 將字串轉為小寫

    ```
    str.lower() -> str
    ```

* `len()` | 回傳字串長度(字元數量) , 也可以用在串列 & 元組 & 字典 & 集合

    ```
    len() -> int
    ```

    * 參數

        * 只有一個 &rarr; 字串 , 串列 , 元組 , 字典 , 集合

* `str()` | 任意型態轉為字串

    ```
    str() -> str
    ```

## <5> 串列
* 新增元素

    ```py
    l = [1, 2]
    
    #新增到尾端
    l.append(3)
    print(l)
    #output:[1, 2, 3]

    #插入到指定位置
    #insert(位置,元素)
    l.insert(0, 0.1)
    print(l)
    #output:[0.1, 1, 2, 3]
    ```

* 刪除元素

    ```py
    l = [0.1, 1, 2, 3]

    #刪除尾端元素
    l.pop()
    print(l)
    #output:[0.1, 1, 2]

    #刪除指定位置元素
    del( l[0] )
    print(l)
    #output:[1, 2]
    ```

## <6> 字典
<https://medium.com/ccclub/ccclub-python-for-beginners-tutorial-533b8d8d96f3>

---

## <7> 條件判斷
* `if(條件):` | 當...則

    ```py
    a = 2
    if(a>=1):
        print('Yes')
    #output:Yes
    ```

* `if-else` | (當...則...)(否則...)

    ```py
    a = 0
    if(a>=1):
        print('Yes')
    else:
        print('No')
    #output:No
    ```

* `if-elif-else` | (當...則...)(否則如果...則...)(否則...)

    注意 : 有 `elif` 就一定有 `else`

    ```py
    age = 14
    if(age<14):
        print('無責任能力')
    elif(14<=age<18 or 80<=age):
        print('限制責任能力')
    else:
        print('完全責任能力')
    #output:限制責任能力
    ```

* `and` 且 | `or`  或

    ```py
    x = 14
    if(x%2==0 and x%7==0):
        print(f'{x}是2和7的公倍數')
    #output:14是2和7的公倍數
    ```

* `pass` | 不做任何事 , 可放在 `else` 語句

    ```py
    age = 14
    if(age<14):
        print('無責任能力')
    elif(14<=age<18 or 80<=age):
        print('限制責任能力')
    elif(18<=age<80):
        print('完全責任能力')
    else:
        pass
    ```

* 三元運算子 | 讓 `if-else` 更簡潔

    ```
    條件為真 if 條件 else 條件為假
    ```

    ```py
    score = 60
    print('PASS' if score>=60 else 'FAIL')
    #output:PASS
    ```

## <> 例外處理
<https://steam.oxxostudio.tw/category/python/basic/try-except.html>

---

## <> 迴圈
* for迴圈 (for loops)

    * `for 變數 in range(起始值,終止值,遞增(減)值):`

        * 起始值 & 終止值 & 遞增(減)值 必為 **整數**
        
            起始值 預設為 **0** , 遞增(減)值 預設為 **1**

            也可以寫成 `for i in range(次數):`

        * 起始值 $\leq$ **變數** $<$ 終止值

            變數名稱通常是 `i` , `j` , `k` . . .

        * 範例

            ```py
            for i in range(3):
                print(i)

            '''
            output:
            0
            1
            2
            '''
            ```

            ```py
            for i in range(5,2,-1):
                print(i)

            '''
            output:
            5
            4
            3
            '''
            ```

    * `for 變數 in 資料:`

        * 範例

            ```py
            for i in 'abc':
                print(i)

            '''
            output:
            a
            b
            c
            '''
            ```

            ```py
            for i in [0,1,2]:
                print(i)

            '''
            output:
            0
            1
            2
            '''
            ```

            ```py
            Dict = {'Mon':'一', 'Tue':'二', 'Wed':'三'}
            for i in Dict:
                print(f'{i}:{Dict[i]}')

            '''
            output:
            Mon:一
            Tue:二
            Wed:三
            '''
            ```

* while迴圈 (while loops)

    * `while(條件):`
      
        ```py
        i = 0
        while(i<=2):
            print(i)

        '''
        output:
        0
        1
        2
        '''
        ```

    * `while(True):` | 無窮迴圈
    
        按 `Ctrl` + `C` 中斷無窮迴圈

* `break` 中止

    ```py
    x = 5

    while(True):
    
        if(x==7):
            break
        else:
            print(x)
    
        x += 1

    '''
    output:
    5
    6
    '''
    ```

* `continue` 跳過本次迴圈 continue 以下內容

    ```py
    for i in range(2):
        print(f'\ni={i}', end='')
        print('a', end='')
        
        if(i==1):
            continue
        
        print('b', end='')

    '''
    output:
    
    i=0
    a
    b
    
    i=1
    a
    '''
    ```

# <> 函式 (function)
* 宣告函式

    ```py
    def fun():
        print('Hello World')
    ```

* 呼叫函式

    ```py
    fun()
    #output:Hello World
    ```

* 參數

    ```py
    def plus(a,b):
        print(f'{a}+{b}={a+b}')

    plus(1,2)
    #output:1+2=3

    #也可以這樣傳入
    plus(a=3,b=4)
    #output:3+4=7
    ```

    * 預設值(當沒有傳入參數時使用預設值)

        ```py
        def welcome(user='Master'):
            print(f'Welcome, {user}.')

        welcome()
        #output:Welcome, Master.

        welcome('Mike')
        #output:Welcome, Mike.
        ```

* 回傳

    ```py
    def bmi(height, weight):
        return weight/(height/100)**2

    myBMI = bmi(170,50)
    print(myBMI)
    #output:17.301038062283737
    ```

* 全域變數 & 區域變數

    <https://ithelp.ithome.com.tw/articles/10206034>

* `global`

    在 Python 中 , 你不能在函式中直接對全域變數重新賦值(很奇怪對吧,其他語言就不會這樣) , 需要在函式裡加上 `global <variable>` 才不會出現 `UnboundLocalError` 例外

    ```py
    # Wrong

    x = 1

    def foo():
        x += 1

    foo()
    #output:UnboundLocalError
    ```

    ```py
    # Correct

    x = 1

    def foo():
        global x
        x += 1

    foo()
    print(x)
    #output:2
    ```

    要在全域使用區域變數也需要在函式裡加上 `global <variable>`

    ```py
    def foo():
        global x
        x = 50

    foo()
    x = int(x/10)
    print(x)
    #output:5
    ```

* `nonlocal`

    在函式裡的函式使用上一層的區域變數需要在本層加上 `nonlocal <variable>`

    ```py
    def fooA():
        x = 100
        def fooB():
            nonlocal x
            x = int(x/10)
            print(x)
        fooB()
    
    fooA()
    #output:10
    ```

* 觀念題

    * a.

        ```py
        x = 1

        def foo(x):
            x *= 2
            print(x)

        foo(x-8)
        #output:?
        ```

    * b.

        ```py
        x = 1

        def foo():
            global x
            x -= 5
            print(x)

        foo()
        #output:?
        ```

    * 這樣會發生什麼事 ?

        ```py
        x = 1
        def foo(x):
            global x
            x /= 10
            print(x)

        foo(x)
        #output:SyntaxError
        ```

    * 答案

        a. `14`

        b. `-4`

* 如何調用和參數名稱一樣的全域變數 ? (有點邪門歪道)

    ```py
    x = 1
    
    def foo(x):
        x *= 2
        globals()['x'] *= 2

        print(f'區域x: {x}')
        print(f'全域x: {globals()['x']}')

    foo(5)
    #output:
    #區域x: 10
    #全域x: 2
    ```

    `globals()` &rArr; 以字典型態回傳全域變數
    
    `locals()` &rArr; 以字典型態回傳區域變數(在全域環境下呼叫則和 `globals()` 作用相同)

* <> 類別 (Class)

    類別 : <https://www.learncodewithmike.com/2020/01/python-class.html>
    
    方法 : <https://www.learncodewithmike.com/2020/01/python-method.htm>

    屬性 : <https://www.learncodewithmike.com/2020/01/python-attribute.html>

    繼承 : <https://www.learncodewithmike.com/2020/01/python-inheritance.html>