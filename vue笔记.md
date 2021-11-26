### part1 基础
引入vue  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
vue核心内容:
new vue({
  el:'',
  template:`{{}}`,
  data:{

  }
});
el:挂载点
template:模板(最终形成ui点原始结构)
data:数据
vue会帮助我们根据data的数据把模板进行渲染,添加到挂载点的位置上.


### part2 template
模板生成后的内容会替换挂载点指定的元素
每一个独立的模板有且只有一个顶级的根节点(如果有多个节点,最外层要用一个容器包起来).

如果指定了el,且没有template,那么el的outerHTML将作为template
如果有template,则优先选择template中的内容

### part3 vue渲染
template => VDOM(虚拟dom) =>html

直接创建 `VNode` （虚拟dom对象），优先级高于 `el` 和 `template`
         creatElment

实现一下createElement函数能帮助理解

### part4 el


当 `Vue` 实例没有 `el` 选项的时候，它会处于一种 <u>未挂载</u> 的状态，我们可以通过组件 `Vue` 实例对象的 `$mount` 方法来手动挂载，通过该方式，我们也可以达到延迟 `Vue` 实例的挂载的目的

app.$mount('#app') 


el:挂载点不能是body和html
当实例被挂载以后,实例对象上就会有一个$el的属性,这个属性就是挂载点元素
vue实例上的内置属性都是以$或者_开头的

### part5 data
data中的数据命名不要使用$,_开头
因为Vue解析data以后,会把当前data中的数据挂载到实例对象上,避免命名冲突

响应数据的变化(数据驱动视图)
数据的变化会自动更新视图(自动重新渲染模板)

了解一下proxy
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy

### part6 vue指令

https://cn.vuejs.org/v2/api/#v-text

https://cn.vuejs.org/v2/guide/list.html#s-authing



通过 `{{}}` 我们可以很方便的中模板中输出数据，但是这种方式会有一个问题，当页面加载渲染比较慢的时候，页面中会出现 `{{}}` ，`vue` 提供了几个指令来解决这个问题

> 指令中的表达式不需要使用 `{{}}`

指令=后面的内容是表达式,而不是普通的字符串
v-show 改变的只是该元素的display样式
       数据的改变比较频繁的时候
v-if改变的是元素的结构(渲染或者删除)
    数据的改变不频繁的时候

    v-if和v-else以及v-else-if必须是连续的

    v-for和 v-if 一起使用时，v-for 的优先级比 v-if 更高。