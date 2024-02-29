---
title: vue学习
date: 2024-02-10 16:35:56
tags: vue
categories: 学习笔记
---

## vue2.0

```
vue参考了mvvm思想
model -- viewmodel -- view
数据代理机制
```



```js
// 创建Vue实例 vue的构造函数参数options要求传js对象
// 参数里 可以写大量键值对用来 配置
const myVue = new Vue({
     template : '<h1>hello</h1>'
    }
)
// 将Vue实例挂载到id='app'的元素位置
myVue.$mount('#app')
```

## 1.templeate

>模版语句
>
>模版语句只能有一个根节点
>
>data数据发生变化 模版语句重新编译

```js
new Vue({
    template :'<h1>我是模版语句</h1>'
}).$mount('#app')
```

也可以不使用template 直接模版语句写在html中

如果直接写在html中 指定的挂在位置就不会替换了

```html
<div id='app'>
    <div>
        <h1>
            {{msg}}
        </h1>
        <h2>
            {{name}}
        </h2>
    </div>
</div>
<script>
new Vue({
    data:{
        msg: 'hello Vue',
        name: 'zjaaa'
    }
}).$mount(#app)
</script>
```



## 2.data

>Vue实例的数据对象
>
>给整个Vue实例数据来源
>
>data必须是纯粹的对象，含零个或多个键值对
>
>插值语法 { { }}
>
>小细节{ {} } 外面的括号大括号里不能有空格 这样是错的

data可以是函数也可以是对象

```js
new Vue({
    template:'<h1>最近非常火的电视剧{{name}},它的上映日期{{releaseTime}},主演有{{lead.name}},{{actors[0].name</h1>'
    data:{
        name: '狂飙',
        relesaseTime: '2023年一月一日',
        lead : {
            name: '高启强',
            age : 41
},
         actors:  [
        {
        name：'安欣',
        age: 41
        },
       {
           name: '高启兰',
           age:23
       }
        ]
    }
}).$mount('#app')
```

## 3.$mount

>可以用el替代挂载

```html
<div id='app'>
    <h1>
        {{msg}}
    </h1>
</div>
<script>
new Vue({
    data:{
        msg:'hello el'
    }
    el:'#app'
})
</script>
```

## 模版语法

### 插值语法

```
{{可以写data里面的数据}}
{{可以写js表达式}}
{{可以写常量}}
模版表达式都被放在沙盒中，只能访问全局变量的一个白名单
插值语法只能写在标签体 不能写在标签属性
```

### 指令语法

>指令语法才能写在标签属性里 插值语法不行

#### v-once

```vue
<!--只渲染元素一次，随后的重新渲染，元素以及子节点视为静态资源，不在渲染-->
<div>
    <h1 v-once>
        {{msg}}
    </h1>
</div>

```

#### v-if

```vue
<!-- v-if -->
<h1 v-if='10>5'>
    指令表达式为真才渲染
    指令表达式为假不渲染
</h1>
```

#### v-bind

```vue
<img src='1.jpg'>
<img v-bind:src='imgPath'>

vue实例里的data数据如下：
data:{
 imgPath:'2.jpg'
}

v-bind简写
<img :src='imgPath'>
<a :href='url'></a>
```

#### v-model

```vue
v-bind 是单向绑定
data变 视图变

v-model 是双向绑定
data变 视图变
视图变 data变
而且v-model只能用在表单类元素里
因为表单元素才能给用户提供交互输入的界面

v-bind简写方式：
v-bind：参数='表达式' 简写为 :参数='表达式'
v-model:value='表达式' 简写为 v-model='表达式'
```

