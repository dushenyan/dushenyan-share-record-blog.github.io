---
title: Vue3 初识共建
date: 2022-10-03 18:26:30
categories: 学习笔记
cover: 'https://miro.medium.com/max/918/1*s2vCxDgTCjVt8AyAyFIDhw.png'
---

# Vue3 初识共建

> 视频链接(B站):
>
> 阮一峰ES6教程: https://es6.ruanyifeng.com/#docs/proxy

## 

## 前置知识



## 响应原理初始篇章

> 补充操作实现图

### Vue2.x响应式

实现原理

- 对象类型：通过**Object.defineProperty()**对属性读取修改拦截，简称数据劫持
- 数组类型：通过重写更新数组的一系列方法实现拦截操作

```js
Object.defineProperty(data,'count',{
  get(){},
  set(){}
})
```

存在问题:

- 新增删除属性,不会刷新
- 直接通过下标形式修改,界面不会自动刷新

解决方法:

数据模板:

```vue
<script>
export default {
  data(){
    return {
      person:{
        name:"涌入人群",
        age:1980
      }
    }
  }
}
</script>
```

操作:

```js
// 不可行
this.person.sex = 'woman'

// 在选项API中data中添加响应式数据person.sex
this.$set(this.person,'sex','woman') 或者 Vue.set(this.person,'sex','woman')

// 不可行
this.person.arr[0] = 'woman'

this.$set(this.person.arr,0,'woman') 或者 Vue.set(this.person.arr,0,'woman')
```

```js
// delete
delete this.person.name

// 删除响应式数据person.name
this.$delete(this.person,'name') 或者 Vue.delete(this.person,'name')
```

### Vue3.x响应式

MDN知识传送:

- Proxy：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy
- Reflect：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect

怎么实现?

- 通过Proxy（代理）：拦截对象中任意属性的变化，属性值的读写添加删除等...
- 通过Reflect（反射）：对被代理对象的属性进行操作
  - Object与Reflect区别：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect/Comparing_Reflect_and_Object_methods



## 生命周期

 

## Composition API

### Setup函数

问: 是什么东西?

- Vue3.x中一个新的配置项, 值由一个函数返回
- Setup是所有**Composition API**的写入舞台
- 组件中用到的所有数据方法都需要配置在setup中
- Setup函数的两种返回值
  - 若返回一个对象,则对象中属性方法,在模板中可以直接使用
  - 若返回一个渲染函数,则可以自定义渲染函数

坑点与解决

- 尽量不要与vue2.x混用
  - 如果有重名,Setup优先
  - Vue2.x中配置(data,methods,computed等...)中可以访问到setup中的属性以及方法
  - 在setup中不能访问到Vue2.x中的属性以及方法
- Setup不能是一个async函数,因为返回不是对象而是Promise对象,模板中看不清其中返回的对象.(可用awite 解析返回正常对象)



### Ref函数

问: 是什么东西?

答: 定义一个简单的响应式对象,与_data 相似,看Prototype中得出含有get,set方法

- 插件一个包含响应式数据的**引用对象(reference对象,简称ref对象)
- script中操作数据**xxx.value**
- 模板中读取数据不必写入.value值

更多小点:

- 接受的数据可以是: 基本类型,也可以是对象类型
- 基本类型数据,响应式依然是靠**Object.defineProperty()**的get和set方法完成的
- 对象类型的数据内部采用Vue3.x中的一个新函数--- Reactive函数

名词解析:

- RefImpl ==> reference(引用)  implement(实现)

```vue
<template>
  <h1>{{ PageTitle }}</h1>
</template>

<script setup lang="ts" name="Abb">
const PageTitle = ref("HelloWorld 页面");
console.log("PageTitle", PageTitle);
</script>
```

#### 使用Ref处理复杂数据,在内部会将其转化为Proxy

```vue
<template>
  <h1>{{ PageInfo.name }}</h1>
</template>

<script setup lang="ts" name="Abb">
const PageInfo = ref({
  name: "隐入凡尘",
  age: 2020,
});
// 修改值
PageInfo.value.name = "机器人总动员"
  
// RefImpl {} 引用代理对象
console.log("PageInfo", PageInfo);
</script>
```

### Reactive函数

问: 是什么东西?

答: 定义一个**引用类型**的响应式数据(基本类型使用ref函数)

更多小点:

- reactive定义的响应式数据是**深层次**
- 内部基于ES6的Proxy实现,通过代理对象操作源对象内部数据都是响应式

```vue
<template>
  <h4>{{ PageInfo.name }}</h4>
</template>

<script setup lang="ts" name="Abb">
const PageInfo = reactive({
  name: "隐入凡尘",
  age: 2020,
});
// 修改值
PageInfo.name = "机器人总动员";

// Proxy {}  内部不管改谁都是响应式
console.log("PageInfo", PageInfo);
</script>
```

### Reactive与Ref两者对比

- 定义数据
  - ref定义基本数据，reactive定义引用类型数据
  - ref也可以定义引用类型数据，内部自动通过reactive转为代理对象
- 原理角度
  - ref通过Object.defineProPerty()的get和set方法来实现响应式，数据劫持
  - reactive通过使用Proxy来实现响应式，通过Reflect来实现反射修改数据
- 使用角度
  - ref定义数据： 操作数据需要.value去读取，模板中不需要
  - reactive定义数据：操作数据与读取数据都不需要.value









## 新源组件

### Fragment 组件

> 翻译: 碎片,散片的意思

- Vue2中: 组件必须有一个根组件
- Vue3中: 组件可以没根组件,内部会将多个标签包裹在一个Fragment组件中
- 小知识点: 可在Vue浏览器插件中看到包裹元素

优点: 减少不必要层级关系,减少内存占用

### Teleport 组件

问: 什么是Teleport?

答; 一种能够将我们组件html结构移动指定位置的技术

> 翻译: 传送,瞬移的意思

```vue

```

### Suspence 组件 (试验性)

问: 什么是Suspence组件?

答: 等待异步组件时渲染的一些额外内容,让应用有更好地体验

> 翻译: 悬念,悬疑的意思

```vue
导入异步组件
```

```vue
```

优缺点: ...

 造成异步的情况:

- 网速慢
- 内部数据 new promise()



