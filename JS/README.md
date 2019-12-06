

  它的运行环境：浏览器.
   B/S (Browser / Server)

1. 学习JavaScript必须要掌握的五个部分：
a. 核心部分：基本语法、函数定义、函数的调用、类、对象、继承.
b. 内置函数：Function、String、Date、Number、Math、RegExp、Array.
c. BOM(Browser Object Model)浏览器对象模型(增强用户交互)：window、document、self、parent.
d. DOM(Document Object Model)文档对象模型(增强用户交互).
e. AJAX(Async Javascript And Xml)异步请求(改善用户体验). 可以实现页面局部刷新.
   

2. 函数的定义：
   匿名函数：

    第一种方式：
    ```
    (function(形参列表){
        // 函数的执行体
    })(实参列表);
    ```

    第二种方式：
    ```
    (function(形参列表){
        // 函数的执行体
    }(实参列表));
    ```

3. 函数调用：
     
    a.用call调用：
    test1.call(document, 10,20);

    函数名.call(主调, 实参列表);

    b.用apply调用：
    test1.apply(document,[10,20]);

    函数名.apply(主调, 实参列表(数组));

4. 特殊运算符：
   
   // null、undefined、false、0
   if (0){
	
   }
 
5. 变量：
    var str = 20; // Number
    var str = []; // Array
    var str = //; // RegExp


    全局变量：都属于window.
        window.变量名.

    局部变量：
        函数体内用var定义的变量.


6. BOM浏览器对象模型：
   定时器:
    第一组
        setInterval();
        clearInterval();

    第二组(延迟的定时器)：
        setTimeout();
	    clearTimeout();

