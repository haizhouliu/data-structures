* ```html
  <!-- code标签包裹代码块，与pre搭配使用 -->
  <pre>
    <code>
      function a(){
  
      }
    </code>
  </pre>
  
  <h1 contenteditable>可编辑属性</h1>
  
  <!-- 自定义进度条， html5新增标签-->
  <progress value="90" max="150"></progress>
  
  <!-- 已废弃 -->
  <marquee>跑马灯</marquee>
  
  <!-- 不设置 tabindex 默认值无穷大,
       name属性在提交表单时会显示在地址栏中,
       tabindex让元素获取焦点 -->
  <input type="text" name="age" tabindex=1/>  
  
  <!-- 缩写 -->
  <abbr title="People's Republic of China">PRC</abbr>
  
  <!-- headergroup -->
  <hgroup>
      <h1>三体主标题</h1>
      <h2>一步人类文明史副标题</h2>
  </hgroup>
  ```
* 浏览器自动请求网站icon

  - https://www.zhihu.com/favicon.ico
  - https://www.baidu.com/favicon.ico

* ```html
  <!-- 点击京东，浏览器会新打开一个标签名为foobar的京东网页，再点击小米，之前的京东网页变为小米网页(window.name) -->
    <a target="foobar" href="https://www.jd.com">京东</a>
    <a target="foobar" href="https://www.mi.com">小米</a>
    
  <!-- _blank是一个特殊词,还有_self _parent _top -->
    <a target="_blank" href="https://www.mi.com">小米</a>
    <a target="_blank" href="https://www.mi.com">小米</a>
  ```

- ```html
  <!-- Emmet语法 -->
  ul>li*3.foo>a[href=#]{item$}*4
  $$*16
  ```


- ```html
  <!-- 假设文件对应地址栏网址为 http://127.0.0.1:5500/miao/index.html
  a标签链接地址以 // 开头，点击后网址 http://abc/.
  以 / 开头，点击后网址 http://127.0.0.1:5500/abc. 替换掉第一个/后面的内容
  以 相对地址 开头，点击后网址 http://127.0.0.1:5500/miao/foo/bar/a.html. 替换掉最后一个/后面的内容
  -->
  <a href="//abc">点击</a>
  <a href="/abc">点击</a>
  <a href="foo/bar/a.html">点击</a>
  ```

- ```html
  <!-- 紧跟在 caption 标签后面的 第一个col表示第一列 -->
  <table border=1>
      <caption>表格标题</caption>
      <col bgcolor="red">
      <col bgcolor="violet" span=2>
      <thead></thead>
      <tbody></tbody>
  </table>
  ```

- ```html
  <!--  设置name属性后,点击a标签，窗口在iframe窗口打开 -->
  <a href="https://www.hao123.com" target="frame1">hao123</a>
  <iframe 
      src="https://www.baidu.com" 
      frameborder="1"
      name="frame1"
  >
    <p>您的浏览器不支持框架</p>
  </iframe>
  
  <!-- iframe标签正常使用时，内部本身没东西，当浏览器识别iframe后,不会把p标签内容展示出来，所以把p标签放在里面. frameset标签内需要展示东西，所以把noframes放在标签外面  -->
    <frameset cols="50%, 50%">
      <frame src="https://www.baidu.com/" />
      <frameset rows="50%, 50%">
        <frame src="https://www.hao123.com/" />
        <frame src="https://v.qq.com/">
      </frameset>
    </frameset>
    <noframes>您的浏览器不支持框架</noframes>
  
  <!-- 当浏览器禁用js后，显示noscript标签内容 -->
  <script>
    var a = 8
  </script>
  <noscript>your browser dont support javascript</noscript>
  ```



