# Learning-js

*learning materials of js*  

> ## Basic content
1. js的介绍及基本语法变量，运算符；  
2. js的流程控制：分支语句、循环、顺序结构；  
3. 数组；  
4. 函数；  
5. 内置对象；  
6. 内置对象及一些方法；  

<br>

---

# Notes
- *ECMAScript* 标准 --- js的基本语法  
- *DOM* --- *Document Object Model* 文档对象模型  
- *BOM* --- *Browser Object Model* 浏览器对象模型  
<br>

> ## 一、介绍  

| 语言 | 作用 |
| :-: | :-: |
| HTML | 标记语言，展示数据 |  
| CSS | 美化页面 |  
| JavaScript | 控制页面，用户和浏览器交互 |  

1. js介绍  
  - 脚本语音、解释性语言、动态类型、基于对象  
  - js **原名** *LiveScript*  
  - **作用**：解决用户和浏览器之间的交互的问题  

2. js代码可以在**三个地方**书写  
   1. 在html文件中用`script`标签  
   ``` html
   <script>
   // js code
   alert("使用script标签弹窗！");
   </script>
   ```

   1. 在html标签中  
   ``` html
   <!--
     html code
     onclick后面的部分就是js代码
     -->
   <input type="button" value="按钮" onclick="alert('通过html标签弹窗');">
   ```

   1. 在外部文件中，需要在html页面中引入（在`script`标签中的`src`属性写入js文件的路径）
   ``` javascript
   // test.js
   alert("使用外部js文件弹窗");

   // index.html
   <script src="test.js"></script>
   ```

3. js代码**注意问题**
   1. 在一对`script`的标签中有错误的js代码，那么该错误后面的js代码不会执行  
   ``` html
   // 错误代码，后面不会执行
   <script>
     alert("我是错的;
     alert("我是对的");
   </script>
   ```

   2. 如果一对`script`标签中有错误，不会影响其他的`script`标签  
   ``` html
   <script>
     alert("我是错的;
     alert("我是对的 1");  // 不会执行
   </script>
   <script>
     alert("我是对的 2");  // 正常执行
   </script>
   <script>
     alert("我是对的 3");  // 正常执行
   </script>
   ```

   3. `script`标签中可以写什么内容
      1. type="text/javascript" 是标准写法
      ``` html
      <script type="text/javascript">
        alert("type 1");
      </script>
      ```
      2. language="JavaScript" 也可以
      ``` html
      <script language="JavaScript">
        alert("type 2");
      </script>
      ```
      3. 都不写也可以（因为 html 遵循h5标准）
      ``` html
      <!DOCTYPE html>
      <script>
        alert("type 3");
      </script>
      ```
      4. 有可能出现：*type* 和 *language* 属性都写
      ``` html
      <script type="text/javascript" language="JavaScript">
        alert("type 4");  // 两种属性都写避免浏览器解析出现意外错误
      </script>
      ```
      5. `script`标签在页面中可以出现多对  

      6. `script`标签一般放在`body`标签的最后（与加载顺序和外部引入有关），有时会放在`head`标签中  

      7. 如果`script`标签是引入外部js文件的作用，那么这对标签这种不要写任何的js代码；
      如果要写代码，重新写一对`script`标签再写  
<br>

> ## 二、变量  
1. 变量声明  
   1. js中存储数据使用变量的方式 (名字，值 --> 数据)  

   2. js中声明变量都用`var` --> 存储数据，数据应该有对应的数据类型  

   3. js中字符串类型的值都用**单引号**或**双引号**  

   4. 变量声明 (声明不赋值`var a;`)  
      变量初始化 (声明并赋值`var a = 1;`)  
   ``` javascript
   var a;  // 变量的声明
   var b, c, d;

   a = 1;  // 变量的赋值
   b = 2;
   c = 3;
   d = 4;

   var e = 5;  // 变量的初始化
   var f = "小白";
   var g = true;
   var h = null;
   var i = new Object();
   ```

2. 代码规范  
   1. js每一行结束用**分号 ';'**  
   2. js的变量名**大小写敏感** (即`a`与`A`是两个变量)  
   3. 变量名命名规范:   
      - 一般以 **字母、\$、\_** 开头;  
      - 中间或后面可以有 **\$、字母、数字**;  
      - 变量名一般是**小写**的;  
      - 变量名如果有多个单词，**第一个单词**的首字母是**小写**的，后面所有单词的首字母都是**大写**的。这种命名方式称为***驼峰命名法***  
      ``` javascript
      // example
      var bigNumber;  // 驼峰命名法(js、go等)
      var big_number;  // 下划线命名法(python、c等)
      ```
      - 不能使用关键字(如`var、break`等)

3. 交换两个变量的值  
   1. 方法1：使用第三方  
   ``` javascript
   var num1 = 10;
   var num2 = 20;
   var temp;
   temp = num1;
   num1 = num2;
   num2 = temp;
   console.log(num1, num2);
   ```
   2. 方法2：一般用于数字的交换  
   ``` javascript
   var num1 = 10;
   var num2 = 20;
   num1 = num1 + num2;  // 30 = 10 + 20
   num2 = num1 - num2;  // 10 = 30 - 20
   num1 = num1 - num2;  // 20 = 30 - 10
   console.log(num1, num2);
   ```
   3. 方法3：位运算  
   ``` javascript
   var num1 = 10;
   var num2 = 20;
   num1 = num1 ^ num2;
   num2 = num1 ^ num2;
   num1 = num1 ^ num2;
   console.log(num1, num2);
   ```

4. 注释  
   1. 单行注释：`// abcdefg`  
   2. 多行注释：`/* abcdefg */`  

5. 数据类型  
   1. js中的原始数据类型  
   ``` javascript
   number, string, boolean, null, undefined, object
   /*
   * number: 数字类型(整数和小数)
   * string: 字符串类型(值一般是用单引号或双引号括起来)
   * boolean: 布尔类型(值只有两个, true(真1),false(假0))
   * null: 空类型, 值只有一个: null; 一个对象指向为空，则此时可以赋值为null
   * undefined: 未定义, 值只有一个: undefined
   * object: 对象
   */

   // undefined情况
   // 1. 变量声明了没有赋值
   // 2. 函数没有明确返回值
   var num;
   console.log(num);  // 输出 undefined
   console.log(num + 10);  // 输出 NaN --- not a number
   ```  
   2. 获取变量类型
   ``` javascript
   // typeof 用法
   // 1. typeof 变量名
   // 2. typeof(变量名)

   var num = 10;
   var str = "小明";
   var flag = true;
   var nll = null;
   var undef;
   var obj = new Object();

   console.log(typeof num);  // number
   console.log(typeof str);  // string
   console.log(typeof flag);  // boolean
   console.log(typeof nll);  // 不是null(是object)
   console.log(typeof undef);  // undefined
   console.log(typeof obj);  // object
   ```  

6. **Number** 类型  
   - 不要用小数验证小数  
   - 不要用NaN验证NaN  
   <br>

   1. js可以表示的进制  
   ``` javascript
   var num1 = 12;  // 十进制
   var num2 = 012;  // 八进制(以0开头)  十进制的10
   var num3 = 0x12;  // 十六进制(以0x开头)  十进制的18
   ```  
   2. 数字类型的范围：最小值和最大值  
   ``` javascript
   console.log(Number.MAX_VALUE);  // 最大值
   console.log(Number.MIN_VALUE);  // 最小值
   Infinity;  // 无穷大
   -Infinity;  // 无穷小
   NaN;  // not a number  NaN != NaN
   isNaN();  // is 'not a number'  验证是否是NaN(不是数字): 是数字输出false; 不是数字输出true
   console.log(isNaN(10));  // false
   console.log(isNaN("你好"));  // true
   ```  
   3. 小数计算  
   ``` javascript
   // 小数的计算不一定精确
   // 原因：小数的二进制存储不一定精确
   var x = 0.1;
   var y = 0.2;
   var sum = x + y;
   console.log(sum == 0.3);  // 输出为false
   ```  

7. **string** 类型  
   1. 字符串长度  
   ``` javascript
   var str = "abcdefg";
   console.log(str.length);  // 输出 7
   ```
   2. 字符串拼接
   ``` javascript
   // 1. 使用 '+' 连接多个字符串
   var str1 = "你";
   var str2 = "好";
   console.log(str1 + str2);  // 输出 "你好"(string类型)

   // 2. 如果一个是字符串其他是数字则还是拼接
   var str = "10";
   var num = 2;
   console.log(str + num);  // 输出 102(string类型)

   // 3. 如果一个是字符串另一个是数字则计算加减(隐式转换: 自动将字符串类型转换成了数字类型)
   var str = "10";
   var num = 2;
   console.log(str - num);  // 输出 8(number类型)
   console.log(str * num);  // 输出 20(number类型)
   ```
   3. 转义符  

   | 符号 | 字符 |
   | :-: | :-: |
   | \\b | 退格 |
   | \\f | 走纸换页 |
   | \\n | 换行 |
   | \\r | 回车 |
   | \\t | 横向跳格(ctrl+I) |
   | \\' | 单引号 |
   | \\" | 双引号 |
   | \\\ | 反斜杠 |

8. **boolean**类型、**undefined** 及 **null**  
   1. Boolean类型  
      - Boolean类型值: true / false
      - 计算机内部存储: true = 1 / false = 0
   2. undefined和null  
      - undefined表示一个声明了没有赋值的变量，变量只声明的时候值默认为undefined
      - null表示一个空，变量的值如果想要为null，必须手动设置

9. **object**类型  
   - **pass**

10. 类型转换  
    1. 其他类型转**数字**类型(三种)  
    ``` javascript
    // 1. 转整数 parseInt()
    // 数字直接转 / 数字开头转 / 字母开头不转 / 小数取整
    console.log(parseInt("10"));  // 10
    console.log(parseInt("10fdsfd"));  // 10
    console.log(parseInt("g10"));  // NaN
    console.log(parseInt("1fds0"));  // 1
    console.log(parseInt("10.98"));  // 10
    console.log(parseInt("10.98fdsfd"));  // 10

    // 2. 转小数 parseFloat()
    // 无小数部分则显示整数
    console.log(parseFloat("10"));  // 10
    console.log(parseFloat("10fdsfd"));  // 10
    console.log(parseFloat("g10"));  // NaN
    console.log(parseFloat("1fds0"));  // 1
    console.log(parseFloat("10.98"));  // 10.98
    console.log(parseFloat("10.98fdsfd"));  // 10.98

    // 3. 转数字 Number()
    // 带有字母转换结果都是NaN (转换方式比1、2严格)
    console.log(Number("10"));  // 10
    console.log(Number("10fdsfd"));  // NaN
    console.log(Number("g10"));  // NaN
    console.log(Number("1fds0"));  // NaN
    console.log(Number("10.98"));  // 10.98
    console.log(Number("10.98fdsfd"));  // NaN
    ```
    2. 其他类型转**字符串**类型  
    ``` javascript
    // 1. object.toString()
    var num1 = 10;
    console.log(num1.toString());  // 10 (string类型)

    // 2. String()
    var num2 = 20;
    console.log(String(num2));  // 20 (string类型)

    // 如果变量有意义，调用.toString()转换
    // 如果变量没有意义，调用String()转换
    var num3;
    var num4 = null;
    console.log(num3.toString);  // 报错
    console.log(num4.toString);  // 报错
    console.log(String(num3));  // undefined
    console.log(String(num4));  // null
    ```
    3. 其他类型转**布尔**类型  
    ``` javascript
    // 1. Boolean(value);
    console.log(Boolean(1));  // true
    console.log(Boolean(0));  // false
    console.log(Boolean(11));  // true
    console.log(Boolean(-10));  // true
    console.log(Boolean("哈哈"));  // true
    console.log(Boolean(""));  // false
    console.log(Boolean(null));  // false
    console.log(Boolean(undefined));  // false
    ```

11. 操作符  
    1. 算数运算符  
       ` +, -, *, /, % `  
       算数运算表达式：由算数运算符连接起来的表达式  
    2. 一元运算符  
       只需要一个操作数就可以运算的符号 ` ++, -- `  
    3. 二元运算符  
       只需要两个操作数就可以运算的符号 ` +, -, *, /, % `  
    4. 三元运算符  
       只需要三个操作数就可以运算的符号 ` a ? x : y `  
    5. 复合运算符  
       ` +=, -=, *=, /= `
       复合运算表达式：由复合运算符连接起来的表达式  
    6. 关系运算符  
       ` >, <, >=, <=, ==, ===, !=, !== `  
       ``` javascript
       // '==','!=': 不严格; '===', '!==': 严格
       var str = "5";
       var num = 5;
       console.log(str == num);  // 输出为 true
       console.log(str === num);  // 输出为 false

       // == 和 != 比较类型若不同，先尝试转换类型再作值比较，最后返回值比较结果；
       // === 和 !== 只会在相同类型下才会比较其值(若类型不同则一定不同)
       ```
    7. 逻辑运算符  
       ``` javascript
       // && -- 逻辑与
       // || -- 逻辑或
       // ! -- 逻辑非
       ```
    8. 优先级
       ``` javascript
       // 1. () 优先级最高
       // 2. 一元运算符 ++ -- ！
       // 3. 算术运算符 先* / 后+ -
       // 4. 关系运算符 > >= < <= 
       // 5. 二元运算符 == != === !==
       // 6. 逻辑运算符 先&& 后||
       // 7. 赋值运算符 =
       ```

12. 语句、表达式、字面量  
<br>

> ## 三、流程控制  
1. 流程控制  
   1. 顺序结构：从上到下，从左到右执行的顺序  
   2. 分支结构：if语句，if-else语句，switch-case语句，三元表达式语句  
   3. 循环结构：while循环，do-while循环，for循环，for-in循环  
2. 分支语句  
   ``` javascript
      // 1. if 语句
      if (表达式) {
         代码;
      }

      // 2. if-else 语句
      if (表达式) {
         代码1;
      }
      else {
         代码2;
      }

      // 3. if-else if -else 语句
      if (表达式1) {
         代码1;
      }
      else if (表达式2) {
         代码2;
      }
      else {
         代码3;
      }

      // 4. 三元表达式
      // 变量 = 表达式1 ? 表达式2 : 表达式3;
      // 判断表达式1结果: true 则执行 表达式2;
      //                 false 则执行 表达式3;

      // 5. switch-case 语句
      // 注意：case的比较使用的是'==='和'!=='(严格的比较)
      switch(表达式) {
         case 值1: 代码1; break;
         case 值2: 代码2; break;
         case 值3: 代码3; break;
         ... ...
         default: 代码n;
      }
   ```
3. 循环语句  
   ``` javascript
      // 1. while 循环
      while(条件) {
         循环体;
         计数器++;
      }
      // 注意：先判断条件，再执行循环/跳出循环

      var i = 0;  // example
      while(i < 10) {
         console.log(i);
         i++;
      }

      // 2. do-while 循环
      do{
         循环体;
      }while(条件)
      // 注意：先执行一次循环体再判断条件，...

      var i = 0;
      do{
         console.log(i);
         i++;
      }while(i<10)

      // 3. for 循环
      for(表达式1;表达式2;表达式3) {
         循环体;
      }
   ```
4. **break**、**continue** 关键字
   1. **break**  
      遇到 break 则立刻跳出当前循环  
   2. **continue**  
      遇到 continue 则立刻开始下次循环  
<br>

> ## 四、数组  

- 数组索引从`0`开始  
- 数组长度 `arr.length`

1. 通过构造函数创建数组  
   ``` javascript
   // var array(数组名) = new Array(数组长度);
   var empty_array = new Array();  // 空数组
   console.log(empty_array);  // 输出Array(0)或[]

   var my_array1 = new Array(5);
   console.log(my_array);  // 输出Array(5), 其中每个值都是undefined

   // Array(一个数字)表示数组长度;
   // Array(多个数字)表示数组元素;
   var array1 = new Array(5);  // 数组长度为5, 数组元素为undefined
   var array2 = new Array(1, 2, 3, 4, 5);  // 数组长度为5, 数组元素为[1, 2, 3, 4, 5]
   ```
2. 通过字面量创建数组  
   ``` javascript
   // var 数组名 = [];
   var my_array2 = [];  // 空数组
   ```
3. 注意问题
   1. 数组中存储的数据类型一定是一样的吗？
      ``` javascript
      // 类型可以不一样
      var arr = [10, "哈哈", true, null, undefined, new Object()];
      console.log(arr);
      ```
   2. 数组的长度是否可以改变？
      ``` javascript
      // 长度可以改变
      var arr = [];  // length = 0
      arr[0] = 1;  // length = 1
      arr[1] = 2;  // length = 2
      console.log(arr.length);
      ```
<br>

> ## 五、五五五

