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
   ```
   2. 22222  

8. **boolean、undefined** 及 **null** 类型  

9.  ？？
<br>

> ## 三、？？？
1. 一 一 一  
<br>

> ## 四、？？？
1. 一、一、一
