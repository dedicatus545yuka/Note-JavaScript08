# Note-JavaScript08
### 正则表达式  
- 正则表达式(Regular Expression): 由一些普通字符和特殊字符组成的，用以描述一种特定的字符规则的表达式。 
- 正则表达式常用于在一段文本中搜索、匹配或替换特定形式的文本。
- 起到一个作用，验证；正则表达式用来定规矩。独立于任何语言，也就是适用于任何语言。
    - 正则表达式本身的内容
    - 正则表达式在JS中的使用,在 JavaScript中，正则表达式也是对象 - RegExp对象
#### 创建（定义）表达式  
1. 字面量方式 
- 语法结构中不允许定义空的正则表达式
- 语法结构 - /正则表达式的规则/+修饰符
```js
var reg = /xxx/; 
```
2. 构造函数的方式  
- 语法结构 - new RegExp(pattern, attributes)
    * pattern - 表示正则表达式的规则
    * attributes - 表示修饰符
```js
var reg = new RegExp();
```
3. 与数组相类似的情况  
```js
var reg1 = /xxx/; 
var reg2 = new RegExp();
console.log(typeof reg1); // object
console.log(typeof reg2); // object
``` 
#### 规则
1. 正则表达式的应用
```js
// 1. 获取用户输入的内容 - 自定义字符串替代
var str = 'text1234567890string';

// 2. 定义一定规则的正则表达式
// var reg = /1234567890/;// true
// var reg = /123/;// true
// var reg = /124/;// false
// var reg = /456/;// true
var reg = /text2/;// false

// 3. 验证 - reg.test(string)
var result = reg.test(str);
/*
    reg.test(str)方法
    * 如果结果为true -> 表示当前字符串与正则表达式匹配
    * 如果结果为false -> 表示当前字符串与正则表达式不匹配
 */
console.log(result);
```
![表达式的应用图示](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/QBY04HAgY5NqOEvv7g8toPUUL7I5FU18.jttT*O7jLw!/m/dD4BAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)      
2. 字符类的验证    
- 将直接量字符单独放进方括号内就组成了字符类。
- 一个字符类可以匹配它所包含的任意字符。
- 由于某些字符类非常常用，JavaScript 的正则表达式中，使用`特殊转义字符`表示它们。
> 值得注意的是: 在方括号之内也可以编写这些特殊转义字符。   

![](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/zCfmSpk0f8*EjhSHsZ3j5Gwtd0dC5axnTXqRYqGaGf4!/m/dPMAAAAAAAAA&bo=nwSAAgAAAAADBzs!&rf=photolist)    
3. 重复的验证 
- 在 JavaScript 中的正则表达式用来描述任意多位的数字，或者描述由三个字母和一个数字构成的字符串时，可以使用字符重复的标记。
>  “*”和“?”可以匹配 0 个字符，允许什么都不匹配。    
![](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/VM2usiNPm14PKFoD2*5ViwvUO9Mn.EAuUo1blXpvJXo!/m/dPMAAAAAAAAA&bo=ZAW.AQAAAAADB*w!&rf=photolist)     
4. 选择、分组和引用    
- 正则表达式包括指定选择项、子表达式分组和引用前一子表达式的特殊字符。
![](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/uMv4LXYgJZYLKhaTRSe3uNWidYdnZ0w0UbF*15DvamA!/m/dPMAAAAAAAAA&bo=JgaeAQAAAAADB50!&rf=photolist)    
5. 指定匹配位置      
- 正则表达式中的多个元素才能够匹配字符串的一个字符，这些元素称之为正则表达式的锚。因为它们将模式定位在搜索字符串的特定位置上。   
![](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/YfAggzxTgHuFdzOyL8wYD1krqalKRh5lW8Qjri3dx5g!/m/dPIAAAAAAAAA&bo=*gUIAgAAAAADB9M!&rf=photolist)    
6. 修饰符   
> 正则表达式的修饰符，用于说明高级匹配模式的规则。修饰符是放在“/”符号后面的，JavaScript 支持三个修饰符。

- i - 不区分大小写搜索
- g - 全局搜索
- m - 多行搜索    
7. 正则表达式的规则
```js
var str = '111';
/*
    正则表达式的规则
    1.[] - 表示匹配内容的集合
      * 特点 - 只要匹配当前集合中的任意一个字符即可
    2.^ - 表示匹配开始的位置(就是以什么开始)
    3.$ - 表示匹配结束的位置(就是以什么结束)
    4.{n,m} - 表示匹配内容的重复次数
      * n - 表示重复次数的下限
      * m - 表示重复次数的上限
 */
// var reg = /[123]/;
/*
    要匹配的是数字和字母
    * 数字 -> 0-9 -> \d
    * 小写字母 -> a-z
    * 大写字母 -> A-Z
  */
// var reg = /[0-9a-zA-Z]/;
// var reg = /[1]/;
// var reg = /^[123]/;
// var reg = /[123]$/;

// 以什么开始，并且以什么结束 - 什么表示123中的任意一个(a.同一个，b.数量)
// var reg = /^[123]$/;

// var reg = /[1]{1,2}/;
// var reg = /^[123]{1,2}/;
var reg = /^[123]{1,2}$/;

var result = reg.test(str);

console.log(result);
```
- 一个小小的练习
```js
// 必须是数字，并且长度在 4-6 之间
var reg = /^[0-9]{4,6}$/;

var result = reg.test('1234567');
console.log(result);

// 匹配数字、字母，并且长度在 6-12 之间
var reg = /^[0-9a-zA-Z]{6,12}$/;

var str = 'this ' +
    'is string'; //字符串不允许换行
```
#### RegExp对象
>JavaScript 可以通过引用类型 RegExp 创建正则表达式对象
```js
var pattern =new RegExp( pattern, attributes );
```
- pattern 参数: 被称为模式（规则），可以是任何简单或复杂的正则表达式，包含字符类、限定符、分组、向前查找以及反响引用等。
- attributes 参数: 被称为修饰符，用于标明正则表达式的行为。   
1. 属性     
![](http://a1.qpic.cn/psb?/V118JuTr0BKcy7/7DTUyzCj2E8Cksw9y6UMtVq*FKiDYJwZWvbKirLGtm8!/b/dPMAAAAAAAAA&bo=IAM8AgAAAAADBz8!&rf=viewer_4)

2. 方法    
![](http://a1.qpic.cn/psb?/V118JuTr0BKcy7/1odNjd11vyeN4VKC3tj2c7I2tO6*VzKJWU.idlLFVxA!/b/dPMAAAAAAAAA&bo=5gSqAQAAAAADAGw!&rf=viewer_4)

#### 字符串的模式匹配
```js
var str = '1234567123890123';
/*
    search(regexp)方法
    * 作用 - 检索指定字符串中是否包含指定内容
    * 参数
      * string - 指定检索的文本内容
      * regexp - 指定检索匹配指定正则表达式的文本内容
    * 返回值
      * 如果包含，返回匹配的第一个字母的索引值(位置)
      * 如果不包含，返回 -1
  */
// var result = str.search('124');
/*var result = str.search(/123/);
console.log(result);*/

/*
    match()方法
    * 作用 - 指定字符串匹配指定文本内容
    * 参数
      * string
      * regexp
    * 返回值
      * 返回数组 - 1.匹配的内容；2.匹配内容第一个的索引值(位置)；3.当前字符串
 */
/*var result = str.match(/[123]/g);
console.log(result);*/

/*
    replace(regexp,replacement)方法
    * 作用 - 使用指定内容替代正则表达式匹配的内容
    * 参数
      * regexp - 用于匹配当前字符串中符合正则表达式规则的内容
      * replacement - 用于替代的内容
    * 返回值 - 替换之后的结果
    * 注意 - 不影响原本字符串的内容
 */
var result = str.replace('123','string');
console.log(result);
console.log(str);
```
#### 字面量字符  
- 其实跟Html中的转义字符一样       
![](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/uniFvjGg7xfOkxifI0hyojlP9a4i.UyaSkjsEehZ5D4!/m/dPIAAAAAAAAA&bo=GwOAAgAAAAADB7g!&rf=photolist)     
### 字符串  
#### 属性
```js
var str = new String('this is string');
// length属性 - 获取当前字符串的字符个数
console.log(str.length);
// 遍历循环
for (var i=0;i<str.length;i++){
    console.log(str[i]);
}
// String和Array有没有关系?
console.log(str instanceof String);// true
console.log(str instanceof Array);// false
```
#### 方法  
1. 大小写转换(中文没有大小写)
- toUpperCase() : 把字符串转换为大写。
- toLowerCase() : 把字符串转换为小写.
```js
var msg = 'Hello World';

var lowerMsg = msg.toLowerCase();
var upperMsg = msg.toUpperCase();

console.log( msg );// Hello World
console.log( lowerMsg );// hello world
console.log( upperMsg );// HELLO WORLD
```
2. 获取指定位置的字符  
```js
var str = new String('this is string');
/*
    charAt(index)方法
    * 作用 - 根据index位置返回指定字符串中的字符内容
    * 参数
      * index - 表示字符串中的指定位置
    * 返回值 - 指定index位置对应的字符
 */
/*var result = str.charAt(3);
console.log(result);*/

// charCodeAt()方法 -> 返回Unicode编码
var result = str.charCodeAt(3);
console.log(result);
```
3. 检索字符串  
- indexOf(searchvalue,fromindex) : 返回某个指定的字符串值在字符串中首次出现的位置。
    - searchvalue ：必需，规定需检索的字符串值。
    - fromindex ：可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。
- lastIndexOf() : 从后向前搜索字符串
```js
var email = 'tom@163@sohu.com';

console.log( email.indexOf('tom'))// 0
console.log( email.indexOf( '@',5));// 7 - 看的还是字符底下的编号,后面的5是从第6个位置开始
console.log( email.lastIndexOf('@'));// 7
console.log( email.lastIndexOf('@',5));// 3 - 这里的往回找字符底下的编号没有变只是倒回去找，10-9-8.....
console.log( email.indexOf('mary'));// -1 - 字符串中没有就返回 -1
```
4. 截取子字符串   
```js
var str = '12345abcdeABCDE';

/*
    slice(start,end)
    * 作用 - 从指定字符串中截取指定位置的子字符串
    * 参数
      * start - 表示开始截取的位置
      * end - 表示结束截取的位置(不包含)
        * 如果默认省略，表示截取到字符串的最后
 */
// var result = str.slice(0,2);
// var result = str.slice(0);
/*var result = str.slice(-3,-1);
console.log(result);*/

/*
    substr(start,length)方法
    * 作用 - 从指定字符串截取指定位置的指定长度的子字符串
    * 参数
      * start - 表示开始截取的位置
      * length - 表示截取的长度
        * 注意 - 如果设定长度超过字符串剩余字符的个数时，截取到字符串的最后面
        * 如果截取的长度省略的话，自动截取到字符串的最后面
 */
/*var result = str.substr(5);
console.log(result);*/

/*
    substring(start,end)方法
    * 作用 - 从指定字符串中截取指定开始和结束位置的子字符串
    * 参数
      * start - (不能是负整数)表示截取的开始位置
      * end - (不能是负整数)表示截取的结束位置
 */
var result = str.substring(0,5);
console.log(result);
```
5. 分隔字符串
- split() :	把字符串分割为字符串数组。
```js
/* var str = '1 2 3 4 5';
var arr = str.split(' ');
console.log(arr);// [ '1', '2', '3', '4', '5' ]*/

/*var str = '1,2,3,4,5';
var arr = str.split(',');
console.log(arr);// [ '1', '2', '3', '4', '5' ]*/

/*var str = '1;2;3;4;5';
var arr = str.split(';');
console.log(arr);// [ '1', '2', '3', '4', '5' ]*/

var str = '12345';
var arr = str.split('');
console.log(arr);// [ '1', '2', '3', '4', '5' ]
```
6. 连接字符串   
- concat() : 连接两个或更多字符串，并返回新的字符串。
```js
var s1 = 'AA';
var s2 = s1.concat('BB', 'CC', 55);

console.log( s1 ); //AA
console.log( s2 ) ; //AABBCC55
```
7. 反转字符串   
- reverse() 方法用于颠倒数组中元素的顺序。
- 该方法会改变原来的数组，而不会创建新的数组。
```js
var str = '12345';// 54321
var arr = str.split('');// 分割字符串，以数组形式输出
var result = arr.reverse();//反转
result = result.toString();//类型转换
result = result.replace(/,/g,'');//替换
console.log(result);
```
8. 判断是否包含
```js
var str = 'vbkjhaskdhalda';
var str2 = 'halda';

/*var result = str.indexOf(str2);
if (result === -1){
    console.log('不包含');
} else {
    console.log('包含');
}*/

// 必须使用字符串的截取方法实现
var result = str.substr(str.indexOf(str2),str2.length);
if (result === str2){
    console.log('包含')
} else {
    console.log('不包含');
}
```
