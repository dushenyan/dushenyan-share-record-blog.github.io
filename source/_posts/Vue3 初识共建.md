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
  - 如果有重名，setup优先
  - Vue2.x中配置(data,methods,computed等...)中可以访问到setup中的属性以及方法
  - 在setup中不能访问到Vue2.x中的属性以及方法
- Setup不能是一个async函数，因为返回不是对象而是Promise对象，模板中看不清其中返回的对象。(可用awite 解析返回正常对象)

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

### computed 计算属性

与方法函数的区别

- 缓存
- 效率

 ```vue
 <template>
   <h4>{{ MovieAll }}</h4>
   电影名称: <input type="text" v-model="MovieInfo.name" />
   <br />
   上映时间: <input type="number" v-model="MovieInfo.time" />
 </template>
 
 <script setup lang="ts" name="Abb">
 const MovieInfo = reactive({
   name: "隐入凡尘",
   time: 2020,
 });
 
 // 简便写法 读取返回数据
 const MovieAll = computed(() => {
   return MovieInfo.name + " - " + MovieInfo.time;
 });
 </script>
 ```

```vue
<template>
  <h4>{{ MovieAll }}</h4>
  电影名称: <input v-model="MovieInfo.name" />
  <br />
  上映时间: <input v-model="MovieInfo.time" />
  <br />
  修正: <input v-model="MovieAll" />
</template>

<script setup lang="ts" name="Abb">
const MovieInfo = reactive({
  name: "隐入凡尘",
  time: "2020",
});

// 完整写法 读取修改数据
const MovieAll = computed({
  get() {
    return MovieInfo.name + " - " + MovieInfo.time;
  },
  set(n: string) {
    let nl = n.split("-");
    console.log("nl", nl);

    MovieInfo.name = nl[0];
    MovieInfo.time = nl[1];
  },
});
</script>
```

### watch 监视属性

- 与Vue2.x中watch配置功能一般
- 踩坑
  - 监视reactive响应式数据时候: oldValue无法正确获取,强制开启deep深度监视失效
  - 监视reactive响应式数据中某个属性: deep配置有效

```vue
<script>
// 数据模板
let numRef = ref(0)
</script>
```

操作数据:

```vue

```



### toRef函数

- 创建ref对象，其value值指向另一对象中的某个属性
- 将响应式对象中某个属性单独提供给外部使用
- toRef和toRefs功能一致，后者可以创建多个ref对象

```vue
<template>
  <h4>{{ name }}</h4>
</template>

<script setup lang="ts" name="Abb">
const MovieInfo = reactive({
  name: "隐入凡尘",
  time: "2020",
});
  
// toRef函数
const name = toRef(MovieInfo, "name");

// 注意点: 使用ref去取name值是,不会去修改MovieInfo值,而是初始化返回新值

// toRefs函数
const { name, time } = toRefs(MovieInfo);
</script>
```

## 扩展Composition API

> shallow 翻译: 浅的

### shallowReactive 与shallowRef 函数

- shallwRef：只处理基本数据类型的响应式，不进行对象响应式处理

- shallowReactive：只处理对象最外层属性的响应式（浅响应）

- 什么时候用？

  - 如果一个对象数据，结构比较深，但只需要变化外出属性 ==> shallowReactive

  - 如果一个对象数据，后续功能不会修改改对象中属性，而是新生的对象来替换  ==> shallowRef

    - ```vue
      <template>
        <h4>{{ MovieInfo.name }}</h4>
        <el-button @click="changeMovieName">点击</el-button>
      </template>
      
      <script setup lang="ts" name="Abb">
      const MovieInfo = shallowRef({
        name: "隐入凡尘",
      });
      
      // 不可行
      // const changeMovieName = function () {
      //   MovieInfo.value.name = "机器人总动员";
      // };
      
      // 将响应式对象MovieInfo数据进行修改
      const changeMovieName = function () {
        MovieInfo.value = { name: "机器人总动员" };
      };
      </script>
      ```

### readonly与shallowReadonly函数

- readonly：让一个响应式数据内部全部变为只读（深只读）

- shallowReadonly：让一个响应式数据变为只读（浅只读）
- 应用场景： 不希望数据被修改，且改后有警告

```vue
<template>
  <h4>{{ MovieInfo.name }}</h4>
  <el-button @click="changeMovieName">点击</el-button>
</template>

<script setup lang="ts" name="Abb">
// =============ref====================
let MovieInfo = ref({
  name: "隐入凡尘",
  time: "2020",
});

// 深层次数据为只读 修改警告
// MovieInfo = readonly(MovieInfo);

// 只考虑最外层数据为只读 修改成功
MovieInfo = shallowReadonly(MovieInfo);
console.log("MovieInfo", MovieInfo);

const changeMovieName = function () {
  MovieInfo.value.name = "机器人总动员";
};

// =============reactive====================
let MovieInfo1 = reactive({
  name: "隐入凡尘",
  time: "2020",
  look: {
    person: 18,
  },
});

// 深层次数据为只读 警告
// MovieInfo1 = readonly(MovieInfo1);

// 只考虑最外层数据为只读 成功
MovieInfo1 = shallowReadonly(MovieInfo1);
console.log("MovieInfo1", MovieInfo1);

const changeMovieName1 = function () {
  MovieInfo1.look.person = 18;
};
</script>
```

### toRaw与markRaw函数

- toRaw函数
  - 作用：将一个由reactive生成的响应式对象转变为**普通对象**
  - 使用场景：用于读取响应式对象对应的普通对象,对这个普通对象的所有操作都不会引起页面更新
- markRaw
  - 作用：标记一个对象，使其永远不会在成为响应式对象
  - 使用场景
    - 有些值不应该为响应式，例如第三方类库
    - 当渲染具有不可变数据源的大列表，跳过响应式转换提高性能

### customRef函数

- 作用：创建一个自定义ref，并且对其依赖项跟终和更新触发进行显式控制

## 起始组件

### Transform组件



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



