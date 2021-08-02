```md
vue 
采用的是 DOM 模板 即模板的语法大多以标签的属性存在的，模板是会被Vue框架编译转换的，所以模板里不需要加this，直接使用如 {{ todos.length }}
而 app = new Vue({
    el: "#wrapper", // 这个元素的outerHTML会作为模板，模板的渲染结果是虚拟dom，虚拟dom变成真实dom，替换掉 这个#wrapper元素，后面数据发生变化，会结合模板和数据生成新的虚拟dom，虚拟dom和和上一次的虚拟dom做对比(patch)，对比完了拿差异，这个差异直接在真实dom上做更新，把新算出来的虚拟dom替换旧的虚拟dom(pre_vnode)
    data: {
    
    },
    methods: {
      
    },
   ....... 这里用this是直接运行的，VUE会把这个this设为实例(app), 不加this的话，会往外层找到全局,methods里的方法也不能写成箭头函数，那样同样会找到全局
})
1. 标签绑定 标签自带的属性如class,可以写为 :class = "" , :style = "{color: 'red'}"引号里不需要双括号写法，反之 有的属性 标签不是自带的，需要加前缀 如 v-if="category == 'all' "  v-for="item in ary" 双括号语法是在两个标签之间的内容才用到
2. v-if 和 v-else 必须是连续的兄弟元素
3. 元素绑定事件 拿到事件对象可以通过 如 @click = "addTodo($event)" 这种写法
4. 浏览器不识别标签和属性名的大小写，自身机制会都当作小写

计算属性, 侦听属性(watch监听属性变化)
计算属性有getter，setter
侦听属性也可以直接通过 this.$watch(msg, () => {})， watch第一次不调用
当data里必须有监听的字段的时候，就需要用watch了
app.$set(this.todos,2,{content: 'eat',done: false}) 一般set数组, 通过this.todos[2] = {content: 'eat',done: false } 这种下标方式设置不会生效，给对象直接赋值可以生效，所有VUE3用了Proxy,可以给下标赋值，Proxy可以全方位的监控对象，getter setter需要递归遍历，耗费性能
app.$set(this.$data, 'msg', 'hello')set对象会报错，可以提前在data里声明好变量

自定义标签写在html里，不能自闭和
自定义组件里不要直接绑定传过来的值，可以用一个变量接住，也不要v-model="todo" 临时变量,应该是v-model =”todo.done“
emit时，传递多个参数，父组件监听的事件函数不加括号 
在组件上监听的事件，默认必须是组件内部emit上来的，或者组件上的写法是@click.native

slot
组件模板里的slot会被组件的子元素换掉
具名插槽 组件模板里<slot="header">默认值</slot>
父级里使用 template v-slot
作用域插槽
  父组件传值给自定义组件，自定义组件使用<slot v-bind:data="item" />
  父组件里的自定义组件 template v-slot="item"

this.$root 根组件
ifram window.top顶层窗口

mixins     hooks compositon api
来源不明确

自定义指令一般是给原生标签扩展一些功能
location.href = 'xxx' 编程式导航
根组件 router-view（给子路由展示的空间）  
子组件 router-link to 声明式导航
路由匹配 类名，精确匹配router-link-exact-active
vue根组件用了路由，所有的组件上都能访问到这个$router，访问到的是对应的new 出来的router实例 （router.push,replace,go）
this.$route是这次匹配的路由模式的相关信息，每个组件都可以读到，matched,params,path,query
watch: {
  $route(){}
}


a标签和router-link的区别
1. <router-link :to="{name: 'user', params: {userId: '333'} }"> </router-link>
2. router-link 匹配成功有类名
3. router-link转换为a标签，hash模式会有#号

导航守卫
  失活组件 beforeRouterLeave
  router.beforeEach()
  router.afterEach()
  
 路由懒加载

```

