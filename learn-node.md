- fs模块

  ```js
  //promise版本
  var fsp = require('fs').promises
  fsp.readFile('a.txt').then(data => {
      
  },err => {
      
  })
  //读取文件
  fs.readFile('./cat.sjon', 'utf8', (err,data) => {
      console.log(data)
  })
  //写入文件
  fs.writeFile('ace.txt', 'content', err => console.log(
  err))
  //读取当前文件夹内的文件目录
  fs.readdir('.', (err, list) => console.log(list))
  //读取具体文件的信息
  fs.stat('ace.txt', (err,data) => {
      console.log(data)
  })
  
  ```

- util模块

  ```js
  var util = require('util')
  var readFileP = util.promisify(fs.readFile)
  var readFile = util.callbackify(readFileP)
  ```

- path模块

  ```js
  path.basename('foo/bar/baz.png')
  path.delimiter // 路径列表的分隔符
  process.env //环境变量
  path.dirname('foo/bar/baz/baa.png')  //返回dir
  path.extname('foo/bar/baz/baa.jpg') //返回扩展名
  
  path.join('foo/bar', './../baz') //路径化简
  
  path.parse('c:/foo/bar/baz/baa.jpg') //返回一个对象， 与format相对应
  
  path.relative('foo/bar/baz/baa', '/foo/bcc/abc') //计算出两个目标路径的相对关系 "../../../bcc/abc"
  path.resolve(process.cwd(),'/foo/bar/baz/baa', '../../../bcc/abz')
  path.resolve()
  path.resolve('/aaa/bbb','/ccc','./././foo/bar')
  path.resolve('/aaa/bbb','ccc')
  
  ```

- event

  ```js
  const EventEmitter = require('events')
  var a = new EventEmitter() //创建一个事件监听触发器
  a.on('foo', function(a,b){
      console.log(a * b)
  })
a.emit('foo',5,6)
  
  //浏览器里的
  et = new EventTarget()
  et.addEventListener('foo',function(e){
      console.log(e)
  })
  et.dispatchEvent(new Event('foo'))
  ```
  
  
  
- node调试

  ```js
  node --inspect-brk test.js
  
  //调试多个
  node --inspect-brk=9999 test2.js
  ```

  