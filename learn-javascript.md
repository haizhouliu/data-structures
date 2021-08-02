```js
//let 和 const 命令
// 1. let 声明的变量只在let命令所在的代码块内有效，且要在 
      // 声明后使用,声明之前的区域叫TDZ(暂时性死区)
      // let定义的变量在块级作用域内，var是在函数作用域
// 2. let、const语句 不存在变量提升,但有TDZ
// 3. let 不允许在相同作用域内重复声明同一个变量
{
  let a = 10 
  var b = 1
}
console.log(a,b)

//const 它实际上保证的，并不是变量的值不得·改动，而是变量指向的那个内存地址所保存的数据不得改动
```

```js
//变量的解构赋值
 1.数组的解构赋值
let [,,...third] = [1,2,3,4,5]
let [a,[b],c] = [1,[2,3],4]

// 2.对象的解构
 1.与数组的区别是数组的元素是按次序排列的，变量的取值由它的位置决定。
 2.对象的属性没有次序，变量必须与属性同名，才能取到正确的值
 let {bar, foo} = {foo: 'a', bar: 'bbb'}
 3.对象的解构赋值的内部机制是先找到同名属性，然后在赋值给对应的变量,真正被赋值的是后者，而不是前者
 let {foo: a, bar: b} = {foo: 'liu', bar: 'hai'}
 //a: 'liu'
```

- js数据类型

  ```md
  numbers,
  strings, 
  Booleans,
  undefined,
  null,
  objects, 
  functions
  ```

- 浏览器函数

  ```js
  eval('1+2')
  3
  
  typeof (123).toFixed(3)
  "string"
  ```
  
- NaN相关

  ```js
  NaN (not a number)
  NaN 参与任何运算都是 false
  NaN != NaN
  null == undefined
  
  // 不是一个数 返回true
  window.isNaN(232) 
  >> false
  // 判断值是不是NaN,其它都为假
  Number.isNaN(NaN) 
  >> true 
  ```

- ```md
  有求值结果的代码片段叫作 表达式
  a = 1（赋值表达式） 
  
  最简单的一条语句由一个表达式和其后的分号组成，如下
    1;
    !false;
  var c = 8;(变量赋值打分号)
  当一行的第一个字符是 +, -, /, `,[, (,这几个符号的时候,在这些符号之前加;
  ```
  
- loop

  ```js
  //先执行一遍
  do {
    var yourName = prompt('Who are you?')
  } while (!yourName);
  console.log(yourName)
  
  //switch 通过 === 判断 
  switch () {
    case 1: {
       console.log(1)
       break;
    }     
  }
  
  //循环遇到continue的话，跳到下一次循环
  //遇到break语句的话，整个循环结束
  var x = 8; 
  x++;
  >> 8 
  >> x 
  >> 9
  >> var y ="9"
  >> y++
  >> 9 
  >> y
  >> 10 
  
  ```


- 词法作用域(lexical scoping)

  ```md
  只看变量所在的那个位置向外看
  
  代码块会产生作用域
  
  for循环
  for(var i = 0; i < 5; i++) {
    不产生作用域
  }
  ```

- ```js
  // 当function关键字在一行的 开头 时，是函数声明语句，没有求值结果
  // 函数声明中函数的名字不可以少
  // 函数声明没法直接调用 要用括号包起来
  function square(x) {
    return x*x
  }
  
  //变量声明，并将函数表达式的求值结果即一个函数赋值给这个变量
  var square = function a(x) {
      a() //只能在里面用
      return x * x
  }
  
  // 函数表达式不是变量声明，只能在内部使用  -> (addEventListener,removeEventListener)
  // 括号里面 函数表达式
  (function(){
    return 8
  })

  //函数声明语句会整体提前
  function f(){}
  console.log(f())
  ```
  
- 调用栈

  ```md
   1.计算内部用于存储函数返回位置，函数的局部变量的内存空间，叫调用栈
   2.函数间的相互调用的逻辑关系，叫调用栈
  ```


- 整数在计算机里的表示

  ```md
  左移 <<
  对于正数来说,是加倍
    1 << 5   32
  对于负数来说，也是加倍
    -2 << 1  -4
    
    n / 2 ==> n >> 1
  保留符号右移 >> 左边补符号，左边是1补1，是0补0
    相当于减半取整
  无符号右移 >>> 左边补0
    负数移完以后变成正数
    移完以后的数字永远当正数理解
  js中浮点数参与位运算时，取其整数部分的低32bit参与运算。
  
  按位与 &
    5 & 8 = 0
    15 & 9
  按位或 |
    '3' | 0
  按位异或 |
    相同为0
    不同为1
  0 和任何数 ^ 就是那个数自己 
  按位非 ~ 一元运算符
    ~n = -(n+1)
  ```
  
- 递归

  ```md
  写递归代码的技巧
    1.要有结束条件，对应到函数调用展开图中，即为到某一层后不在继续展开
    2.实现递归函数时，调用自身时认为这个函数已经正确实现
    3.递归的更深层次应该将问题向更小规模推进，或者更深层应该进入不递归的分支
    4.合成效益法则 （斐波那契数列用递归的话，要缓存）
    
    二分查找
    https://leetcode-cn.com/problems/search-insert-position/solution/te-bie-hao-yong-de-er-fen-cha-fa-fa-mo-ban-python-/
  ```

- 浮点数

  ```md
  # 浮点数的表示
  
  * 浮点数一般使用8字节即64bit存储，为双精度浮点数
    * 也有用4字节即32bit存储的单精度浮点数
  * 最左边一位表示符号，0表示正，1表示负
  * 接下来的11bit表示指数
  * 剩余的表示科学记数法中的小数部分，不含整数部分，因为整数部分总是1
  
  * 为什么指数的范围是-1023到1024而非-1024到1023？
    * 指数部分并没有使用补码进行存储
    * 正1024次方表示无穷大
  * 为什么指数部分读出时要减1023，写入时要加1023？
    * 指数部分使用原码，范围是0到2047
    * 表示-1023到1024
    * 所以0表示-1023
    * 所以读出时减，写入时加
  * 为什么指数不用补码？
    * 为了能够从左往右扫描即可确定两个浮点数的大小
    * 即除符号位以外只看指数部分即可以确定大小
      * 即指数部分谁先出现1谁更大
      * 如果指数部分完全相同，那么底数部分谁先出现1谁更大
  * 为什么要如此在意浮点大小对比的效率？
    * 因为浮点数更多时候是对比大小而非对比相等
      * 因为浮点数表示的不精确
        * 很难保证数学上相等的两个计算路径在程序中的计算结果也是完全相同的
          * 在程序中 a * b / c 的结果跟 a / c * b 有可能不相同的
          * 所以在程序中很少判断两个浮点数的相等
            * 而是判断它们在数轴上的距离，即求其差的绝对值看是否小于某个精度
              * Math.abs(a - b) < Number.EPLSION
  * 为什么不把底数的整数部分存储？
    * 因为底数的整数部分总是1
    * 效果就是二进制状态下的有效位数是53位
  * 正因为有效位数有53位，如果用这53位全部分表示整数
    * 即2的53次方，可以保证在这个范围内的整数运算的精确
    * 所以有一个常量Number.MAX_SAFE_INTEGER的值即为2的53减1
    * 大于这个范围的数不是不能表示，只是不保证完全精确
      * 大于这个范围无法表示浮点数，且整数也不是连续表示的
  * 因为总的有效数字只有53位
    * 所以如果整数部分使用的越多，小数部分就越小，反之亦然
    * 而数值越大，整数部分需要的有效位数就越多，而小数部分的有效位数就越少
      * 即数值越大，小数部分的精度就越低
    * 而数值越小，整数部分需要的有效位数就越少，而小数部分的有效位数就越多
      * 即数值越小，小数部分的精度就越高
  * IEEE754
    * 单精度浮点数 float   float32   f32
      * 使用4字节表示，其指数部分8bit，底数23bit
    * 双精度浮点数 double  float64   f64
      * 使用8字节表示，指数部分11bit，底数52bit
      var generate = function(numRows) {
      let result = []
      for(let i = 0; i < numRows.length; i++) {
        result.push([])
      }
      if(numRows == 1) {
        return [[1]]
      }
      if(numRows == 2) {
        return [[1],[1,1]]
      }
      if(numRows > 2) {
        result = [[1],[1,1]]
      }
      for(let i = 2; i < numRows; i++) {
        for(let j = 1; j < i; j++) {
          result[i][j] = result[i-1][j-1] + result[i-1][j]
        }
        result[i][0] = 1
        result[i][i] = 1
      }
      return result
  };
  ```


- ```
  value.x === value["x"]
    true
  ```

- 数组

  ```js
  数组是值的有序集合，即值在数组里是有序的
  a = [1,2,3,4,5,6,7]
  a.slice(3)
    [4,5,6,7]
  a.slice(3,6)
    [4,5,6]
  a.slice(3,-1)
    [4,5,6]
  浅拷贝 指针指向同一个地方
  
  //判断下标有没有在数组里，也可以是字符串
  5 in [1,2,3,4,5] 
   false
  '5' in [1,2,3,4,5,6] 
   true
  
  // includes
  a = [1,2,3,NaN]
  a.includes(1)
    true 
  a.includes(NaN)
    true 
  a.inexOf(NaN)
    -1
  
  // reverse
   修改自身
   
  // toString  join
   
  // splice
   a.splice(1,2,'a','b','c')
   
  
  ```

- 对象

  ```js
  对象是值得俱名集合，即值在对象里是有名字的
  in 二元运算符 ‘age’ in {age: 18}
  
  // key prop
  for(key in obj) {}
  
  //原始对象  premitive value
  s = "abc" 
  
  //包装对象  wrapped value
  Object(s)
  
  
  // ?.
  
  ```

- string

  ```js
  // 可以接多个参数
  "one two".indexOf('wo')

  // trimstart  trimend
  ‘  liu ’.trim()
  
  s = "abcdef"
  s.split('')
  s.anchor()
  s.startWith('ef')
  a.endsWith()
  s.padEnd(20)
  s.padStart(20,'abc')
  "0".repeat(3)
  s.substring(2,4)  //slice
   'cd'
  s.substr(1,3)
    'bcd'
  ```
  
- arguments

  ```js
  类数组对象
    么有数组上的方法
    有length 属性
    
  形参列表 剩余参数运算符 Rest params
  ...运算符 展开运算符 spread operator 
    var a = [1,2,3,4,56]
    Math.max(...a,...[3,77])  77
  
  Math.random()
  [0,1)
  ```
  
- apply

   ```js
  f.apply(obj,ary)
  
  obj.f = f 
  obj.f(...ary)
  ```

- 原型

  ```js
  // 任何对象都有__proto__属性，除了undefined,null
  // 函数的__proto__ === Function.prototype (Function是用来创建函数的)
  // 只有普通函数们自动有prototype 属性， (箭头函数没有)， 用于给到构造函数创建出来的实例当做原型
  Object.getPrototypeOf({}) === ({}).__proto__
  
  // 转换为字符串2
  2..toString() 
  // 总是转换为类似这种中括号的形式 "[object Number]" ，
  // 两个toString行为不一样,但都是通过this得到字符串
  Object.prototype.toString.call(2)
  "[object Number]" 
  
  // 函数继承自Function.prototype,数组继承自Array.prototype
  Array.__proto__  === Function.prototype
   
  // 创建一个以{a:1,b:2}为原型的对象
  obj = Object.create({a:1,b:2})
  
  //把obj的原型设置为{a:1}
  Object.setPrototypeOf(obj, {a:1})
  
  //构造函数创建若干个原型相同的对象，一个用new操作符创建出来的对象一般称作这个构造函数的实例
  new f() //当构造函数调用
  f() //当函数调用
  obj.f() //当方法调用
  f.call/apply() //call或apply直接调用
  
  function Rabbit(type){
    this.type = type 
  }
  killerRabbit = new Rabbit("killer")
  Object.prototype.toString.call(killerRabbit)
  //期待返回killerRabbit的构造函数 [object Rabbit]
  //然而 返回 [object Object]
  
  //可枚举属性 出现在 for in 里
  
  //自己创建不可枚举属性
  var obj = {}
  Object.defineProperty(obj, 'z', {
      value: 10,
    //enumerable: false, 是否可枚举
    //writable: false, 是否可修改
    //configurable: false, 是否可重新定义
  })
  
  //定义多个属性
  Object.defineProperties(obj, {
      a1: {
          value: 'xxx',
      },
      a2: {
          a2的属相描述符，
      }，
  })
  
  //判断对象自有属性，从Object.prototype的hasOwnProperty方法上读取，
  //因为当对象有个属性叫hasOwnProperty时，无法判断
  var hasOwn = Object.prototype.hasOwnProperty
  for(let key in obj){
      if(hasOwn.call(obj, key)) {
          console.log(key)
      }
  }
  
  //创建实例前，把构造函数写好
  function Rabbit(type) {
    this.type = type 
  }
  // 这种写法会好一些， 属性不可枚举
  Object.defineProperties(Rabbit.prototype, {
      dance: {
          value: function() {
              
          }
      }
  })
  
  Rabbit.prototype  = {
      constructor: Rabbit,
      dance() {
          
      },
      jump() {
          
      },
  }
  
  //创建一个原型为空的对象
  var map = Object.create(null)
  Object.setPrototypeOf(map, null)
  map.__proto__ = null
  
  //Object.create扩展
  obj3 = Object.create({a:1,b:2},{
      dance: {
          value: 1, // obj3自己还有这几个方法
      },
  })
  
  //Getter Setter 
    Object.defineProperty(obj, 'foo', {
        //value:,
        get: function(){},
        set: function(val){}
    })
  
  instanceof  
  //不能判断原始类型
  'str' instanceof String //false
  
  String.prototype === 'str'.__proto__
  //浏览器转换为
  String.prototype === new String('str').__proto__
  
  // new.target
  function f(){console.log(new.target)}
  new f()
  
  //with 语句
  a = {x:1,y:2,z:function(){return this}}
  with (a) {
      x + y
  }
  with (a) {
      z()
  }
  
  // use strict
  Object.preventExtensions(obj)
  Object.isSealed(obj)
  Object.freeze({x:1,y:2})
  
  
  ```

- try catch

  ```js
  //  语法错误 catch不到,可以用eval
  try {
      eval(`try {
        f(
        } catch(e) {
            console.log(111)
       }`)
  } catch(e){
      console.log(e)
  }
  
  // finally 
  try {
      
  } catch {
      
  } finally {
      //里面一定会执行
  } 
  ```

- JSON.stringify

  ```js
  // 接收第二个参数 
  ```

- sort

    ```js
   posWeight = {
     boss: 100,
     manager: 90,
     worker: 40
   }
   [{name: 'lizong', position: 'boss'},{name: 'xiaozhang', position: 'worker'}, {name: 'lijingli',position: 'manager'},{name: 'lizong', position: 'boss'},{name: 'xiaozhang', position: 'worker'}].sort((a,b) => posWeight[a.position] - posWeight[b.position])
   
   如果a-b是负数则a在前面;
   如果a-b是相等则字符串相同;
   如果a-b是正数则b在前面;
   function sortNumber(a,b){
       if(a<b){
         return -1;
       }else if(a==b){
         return 0;
       }else{
         return 1;
       }
   }
   const arr = ['z','b','a','d','e']
   arr.sort(sortNumber) 
   
   result = [{ li: 8 }, { ha: 12 }, { zh: 8 }]
   result.sort((a, b) => {
     if (b[Object.keys(b)[0]] - a[Object.keys(a)[0]] == 0) {
       return sortNumber(Object.keys(a)[0],Object.keys(b)[0])
     } else {
       return b[Object.keys(b)[0]] - a[Object.keys(a)[0]]
     }
   })
   [{ha: 12},{li: 8},{zh: 8}]
   
   ["apple", "apply", "appl", "app", "ap", "a",'z','b','ba'].sort((a,b) => a < b  ? -1 : (a == b ? 0 : 1))
   ```
   
- 正则表达式

   ```js
   1.创建方式
     1.直接量  
     var re1 = /abc/
     2.构造函数  
     var re2 = new RegExp("abc")
   2.反斜杠
     re = new RegExp('\n')  //接收到的是一个回车
     re = /\n/ //回车以转义的形式出现
   3. 表示 + 这个符号
     /eighteen\+/
   4.方法
     /abc/.test('abcdef')  //true 
     /abc/.exec('abcdef')  //匹配第一次出现的 abc
   
     //把若干个字符放进中括号里 匹配任一个字符 加上 oo
     /[abc]oo/.test('lioo')
     /[abc]oo/.exec('lioo')
      
     // - 表示从0到9的任一个数字(升序)
     /[0-9]/
     // 大小写字母
     /a-zA-Z/
   
     //快捷方式
     /\d/ 代表 [0 - 9]
     /\w/ 代表 [0 - 9a-zA-Z] 外加一个下滑线 ‘_’
     /\s/ 匹配任意一个空白符
     /\s/.test('\n') /\s/.test('\t')
   
     \D  取反
     \W  取反
     \S  取反
     . 匹配任意符号除了换行符
     /./.test('\n')  //false
     把 . 放在[]里表示.自己
     /[.]/  /\./
   
     // ^ 脱字符 取反
     /[^01]/ 找到不是0 或不是1的就返回 true 
     /[^]/ 空集取反 所以匹配任意符号 
     /[a^]/ 不出现在中括号开始，就代表它自己 ^
         
      //+ 重复一次或多次 >. 1  先匹配尽量多的符合条件的符号
      //* 重复零次一次或多次  >> 0
      //? 重复零次或一次 0,1
         
      // +? 非贪婪匹配
         
      //精确重复次数
      /\d{4}/
      //最少两次，最多四次
      /\d{2,4}/ 
      //大于等于5次
      /\d{5,}/
          
      //多个字符 重复
      /boo+(hoo)+/
      
      i 不区分大小写 
      
      exec没匹配到返回 null
          
      match 是字符串上的方法
      re.exec(str) == str.match(re)
      "one two 100".match(/\d+/)
      //g
          
      //括号的作用 拿到每一部分 分组捕获    
      'boohoohoooohoooo'.match(/boo+(hoo+)+/)
          
       // ^ 匹配字符串最前面引号的那个位置
       /^foo/.exec('fooliuhai foo') '^'匹配的是foo之前的那个位置
       // $ 匹配字符串的结束位置
       /^\d+$/ 匹配完全由数字组成的字符串
       // \b 匹配的是字符边界 
        需要注意的是单词边界符可以是字符串的开始或结束位置，也可以是任意一个单词字符与非单词字符的中间位置
       /\bcat\b/.test(' cat oo') //true 
       /\bcat\b/.test('cat')
       /\bcat\b/.test('cat oo') //true
       /\bcat\b/.test(' catoo')  //false
          
   零宽断言扩展了^ $ \b这几个匹配符
   它匹配一个位置，可以要求某个位置满足或不满足特定条件。
   分为四种情况：
     positive look ahead assition
       要求某个位置的右边满足某种条件（右边遇到某种模式）
       (?=expr) 匹配一个位置，要求其右边要出现expr的匹配
     negative look ahead assition
       要求某个位置的右边不满足某种条件（右边不能遇到某种模式）
       (?!expr)
     positive look behand assition
       要求某个位置的左边满足某种条件（右边遇到某种模式）
       (?<=expr)
     negative look behand assition
       要求某个位置的左边不满足某种条件（右边不能遇到某种模式）
       (?<!expr)
   
   \b == (?=\w)(?<=\W)|(?=\W)(?<=\w)|^|$
   ^  == (?<![^])
   $  == (?![^])
          
     /\d+ (pig|chicken|cow)s?/
     /123 (abc|bar)/.exec('123 abc')
     /123 (abc|bar)/.exec('123 bar ')
     /123 abc|bar/.exec('123 bar ')
          
     /(?:foo)/
     第一对括号不再被捕获并放入结果中
          
     /(?<year>\d\d\d\d))-(?<month>\d\d)/
     [groups: {year: "2020"}]
     
     //replace  /g 所有的匹配都替换掉
     'foobar'.replace(/ba/g, '##')
     'foobafoobzd'.replace(/oo(.)(.)/g, 'oo$2$1')
   
     // 字符串上的 search方法
   ```

   

- class 语法

   ```js
  class A extends Array {
      #a = 0
      b = []
      c = new Map()
      
      constructor(){
          super()
      }
      getA() {
          return this.#a
      }
  }
  A.prototype.__proto === Array.prototype
  ```


- 模板字符串

  ```js
  var x = 3 
  a = `liuhai${x*x}zhou` 
  
  tagged string
  function f(...args){}
  f`abc${1}bb${2}`
  
  String.raw`\\\\` 
  返回未被转义的结果 "\\\\"
  ```


- DOM

     ```js
  // document.createElement('a')
  // document.createTextNode('hello')
  
  //元素上没有此方法，document上才有
  document.getElementById('div')
  
  //一个结点在文档中只能出现一次
  
  //复制一个结点 
  $0.cloneNode()
  $0.cloneNode(true) // 深度复制
  
  parentNOde.removeChild(childNode)
  parentNode.appendChild(childNode)
  parentNode.removeChild(childNode)
  parentNode.appendChild(childNode)
  parentNode.insertBsfore(newNode, baseNode)
  parentNode.replaceChild(newNode, oldNode)
  prepend
  
  append('liu','hai','zhou')
  appendChild 只能传结点
  children不包含文本结点
  
  //合并$0中连续的文本结点，深层次
  $0.normalize()
  
  getAttribute / setAttribute / value
  el.getAttribute('class')
  
  $0.dataset.xxx
  
  $0.className
  $0.id
  $0.htmlFor
  <label for="foo"></label> $0.htmlFor
  
  //选择器
  document.querySelectAll('div ul li')
  documetn.querySelectAll(':hover') 
  可以选择一部分 伪类
  不能选择伪元素
  返回静态集合，不会动态更新
  
  //切换类名
  $0.classList.toggle('foo')
  replace
  
  //
  $0.innerText == $0.outerText
  $0.textContent(建议使用)
  
  $0.innerHTML 不包含标签自己
  $0.outerHTML
  ```

- Event 

  ```js
  //解绑失败，因为第一行的 function aa(){} 是表达式，只能用在函数内部，function不是打头
  $0.addEventListener('click', function aa(){
      console.log('xx')
  })
  $0.removeEventListener('click', aa)
  
  //EventObject
   'mousedown' e.which 1 2 3 左中右 无法展示组合键
               e.buttons 1 4 2
  // 函数作为谁的事件 this就是谁（非箭头函数）
  // 不同的事件 不同的事件对象
  e.stopPrppagation() // 阻止该元素向上冒泡，该元素自身后续绑定的如click事件还是会执行
  e.stopImmediatePropagation() //阻止自己后续及向上传播，自身后面的代码会继续执行，除了死循环，报错，return等 
  
  //capture 捕获阶段
    //如何注册捕获阶段
    $0.addEventListener('click',function(){
        alert(6)
    }, true) 捕获阶段的事件处理函数
  
    //事件的执行顺序
    从捕获到目标到冒泡
    target目标阶段不区分捕获 冒泡，按注册顺序执行
  
    e.target 是触发事件执行的元素，
    即使该元素没绑定事件，但父元素绑了，点击该元素还是可以通过父元素内e.target找到此元素
  
    // 事件代理 不用管里面的元素增加或减少 
    把事件绑在父元素上 通过e.target判断
    e.currentTarget === this
  
    var btns = document.querySelectAll('button')
    for(let i = 0; i < btns.length; i++){
      //循环体运行多少次 i就有多少个
      btns[i].addEventListener('click', function(e){
        console.log(i + 1) 
      })
    }
    // btns[i]的i 不在事件函数里
    for(var i = 0; i < btns.length; i++){
      let j = i
      btns[i].addEventListener('click', function(e){
        console.log(j + 1) 
      })
    }
  
    //不用 let
    想要每个作用域里都有一个函数及变量
    for(var i = 0; i < btns.length; i++){
     (function(i) {
        btns[i].addEventListener('click', function(e){
        console.log(i + 1) 
       })  
     })(i)
    }
  
    // 减少函数创建次数
    function loopBody(i){
      btns[i].addEventListener('click', function(e){
        console.log(i + 1) 
       })  
    }
    for(var i = 0; i < btns.length; i++){
       loopBody(i)
    }
  
    // 默认行为
    元素的绑定事件发生在默认行为之前
    e.preventDefault() 阻止默认行为
  
    // 鼠标右键事件
    contextmenu 
  
    //先发生滚动 再运行事件
     window.addEventListener('scroll',function(){
         console.log(3)
         event.preventDefault()
     })
    
    //键盘事件 一般绑在window上 （只会在有焦点的元素上触发）
    //按住不松手 会一直触发keypress
     keydown 
     keyup 
     keypress ctrl alt shift等不触发该事件
     
     //鼠标点击事件
     css point-events: none;
     mousedown
     mouseup
     click
     
     //鼠标指针的位置
     // pageX pageY  相对于页面
     //clientX clientY 相对于窗口
     //offsetX offsetY  相对于元素 （偏移量）
     //screenX screenY  相对于屏幕
     
     //鼠标移入移出
     mouseout 
     mouseover
     // 不冒泡 从父元素enter到子元素 ，子元素不冒泡，父元素不leave
     mouseenter
     mouseleave
     
     //scroll 滚动事件
     无法阻止scroll事件的默认行为
     
     //滚轮事件  与 被动事件
     mousewheel 
     有些事件的默认行为会影响到用户体验，从用户角度希望默认行为是即刻触发的
     但是浏览器需要先调用事件处理函数确认事件处理函数没有调用 preventDefault后，才能执行默认行为
     但执行函数需要时间，就会让默认行为发生的晚一些，用户会感觉到延迟。
     更多时候处理函数并没有调用 preventDefault,但浏览器还是要等到函数运行完才能滚动
     于是有了passive事件，在事件绑定时，就告诉浏览器，该事件处理函数不会调用preventDefault
     这样 浏览器可以在运行函数的同时，就直接开始默认行为的执行，消除了这个延迟
      
     
     window.addEventListener('mousewheel',function(e){}, {
         passive: true // 本事件处理函数是否会调用 e.preventDefault() true 代表不会阻止默认行为发生
         // 即使函数没有运行完，浏览器也可以执行默认行为，如滚轮等
     })
  
     // 阻止滚轮发生
     window.addEventListener('mousewheel', e => e.preventDefault(), {passive: false})
    //捕获 
    userCapture: true 
    //绑定单次事件 
    once :true
  
  // document.querySelectorAll('[id]')
  // document.querySelector('a[id="result_logo"]')
  // document.querySelector('a#result_logo')
  // document.querySelector('a[href="/"]')
  
  // 聚焦事件 focus blur 不冒泡 但能被捕获到
     focusin / focusout 事件可冒泡
     
   //load 加载事件
     完成加载 
     window.onload是在页面中所有的资源加载完成的时候触发的 包括图片 脚本 css等
        dom解析完成
        图片加载完成
        js执行完成
     
     代码遇到script就立即解析，后面暂停
     
     //但是图片有些比较大，加载完成需要好几秒，而且我们一般的初始化操作都不会涉及到图片，
     //一般是绑事件，所以只需DOM构建完成就可以，
     document.addEvenListener('DOMContentLoaded', () => {
         //DOM构建完成即可，
         //有的浏览器不支持 有另外一个事件 readystatechange
         // document.readyState == 'complete' 表示DOM解析完成
     })
  
    script标签的load事件 在src文件加载好 运行之后才触发
    //js 一般放在后面
    js的下载和执行都阻碍了浏览器后面的解析(把html源代码解析成dom树，然后画出来)，页面会白屏
    // <script defer async src="aaa.js" ></script>
    defer async 不会阻止页面解析
    区别
    defer 的script标签按顺序执行  在dom解析完成之后执行，在domready之前
    async 谁先下载完 谁执行
    
    css不会阻止页面执行
    
    //beforeunload 页面关闭之前触发（需与页面有交互）
    
    script 标签的 onerror 事件在src文件加载失败触发
    window.onerror 在页面里js代码出错时触发
    
    trigger event js
    window.dispatchEvent(new Event('scroll'))
  
    create the event
    const event = document.createEvent('Event')
    event.initEvent('build', true, true)
    elem.addEventListener('build', function(e){
        
    }, false)
    elem.dispatchEvent(event)
  
    // 两个线程之间可以通信，不能共享内存
    复制一个对象 可以postMessage到一个worker，让浏览器复制
    worker内不能访问dom
    
    setTimeout 
    clearTimeout
    setInterVal
    clearInterVal
    
    (()=> 2).length
  
    window.onresize
    window.onhashchange
    
  // 移动端touch事件
  ```

- debounce (防抖)   throttle（节流）

     ```js
     //把执行函数的频率降低的两种形式
     操作完全停止以后 再延迟一会再响应 debounce
     function debounce(f,time){
         var id = null
         return function(...args){
             clearTimeout(id)
             id = setTimeout(() => {
            f.call(this, ...args)
             }, time)
         }
     }
     
     input.addEventListener('keyup', debounce(e => {
         console.log(e.target.value.length)
     }, 1000))
     
     lodash 
     f = _.debounce(function(){
       console.log(1)
     }, 1000)
     f = _.debounce(function(){
       console.log(1)
     }, 1000,{leading: true}) // 第一次运行就调用，后续停下超过时间再调用
     
     f = _.debounce(function(){
       console.log(1)
     }, 1000,{leading: true, trailing: false}) 
     //trailing 停下1s钟以后 要不要运行 
     
     降低频率 throttle
     throtle leading trailing 都是默认为 true  
     trailing 最后一次执行完，后面又有一次，离它太近，我还要不要执行 
     
     debounce leading false , trailing: true
     
     function throttle(f, time){
         var scheduled = false
         var lastArgs = null
         return function(...args){
             lastArgs = args
             if(!scheduled){
                 scheduled = true 
                 setTimeout(() => {
                     scheduled = false
                     f.call(this,...lastArgs)
                 }, time)
             }
         }
     }
     
     ```
     
- BOM 

     ```js
     location.href = xxx
     location.assign(xx)
     location = xxx
     location.replace(xxx) //回退不了 
     
     location.reload()
     
     history.pushState(null，‘’，‘/foo’)  //页面不刷新
     history.popState()
     
     navigator.userAgent
     ```

- ```js
     decodeURIComponent('%e6%88%91')
     decodeURIComponent('name=li&msg=%e6%88%91')
     encodeURIComponent
     ```


- HTTP

  ```js
  // get 与 post 请求的区别
  
  // 同源策略 same origin policy (简称跨域)
    页面只能和自己的服务器通信
    协议 域名 端口号 有一个不一样 就叫跨域
  
  // 跨域方法
     响应头添加 Access-Control-Allow-Origin: * 
         
   github网站禁止自己网站访问其他站点
   // 内容安全策略 content-secruity-policy 极大提升站点安全性， 浏览器请求一个页面时，且页面内容为HTML，,并展示出来，响应体上有Content-s-p
   // 对html页面(即里面的js的行为生效)，不是对css或js（页面里使用的资源）生效
  default-src 'none'
  
  base-uri 'self'
  
  block-all-mixed-content 不能加载混合内容，即https页面加载http内容
  
  connect-src 'self' uploads.github.com www.githubstatus.com collector.githubapp.com api.github.com github-cloud.s3.amazonaws.com github-production-repository-file-5c1aeb.s3.amazonaws.com github-production-upload-manifest-file-7fdce7.s3.amazonaws.com github-production-user-asset-6210df.s3.amazonaws.com cdn.optimizely.com logx.optimizely.com/v1/events wss://alive.github.com github.githubassets.com
    可以连接哪些服务器
  
  font-src github.githubassets.com 可以加载来自哪里的字体
  
  form-action 'self' github.com gist.github.com 表单可以提交到哪里
  
  frame-ancestors 'none' 可以有谁做为本页面的frame祖先，none表示没有，即这个页面不能放入任何页面的iframe里
  
  frame-src render.githubusercontent.com 可以嵌套哪里的页面在自己的frame里
  
  img-src 'self' data: github.githubassets.com identicons.github.com collector.githubapp.com github-cloud.s3.amazonaws.com *.githubusercontent.com customer-stories-feed.github.com spotlights-feed.github.com
  
  manifest-src 'self'
  
  media-src github.githubassets.com
  
  script-src github.githubassets.com
  
  style-src 'unsafe-inline' github.githubassets.com
  
  worker-src github.com/socket-worker-5029ae85.js gist.github.com/socket-worker-5029ae85.js
   
  
  
  // 封装ajax 
  function get(url, f, g){
      var xhr = new XMLHttpRequest()
      xhr.open('GET', url)
      // onreadystatechange()的定义是只要返回的状态码只要变化时就回调一次函数，而onload只有状态码为4时才能回调一次函数。
      xhr.onload = function (){
          if(xhr.status < 400){
              f(xhr.responseText)
          } else {
              g(xhr.responseText)
          }
      }
      
      xhr.onerror = function(e) {
          g(e)
      }
      
      xhr.send()
  }
  
  <button onclick="add()"></button>
  浏览器根据这个onclick="add()"属性的字符串构造出了一个函数，
  把 add()当作这个函数的函数体，构造出来的这个函数就是这个button结点的onclick属性
  button.onclick = function onclick(event){
      add()
      //可以用this
  }
  
  配置referer请求头
  <meta name="referrer" content="origin" />
   // 设定当前页面如何发送referrer请求头 ,origin表示只发页面的origin，即端口及之前的内容
      
   // Referer是请求头，表示这个请求是哪个页面发出的。服务器可以读取到。
    防盗链
    https://moz.com/blog/meta-referrer-tag
  
  ```

- http请求首部

  ```js
   a.com页面https://www.a.com/search向b.com服务器https://www.b.com/foo/bar/baz发送请求
  
    get('https://www.b.com/foo/bar/baz')
  
    GET /foo/bar/baz HTTP/1.1
    Host: www.b.com // 用来告诉服务器，浏览器是通过什么域名来连接到服务器的，带端口号，可用此特性来实现同一个服务器服务多个网站，coding/github pages就是这么做的
    Refer: https://www.a.com/search 表示这个请求是哪个页面发出来的（这个请求的响应将要被哪个页面使用）
    User-Agent: .... //浏览器表示，可以用js通过navigator.userAgent读到
    Accept: text/html;text/plain; // 浏览器能接收什么类型的响应
    Accept-Language: en-us; zh-cn; //给用户看的语言
    Accept-Encoding: gzip, deflate, br //压缩算法
  
    响应相关首部
    Content-Length : 配合Connection:keep-alive可以实现Http pipe line (请求响应都有，响应体的长度)
    Content-Type: type/substype; charset=utf-8 （请求或响应体的类型）
    Date: Thu, 18 Jul 2017... (服务器给你响应的时间)
    Expires: ISO Time String 本资源的过期时间，过期之前，浏览器可以选择完全不发请求，直接使用本地缓存的版本。过后必须发请求
    Connection: keep-alive //希望服务器不要关闭连接 （连接的复用需要配合Content-Length 来确定下一次的连接）
    If-None-Match（请求） /Etag(请求)
    If-Modified-Since(请求)/ Last-Modified(响应)：IOS Time String
    Cache-Control
  
    // 根据时间
    =================================
  
    GET /resource HTTP/1.1
    =================================
  
    HTTP/1.1 200 OK
    Last-Modified: 2020-09-30
  
    content...........
    =================================
  
    .
    .
    .
    .
    .
  
    .
    =================================
  
    GET /resource HTTP/1.1
  
    If-Modified-Since: 2020-09-30
    =================================
  
    HTTP/1.1 304 Not Modified（协商成功）
    =================================
  
    HTTP/1.1 200 OK（未协商成功）
    Last-Modified: 2020-10-02
  
    new content...........
  
    // 
    =================================
  
    GET /resource HTTP/1.1
    =================================
  
    HTTP/1.1 200 OK
    ETag: 由内容计算出的hash值
  
    content...........
    =================================
  
    .
    .
    .
    .
    .
  
    .
    =================================
  
    GET /resource HTTP/1.1
  
    If-None-Match: hash (如果资源不匹配hash值)
    =================================
  
    HTTP/1.1 304 Not Modified（协商成功）
    =================================
  
    HTTP/1.1 200 OK（未协商成功）
    ETag: 新内容计算出的新hash值
  
    new content...........
    =================================
  
    // Expires: 过期的具体时间点
    // cache-control: maxage-xxx: 过多久过期 （请求或响应头都可以使用，用来控制或选择缓存策略）
     可以用这一对实现强缓存，即需要这个资源时，可以不发请求
  
    cache-control: no-cache; // 响应头，意为让浏览器不缓存这个资源
    cache-control: max-stale=86400 (请求头，)
  
  
  // CORS Cross-Origin Resource Sharing
  非简单请求会发送预检请求（OPTIONS）
  跟cors相关的请求头
    access-control-allow-methods: get, search, mkcol
    access-control-allow-origin: *
    access-control-allow-headers: Origin, X-Requested-with, Content-Type, Accept
    access-control-max-age: 86400,预检请求的有效期是一天，一天之内请求都是可以的，不用再发预检请求
  
  跨域基本是限制ajax这种请求，向图片，css加载是不限制的（这种形式加载的资源无法读到完整的内容，拿不到css文件的源代码，图片的像素点）ajax是能够拿到原始内容， 这是一种信任关系的转换，ajax是服务器信任我，
  ajax请求不能发成功的原因主要是可能泄漏用户隐私
  
  //jsonp
  加载了script标签，js运行，然后我页面之前声明好了一个函数（由服务器返回了一段能调用客户端的代码）
  script get请求
  
  function jsonp(url, f){
      var functionName = 'JSONP_CALLBACK_' + Date.now()
      var script = document.createElement('script')
      script.src = url + '&callback=' + functionName
      window[functionName] = f 
      document.head.appendChild(script)
  }
  
  CSP （限制加载恶意代码，只能加载自己服务器的js,无法把隐私信息传出去）
  
  XSS 跨站脚本攻击（影响到整个网站）
  Cross Site Script(自己的网站没有转义,有人运行了恶意的js代码,读取了隐私，发往其他的服务器， lodash里的escape可以转义)
  所以有了csp （只允许页面往自己服务器发）
  
  host头与referer头
   host头 发的是当前请求的资源的名称
   referer 你在哪个页面请求的资源或者从哪个页面点击的链接
   自己服务器的响应体设置 Referer-Policy: none; 盗链别人的图片
   或者 meta标签
   
  // 跨站请求伪造 cross site request forgery
   b网站带上你的认证信息给你的网站发送请求，
   //解决方案 让浏览器不带这个认证信息
  
  ```

  

- 表单域

  ```js
  // 文本框的change事件只会在光标移出输入框后才触发，如果想在输入的时候就触发，可以使用keydown,keyup,keypress,input事件
  
  document.all == document.querySelectorAll('*')
  document.forms ==  document.querySelectorAll('form')
  
  // disabled 禁止
  [disabled], :disabled {
      color: grey;
      cursor: not-allowed;
  }
  
  ```

- ```js
  
  - // 读取文件内容
      var reader = new FileReader()
      reader.addEventListener('load', function(){
          console.log(reader.result.slice(0,20))
      })
      reader.readAsText(file)
  
      // select
      select2 choosen
      
    // localStorage
      // 浏览器限制了存在ls里数据的大小，一般是5M
      sessionStorage 在每次会话结束之后（浏览器关闭后）会清空
      
    // 双击打开的文件都是存在同一个localStorage
      
    window.onstorage 会在localStorage发生变化的时候触发
    window.onhashchange会在location.hash发生变化时触发
    window.onresize会在窗口发生变化时触发
  
  ```

- 生成器函数

  ```js
  // 生成器函数
  function * fibbs(n) {
      var a = 0
      var b = 1
      var count = 0
      
      while(count++ <　n) {
          b = b + a 
          a = b - a
          yield a
          var c = 1
      }
  }
  //生成器函数的调用 -> 返回一个生成器
  fibb10 = fibbs(10) // 此时生成器函数还未运行
  
  fibb10.next() // 生成器的调用 ， 第一次运行到yield语句截止,yield语句不是return语句，它是让 值a 生成出去，并让自己的函数暂停
  
  fibb10.next(987) // 此时让yield语句继续执行 ，并把传入的参数返回（如果有个变量接着yield a）
  
  {value: xxx, done: true} 
  // done第一次为真的时候 value为函数的返回值，如果函数没有返回值 则为undefined
  
  for(var x of fibbs(10)){console.log(x )}
  [...fibbs(10)]
  
  生成器对象还有 throw return方法，都可以接参数
  
  var a = [1,2,3,4]
  // for of 语句的行为 把a转换成一个生成器
  for(var x of a[Symbol.iterator]) {
    console.log(x)
  }
  
  //能够迭代的都可以读出这个属性
  a[Symbol.iterator]() // 有next
  
  //Symblo js的基本数据类型 原始类型
  typeof Symbol.iterator
  
  //每次返回不同的symbol,具有唯一性 
  a = Symblo()
  b = Symbol()
  a == b //false
  
  // symbol可以作为对象的key (实现私有属性)
  
  d = Symbol()
  obj = {}
  obj[d] = 888
  
  // 私有属性， 不会参与自动类型转换为字符串
  String(d) + 'hello'
  d.toString()
  
  // 构造相同symbol
  Symbol.for('xxxyyy') === Symblo.for('xxxyyy')
  
  ```

- ```js
  所有能for of 的对象都有 [1,2,3][Symbol.iterator]()
    [...document.all] //当作可迭代对象
  
    读取一个东西的[Symbol.iterator] 并调用它，能够得到生成器，这个东西就称为可迭代对象
  
    能用 ...的不一定能用 for of
    a = {x:1,y:2}
    b = {
        ...a, // 在对象里用 ... 是当作一个正常的对象展开
        z: 888
    }
  
    Number.prototype[Symbol.iterator] = function *(){
       for(let i = 0; i < this; i++){
         yield i 
      }
    }
    for(let i of 9){
        console.log(i)
    }
  
    function * f() {
        yield 1
        yield 2
        yield 3
    }
    [...f()]
  
  
    function * f() {
        yield 1
        yield *g()
        yield 3
        yield *[1,2,3,4]
    }
    function * g(){
        yield 'a'
        yield 'b'
    }
    [...f()]
  
    class Person {
        *[Symbol.iterator](){
            yield 2
            yield 3
        }
    }
  ```

- ```js
  (function f(){})
    ƒ f(){}
  function f(){}
    undefined
  
  // function f(){}() => undefined()  报错 
  // function f(){}; ()   function语句结束了，括号报错
  ```

-  ```js
  模块化
  //把代码拆分到不同的文件并放入不同的文件夹
  js里就是把代码按照约定放进别的文件里，然后作为函数体加载进来，函数体里干的是修改传给他的对象，最终返回。
  传给它的原因是模块函数还未运行完，我们就知道它的运行结果,而不是等到return
  
  // 在浏览器用script标签加载很多模块是不可行的
  JS语言里没有模块系统
  为什么要模块系统？
    因为模块化开发便于维护，也便于解耦
      不同功能模块的代码放在不同的文件及文件夹里
      甚至放在不同的软件包里
  
  实现好的模块系统在浏览器中实际上不可用：
    因为浏览器如果还一个一个加载模块文件，就太慢了
      因为从网络上加载大量的小文件总体速度是很慢的
      而在所有模块加载完成之前，模块系统是不会开始执行入口模块的代码的，进而相当于不执行任何模块代码
        也就是页面中的功能都不可用
        视模块数量、依赖关系以及网络速度，这个不可用的时间可能很久，甚至可能长达10秒以上
    所以需要将所有的模块打包成一整个文件
      因为一个10M的文件比1000个10k的文件下载速度快。
      打包原理即为浏览器中异步加载模块的基本原理：
        从入口文件开始，加载并缓存所有模块的依赖，等所有的依赖都加载完成的时候，构建好的对象其实就是打包结果的一部分，将其跟require函数一起输出为一个文件，即为打包结果。
  
        
   // 解耦
  ```

- es-module

  ```js
  export default {z:1,y:2} //默认导出
  export var a = 8 //俱名导出的两种形式，声明时直接导出
  var b = 3 
  var c = 4 
  export {b,c} // 俱名导出的两种形式 ，导出已经声明好的内容，则需要加 {}
  
  //如何引用
  import valueb from './file.js' //导入file.js的默认导出
  import {a,b,c} from './file.js' //导入file.js的俱名导出， 名字要对应
  // 一次性导入
  import valueb, {a,b,c} from './file.js'
  
  es modules
  
  每个模块有自己的作用域内执行
  通过import创建的变量相当于const创建，所以不能单独放在等号左边
  通过import创建的变量会跟其引入的来源绑定，来源变量发生变化，引入的变量也发生变化
  
  导入其它模块的默认导出
  import xxx from './xxx.js'
  导入俱名导出
  import { a, b as bb , c as cc} from './x.js'
  同时导入默认及俱名导出
  import a, { b, c, d } from './mod.js'
  创建默认导出
  export default [1, 2, 3, 4]
  创建俱名导出
  export var a = 1
  export var b = 2
  var c = 3
  var d = 4
  export { c, d }
  
  import * as foo from './foo.js'//将foo.js的所有导出导入到foo变量
  foo.default 为默认导出
  foo.xxx 为俱名导出
  且都为getter setter，但set是无效的
  
  export * from './a.js'//将a.js的所有导出从当前文件再导出
  export * from './b.js'
  import xx from yy + '.js'
  
  所有的导入导出语句都必须出现在模块文件的最外层，即不能放入任何代码块，如if，函数，循环
  所有导入的模块名称必须是静态的，不能有任何运算
  
  ```


- Promise

  ```js
  Promise.resolve(Promise.resolve(5))
  Promise.resolve(Promise.reject(5))
  Promise.reject(Promise.resolve(5))
  Promise.reject(Promise.reject(5))
  
  
  p = Promise.race([p1, p2, p3]) // p取 数组里最先确定状态的promise的状态
  Promise.any //返回第一个成功的值
  Promise.all([p1,p2,p3]).then(ary => {}) //如果三个promise都返回成功，ary为包含成功的结果的数组，如果有失败的，返回的是以第一个失败的promise为原因的promise
  Promise.allSettled // 并不要求所有的promise都成功 ，返回的是数组里包着对象
  function all(promises){
      return new Promise(function(resolve,reject){
          let ary = []
          let completed = 0
          if(promises.length == 0){
              return resolve([])
          }
          for(let i = 0; i < promises.length; i++){
              promises[i].then(val => {
                ary[i] = val
                  completed++
                  if(completed == promises.length){
                      resolve(ary)
                  }
              }, reason => {
                  reject(reason)
              })
          }
      })
  }
  
  p.finall(function(){}) // finall 不接参，状态取决于p的状态，和函数里的return无关
  
  
  
  // async function  本质上是一个生成器函数
  async function foo(){
      console.log(1)
      var y = await 2
      console.log(y)
  }
  foo()
  
  console.log(3)
  await后面接的转换为promise
  
  var a = async () => {
      console.log(1)
      var y = await 2
      console.log(y)
  }
  a().then(val => console.log(val))
  
  
  //异步生成器函数
  async function *foo(){
      console.log(1)
      var x = await setTimeout(() => {console.log(2)},1000)
      yield x
      console.log(x)
  }
  generator = foo()
  g = generator.next()
  g,then(obj => console.log(obj))
  
  
  async function bar(){
      let generator = foo()
      for await(let x of generator ){
          console.log(x)
      }
  }
  bar()
  
  ```

