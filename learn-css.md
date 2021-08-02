- css 语法

- auto | inherit 多选一

  - a || b a 和 b 都得写, 顺序无所谓

- **css 选择器**

  - **div p** div 和 p 是**后代关系**,不管包几层

  - **div > p** div 和 p 是**父子关系**

  - **div ~ p** div 后面的所有**同级**p 标签

  - **p + ul** 选择紧跟 p 标签后面的 ul 元素，p 和 ul 是**兄弟关系**

  - ul ~ \* 选中**ul 后面的兄弟元素**

  - \* :hover 任意元素里的元素被 hover 时，但选不中 html

  - .foo ~ [role] + #foo 选中的这个元素要有 id 属性，且紧跟着的上一个兄弟元素要有 role 属性，且这个上一个元素的前面要有一个有 class 属性的兄弟元素

  - [role="article"] 选择所有 role 属性为 article 的元素

  - [title^="web"] 选择所有 title 属性以 web 开头的元素

  - [title$="world"] 选择所有 title 属性以 world 结尾的元素

  - [title*="Style"] 选择所有 title 属性中任意位置出现 Style 的元素

  - [title~="Style"] 以独立的单词出现

  - [class~="Stylei" i] 不区分大小写

  - [class*=" ui-"],[calss^="ui-"] 选中类名以 ui- 开头的元素

  - [class*="er "],[class$="er"] 选中类名以 er 结尾的元素

  - :first-child :last-child :nth-child(2) :nth-last-child(2)

  - :nth-child(odd) :nth-child(even)

  - :nth-child(3n + 1) **n 从 0 开始计数**

  - :nth-last-child(3n + 1)

  - :not(div) :not(.foo)

- **css 优先级**

  - **继承来的样式没有优先级，即优先级还不如 0 0 0**
  - <font color="red"></font> 标签自带属性样式的优先级比继承来的高，比 0 0 0 低

- css 值与单位

  - **margin-top**: 25% ; 取的是父元素的 content-box 的**width**

    - 因为当父元素 height: auto;时，父元素高度由子元素撑起来，子元素若取父 height，会形成相互依赖

  - padding-top: 25%; 取的是父元素的**width**

  - height: 25%; 取的是父元素的**height**, 当父元素高度不依赖子元素的时候，子元素设置百分比有效。或者当父元素设置百分比，父元素的父元素也要设置百分比，直至声明 html 的 height: 100%;因为不设置的话，相当于 html 的 height 为 auto，又形成依赖

  - **line-height**: 150%; 自己字号的 150%

  - **line-height**: 2; 若子元素 font-size: 50px; 则子元素行高为 100 排序；

  - **vertical-align**: 40%; 自己行高的 40%

  - **font-size**: 200%; 父元素字号的 200%，与 em 效果一样

  - **1rem 代表一个 html 的字号大小**

  - ```html
    <!-- 页面默认字号 16px -->
    html { font-size: 12px; } div { font-size: 2rem; }
    ```

  ```

  - 1vw 视口宽度的100分之一 (包含滚动条)

  - calc(500px - 40%) 更多的是计算百分比,注意空格

  - font-style:  italic;

  - font-variant:  small-caps; 把小写字母显示成小型大写字母，适合当标题
  ```

- 文字相关的属性

  - text-indent: 2em; 用百分比的值是相对于元素自身宽度，适用于块级元素
  - text-transform: uppercase | lowercase | capitalize; 把文字显示成大写/小写/每个单词首字母大写
  - text-align-last: justify; 文本最后一行两端对齐
  - text-decoration: underline dotted red; 着重号
  - word-spacing: 1px; 单词之间的间距在原有基础上加了一个像素
  - letter-spacing: 1px; 字母之间...
  - word-break: break-all; 单词折行
  - word-sapce: no-wrap; 不换行，一行显示

- 盒模型

  - DTD（Document Type Defination）文档模型由 DOCTYPE 声明称为文件类型定义，浏览器会**通过识别 DTD 采用相对应的渲染模式（标准模式、怪异模式），声明 HTML 版本，让浏览器解析器知道应该用哪个规范来解析文档**。

  - 简述盒模型

    - 1. 盒子模型分为 标准盒模型（W3C 标准模型）、怪异盒模型（IE 盒模型）
      2. margin 可以为负值

  - ```html
    <!--
    box-sizing属性默认不继承，
    标准模式下，一个盒子模型的总宽度= width + margin(左右) + border(左右) + padding(左右)（width是content的宽度）
    怪异模式下，一个盒字模型的总宽度= width + margin(左右)（即width已经包含了content、border、padding）
    -->
    box-sizing: border-box; 怪异模式 box-sizing: content-box; 标准模式
    ```

  - **有 doctype 声明的话，浏览器按 box-sizing: content-box;来渲染**

  - ```html
    <!-- 全局设置box-sizing属性，当父元素修改box-sizing属性值，其后代自动inherit -->
    html { box-sizing: border-box; } * { box-sizing: inherit; }
    ```

  - ```html
    <!-- 三角形 -->
    div { width: 0; height: 0; border: 15px solid; border-color: red transparent
    transparent rgba(0,0,0,0); }
    ```

  - ```html
    块元素水平布局： 1.水平方向的七个属性之和要等于包含块的content-box宽度
    2.width
    默认为auto,且尽量占据多的空间，其他属性值默认为0,可以设置margin为auto(上下为0)
    3.零个auto：则margin-right由默认的0重置为auto 4.一个auto：计算出它
    5.两个auto：
    5.1：两个都在margin上，则两边margin相同，若计算出负值，都给到margin-right
    5.2：其中一个在width上，则width占据尽可能多的空间，另一个auto为0
    6.过分受限的话，margin-right会重置为auto 7.元素宽度不受内容影响
    8.margin-left计算结果不能为负值，但可以声明为负值
    ```

  - **calc 设置 paddding 实现 通栏 + 居中**

- **合并垂直外边距**（此现象发生在**常规流垂直方向上的块元素**）

  - 兄弟元素之间上下 margin 会合并
  - 父子元素之间

    - 当子元素有 margin，父元素 margin 为 0，且没有 border 时，它们会重叠在一起，也就是说子元素 margin 成为了父元素的 margin

  - ul 没有 border 的时候，li:first-child 与 li:last-child 的 margin 会成为 ul 的 margin，ul 的范围是包住 li:first-child 与 li:last-child 的 border-box ,**有 border 的时候，包住 margin-box**
  - **垂直方向上的 margin 设置为 auto，会重置为 0**

- **负外边距**

  - 两个负外边距重合，取绝对值最大的那个

- body 的高度是第一个元素的开始与最后一个元素的结束

- **为什么要有 BFC(块级格式化上下文)**

  - 如果**父元素就想要包住子元素的 margin 的话** ，就得触发父元素的 BFC，这样父元素就包住了子元素的 marginbox

  - ```html
    <!--
    外层元素触发BFC,会创建一个封闭空间，此时外层元素包的是margin-box
    子元素的margin跑不出去,里面的元素和外面的互不影响(因为子margin不会成为父的margin)
    -->
    <div>
      <p>lorem3</p>
    </div>
    ```

  - ```css
    /** 触发元素BFC的方式 **/
    div {
      overflow: hidden;
    }
    div {
      display: flow-root;
      /** 相当于父元素重新开启了一个常规流(页面)，子margin不会跑到页面外面 **/
    }
    ```

- **行内元素**

  - line-height：可以把行高当作一个框，是一行字实际的显示区域，**它的垂直中心和 em 框的垂直中心在一起**，和文本行基线之间的距离
  - 行内框：它是一个布局概念，对于非替换元素，元素行内框的高度刚好等于 line-height 的值，也就是行高框， 父元素包的是行高框。对于替换元素，其行内框的高度等于 margin-box.
  - 非替换元素的内边距、边框和外边框对行内元素或其生成的框**没有垂直布局效果**，只有显示效果
  - 替换元素的外边距和 border 确实会影响该元素行内框的高度，替换元素的 margin-box 对着 x 的基线，可以通过调整 vertical-align 属性调整对齐方式
    - img 的行内框是 margin-box
  - 对于 display：inline;的元素，看它的行内框就是只看它的行高

- 幽灵字符(有字出现就会有幽灵字符)

  - ```html
    <!-- 图片下方有一个字符间隙(因为幽灵字符的存在)，增大行高，间隙越来越大 -->
    <p>
      <img src="https://www.zhihu.com/favicon.ico" />
    </p>
    <!-- 设置vertical-align的top/middle/bottom可以解决间隙 -->
    ```

  - ![image-20201011202411784](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201011202411784.png)

- propagate to viewprot(冒泡到视口)

- ```html
  <!-- 给html设置bgc,滚动条会应用到视口 -->
  html,body { overflow: scroll; }
  <!-- 单独给body设置滚动条，也会显示在视口 -->
  body { overflow: scroll; }
  ```

- html5shiv(条件注释)

- ```html
  ui { font-size: 0; }
  <!-- 副作用 因为ui有margin，默认1em,当字号变为0，所以margin被重置为0 -->
  ```

- 颜色与背景(背景不继承)

  - ```html
    <!-- 背景颜色填充border-box -->
    background-color: lime;
    <!-- 背景图片从padding-box开始平铺 -->
    background-image
    <!--
    1. 图片水平宽度为200px，height等比缩放
    2. 图片高度为200px,width等比缩放
    3. 图片在哪个盒子平铺，就取该盒子值的百分比
    4. contain: 图片等比放大到刚好被元素包住. cover: 图片放大到把元素覆盖住
    -->
    background-size: 200px; background-size: auto 200px; background-size: 50%;
    background-size: contain; background-repeat: repeat-x;
    <!--
    1.向右偏移10 向下偏移20
    2.向右偏移10 垂直居中
    3.水平居中   向下偏移10
    4.四个角落
    5.图片向中心偏移
    6.从最右向左偏移50px
    7.当值为40%时，图片的40%对应元素的40% -->
    background-position: 10px 20px; background-position: 10px;
    background-position: center 10px; background-position: left bottom;
    background-position: left 10px bottom 10px; background-position: calc(100% -
    50px);
    <!--
    默认值 scroll,随着元素滚动而滚动，不会随着元素的滚动条滚动而滚动，
    local 会随着元素的滚动条滚动而滚动
    fixed 相对于视口摆放，此时图片size对于视口。元素离开视口，图片就看不到了
    -->
    background-attachment: fixed;
    <!-- 定义起始平铺位置-->
    background-origin: content-box || border-box || padding-box
    <!-- 只显示content-box盒子区域内的背景图片 和颜色 -->
    background-clip: content-box; object-fit: contain; 图片缩小到正好撑满元素
    ```

- ````html
  - 定位 - ```html 1.元素脱离常规流(周围元素、包含块都感知不到它的存在)
  2.元素成为了定了位的块级元素,类似inline-block，尽量包着子元素 3.fixed
  元素的margin-box相对于窗口定位,不会随着页面滚动而滚动 4.relative
  元素没变，未脱离常规流，相对自身定位 5.absolute 元素脱离常规流,
  相对于最近的定位祖先(position不为static)的padding-box，没有就相对于html定位，随着页面滚动。设置top:0;left:0;
  会怼着html元素左上角. 6. sticky 粘连定位， position: fixed; position:
  relative; position: absolute; span { position: sticky; top: 0; }
  <!--
      可以认为是融合了fixed定位和relative定位
      元素的四周都在窗口以内的时候，看起来就在常规流里
      当元素的某一边从窗口的对应边离开时，触发该边的fixed定位以及该边的方位距离，
      而元素本身必须出现在其包含块内部，如果包含块离开窗口，元素也会被带走
      元素原来位置是保留的，最终会被父元素滚动带走 -->

  z-index
  <!--
      该属性只能用在定位元素上
      只能为整数。范围是-2147483648 - 2147483647
      如果父子元素都定位的时候，子元素无法通过z-index跑到父元素的下方
      -->
  ````

- **垂直水平居中**

- **transition**

  - transition: 什么属性 如何变过去(匀速 or 碎步 or 等等) 用多久的时间慢慢变 等多久以后才开始变, 什么属性 如何变过去(匀速 or 碎步 or 等等) 用多久的时间慢慢变 等多久以后才开始变, **width linear 1s 1s;**

- **表格布局**

  - **只有单元格，表本身有边框**

  - ```html
    <!-- 边框合并,此时可以给tr等元素设置边框 -->
    table { border-collapse: collapse; }

    <!-- border相当于给到了table 和 td -->
    <table border="1">
      <!-- col标签不能hover -->

      <!-- 选中td空标签 <td></td> -->
      td:empty

      <!-- 左侧自适应-->
      <table>
        <td>左侧内容</td>
        <td>右侧</td>
      </table>
      table { width: 100%; } td:first-child { width: 1px; }
    </table>
    ```

- 浮动

  - 行内元素设置浮动，元素会生成一个块框,此时设置宽高有效

  - 常规流中的块元素感知不到浮动元素，常规流中的行内元素可以感知的到,并绕着它渲染

  - s 父元素也感知不到

  - 浮动的子元素的**margin-box**怼着父元素

  - 行内元素盖着浮动元素，和先后顺序无关

  - ```css
    /**
    float 和 定了位且脱离了常规流的(absolute，fixed)元素搭配不生效
    float 和 未脱离常规流的元素搭配才生效，
    并且float先生效。先浮动，然后相对于浮动后的位置偏移
    **/
    div {
        positin: relative;
        top: 2px;
        float: left;
    }
    /** 闭合浮动定义 **/
    某个块框通过增加自己的高度使其能够包含其浮动的后代元素
    /** 如何让父元素包着浮动的子元素 **/
    触发包含块的BFC.具体效果是
      元素包着子元素的margin
      元素包着自己所有的浮动后代(即闭合浮动)
      元素自动变窄以避开与浮动元素的重叠。
      div {
        overflow: hidden;
        display: flow-root;
        display: inline-block; X
        display: table-cell;
        float: left; X
        position: fixed/absolute; X 一般不采用，后面的元素同样感知不到定位元素
       }
    不常用的方法
       在父元素底部添加一个section
       section {
         clear: both;
       }
    或者 回车
       <br clear="both">
    通用闭合浮动
      <div class="clearfix"></div>
    .clearfix {
        clear: both;
       }
    /** 清除浮动定义**/
    某一个块框通过向下移动，使其两边木有浮动元素。块框的border-box移到浮动元素的布局盒子(margin-box)的下方
    div {
      clear: both;
        /**
        此属性控制的是自己，控制不了别人
        元素的border-box在浮动元素的下方
        **/
    }

    ```

- 伪元素

  - ```html
    <li data-tip="低价促"></li>
    li[data-tip]:after { content: attr(data-tip); white-space: nowrap; }
    ```

- 计数器

  - ```css
    /* 每遇到一个这样元素的，计数器变量para + 1 */
    p {
      counter-increment: para 1;
    }
    p::before {
      content: counter(para) ". ";
    }
    /** 遇到h1标签 后面重置计数器变量para **/
    h1 {
      counter-reset: para;
    }
    ```

- 媒体查询

  - ```css
    /** media query 不会让优先级发生变化 **/
    @media (max-width: 600px) {
        div {
           color: red;
        }
      }
    /** 对手机生效 **/
    <meta name="viewport" content="width=device-width">
    ```

- flex 布局

  ```html
  section { /** 主轴默认值向右 **/ flex-direction: row; /** 交叉轴 **/
  flex-wrap: wrap; /** 一行或一列的元素在主轴方向上的摆放 **/ justify-content:
  center; /** 行们或列在交叉轴方向上的摆放 **/ align-content: middle; /**
  行里的元素在这一行中，交叉轴方向上的对齐方式 **/ align-items: center; }
  section div { /** 跟align-items的取值是一样的 **/ align-self: stretch; /**
  展示顺序 **/ order: 5; /** 扩张因子 每一行主轴方向上多余的空间分配权重，**/
  flex-grow: 0; /** 收缩因子
  每一行主轴方向上空间不够时元素的收缩系数，收缩权重还要拿flex-shrink乘以元素的宽/高
  收缩只会发生在不wrap的情况下 div.width * flex-shrink **/ flex-shrink: 1; /**
  元素在主轴方向上的初始尺寸，相当于width或height
  值不为auto时，级别比width,height高 ， **/ flex-basic: ; } /** 相关网站 **/
  1.https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/
  2.https://flexboxfroggy.com/ /** damiao **/ display: flex / inline-flex; /**
  元素本身是行内的，内部是flex **/ flex-direction: row | row-reverse | column |
  coumn-revers; flex-wrap: nowrap | wrap | wrap-reverse; flex-flow:
  <flex-direction>
    ||
    <flex-wrap
      >; 一行或一列的元素在主轴方向上的摆放 justify-content: flex-start flex-end
      space-around space-between; 行或列在交叉轴方向上的摆放 align-cotnent:
      flex-start flex-end space-around space-between stretch;
      行中的元素在这一行中，交叉轴方向上的摆放 align-items: baseline |
      flex-start | flex-end | center; flex
      item单独调整自己在行中，交叉轴方向的摆放
      align-self：跟align-items的取值是一样的 flex-grow
      每一行主轴方向上多余的空间分配权重，这个属性不会改变元素在在不同行的分布
      flex-shrink
      每一行主轴方向上空间不够时元素的收缩系数，收缩权重还要拿flex-shrink乘以元素的宽度或高度
      收缩只会发生在不wrap的情况下 flex-basis
      元素在主轴方向上的初始尺寸，相当于width或者height
      flex：一次性设置grow，shrink和basis属性。 order 调整 flex
      子元素的展示顺序的。 flex布局可以实现双向居中
      flex父元素里的匿名文本也将成为一个flex-item flex子元素的margin
      auto在可能的情况下将会占据剩余的空间</flex-wrap
    ></flex-direction
  >
  ```

  - align-items: stretch ;**属性默认值** 默认拉伸 div 的高度

  - align-items: flex-start 保持原有的尺寸

- ```css
  /*单行文本省略号*/
  p {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
  }
  /* 折行*/
  p {
      word-wrap: break-word;
  }

  longggg&shy;wordbreak
  ```

- FOUC

  - 把首屏样式放在 style 里

- ```css
  linear-gradient div {
    height: 100px;
    background-image: linear-gradient(red, yellow);
    background-size: 50px 50px;
  }
  ```

- ```html
  viewport声明：
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  只被手机浏览器识别。不被电脑浏览器识别。
  它的作用是设定手机浏览器使用多宽的窗口（即初始包含块的宽度）来渲染页面
  手机上页面一旦渲染，窗口的大小是不再发生变化的，双指缩放也不会让页面重新布局
  手机在特定宽度的浏览器上渲染完成后会将结果正好铺满手机屏幕
  所有的手机都支持viewport的width写成device-width，该值在不同手机上不一样，典型的大小是360，415，425，390，320
  一般来讲屏幕越大device-width实际生效的值也越大
  安卓5.0以上支持将viewport的width写成具体数值，这样一来开发者就相当于面对了相同宽度的手机浏览器窗口。
  针对不同的网站设计，需要使用不同的方案：
  网站想要像小米商城移动版一样，是不同手机上都是等比的，
  如果网站用户的浏览器都支持将viewport的width写成具体数值，那么就直接将width写成视觉稿的宽度（不用带单位）
  然后整个页面就用从视觉稿里量出来的数据配上px单位。
  如果网站用户的浏览器有比较旧的，不支持将viewport的width写成数值，而只能写成device-width
  我们想要的效果其实就是视觉稿宽度就是屏幕宽度 假设视觉稿宽度为X，则Xrem = 100vw
  于是 html {font-size: calc(100vw / X)}
  开始时使用视觉稿中量出来的尺寸配上rem单位即可。
  但是，由于Chrome浏览器默认不支持小12px的字号，所以html元素的字号放大100倍
  视觉稿中测量出来的数值则要缩小100倍再加上rem单位
  更旧的浏览器甚至不支持calc/vw，所以使用js读取出窗口宽度的px单位的长度，然后计算出结果并设置到html元素上
  小米商城就是这么做的 body { font-size: 16px; }
  对于内容更多以文字为主，没有太多需要保持比例的布局的网站，如github的首页
  那么直接将viewport设置为device-width，让不同手机有不同窗口宽度
  使用流式布局风格+media query来实现。
  对于布局想要保持比例，但文字内容跟屏幕大小呈正相关的网站
  可以使用device-width，让文字保持默认大小即16px，那么空间越大字就越多
  但页面的布局及元素的大小，依然使用rem等比缩放布局。
  ```

- 2D,3D 变换

  ```css
  transform-origin: left center;
  (不动点)/**后一个变换基于前一个的结果**/transform: rotate(20deg) translatex(
      30px
    );
  /** scale放大不影响布局, zoom: 2;相当于把页面放大200% **/
  transform: scale(2);

  /** 3D **/
  transform: perspective(500px) rotatey(45deg);
  transform-style: preserve-3d;
  /** 关键帧 **/
  @keyframes keyname {
    from {
    }
    50% {
    }
    to {
    }
  }
  div {
    animation-name: keyname;
    animation-duration: 3s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: alternate | reverse | alternate-reverse;
  }
  ```

- 回流与重绘

  ```html
  回流 reflow relayout 重新计算元素的布局(大小，摆放位置等) 重绘 repaint
  (视觉效果发生变化)
  ```

- 回到顶部

  ```html
  scroll-behavior: smooth; 元素内容需要滚动时总是平滑滚动
  ```

- Source map

  ```html
  Source
  map就是一个信息文件，里面存储着位置信息，也就是说转换后的代码的每一个位置，所对应的转换前的位置
  有了它，出错的时候，除错工具将直接显示源代码，而不是转换后的代码
  ```

- 元素无法被选中

  ```html
  * { user-select: none; } * { pointer-events: none; }
  ```

- 元素成比例

  ```css
  <div > <span > </span > </div > div {
    width: 200px;
    border: 2px solid;
  }
  span {
    display: block;
    padding-bottom: 50%;
  }

  /** 或者div不设宽度,但当div里有内容时(内容本身有高度)，比例就不对了， **/
  <div > </div > div {
    border: 2px solid;
    padding-bottom: 50%;
  }

  /** 解决方案是position **/
  div {
    position: relative;
  }
  span {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border: 5px solid red;
  }
  ```
