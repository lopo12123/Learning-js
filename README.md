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
   1. 在html文件中用script标签  
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

   1. 在外部文件中，需要在html页面中引入（在script标签中的src属性写入js文件的路径）
   ``` javascript
   // test.js
   alert("使用外部js文件弹窗");

   // index.html
   <script src="test.js"></script>
   ```

3. js代码**注意问题**
   1. 在一对script的标签中有错误的js代码，那么该错误后面的js代码不会执行  
   ``` html
   // 错误代码，后面不会执行
   <script>
     alert("我是错的;
     alert("我是对的");
   </script>
   ```

   2. 如果一对script标签中有错误，不会影响其他的script标签  
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

   3. script标签中可以写什么内容
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
      5. script 标签在页面中可以出现多对  

      6. script 标签一般放在 body 标签的最后（与加载顺序和外部引入有关），有时会放在 head 标签中  

      7. 如果 script 标签是引入外部js文件的作用，那么这对标签这种不要写任何的js代码；
      如果要写代码，重新写一对script标签再写  
<br>

> ## 二、变量  
1. 变量声明  
   1. js中存储数据使用变量的方式 (名字，值 --> 数据)  

   2. js中声明变量都用 **var** --> 存储数据，数据应该有对应的数据类型  

   3. js中字符串类型的值都用**单引号**或**双引号**  

   4. 变量声明 (声明不赋值 var a;)  
      变量初始化 (声明并赋值 var a = 1;)  
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
   2. js的变量名**大小写敏感** (即 a 与 A 是两个变量)  
   3. 变量名取名规则:   
      一般以 **字母、$、_** 开头;  
      中间或后面可以有 ** $、字母、数字 **;

3. ererer



<br>

> ## 三、？？  

- 数据类型  


- 运算符  
