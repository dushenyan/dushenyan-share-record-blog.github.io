---
title: TypeScript 沉淀笔记
date: 2022-09-25 18:26:30
categories: 学习笔记
cover: 'http://inews.gtimg.com/newsapp_bt/0/13469186158/1000'
---


# TypeScript 沉淀笔记

> 注: 变量名命名不一定存在确切意思
>
> 基于版本号: TypeScript 4.8.x 编写
>
> 查看TS指示 : XF ==> XX 指悬浮鼠标(XF)与XX之上

基础部分 ==> [TypeScript官网](https://www.typescriptlang.org/)查看即可 

触类旁通 ==> [深入理解TypeScript](https://jkchao.github.io/typescript-book-chinese/#why)站点

### keyof 关键字

问题导向: **取得键名**

```ts	
// 类型实例键名
type T1 = keyof string
type T2 = keyof number

// 对象键名
type T3 = keyof { name: string; age: number }

// 可出去String(字符串)中的所有实例方法 
let as1: T1 = "match"

// XF => T3 上 只可填入 name 和 age
let as3: T3 = "name"
```

```ts
// 案例1
function getAttribute(obj: { [x: string]: any; name?: string; age?: number }, key: string) {
  return obj[key]
}
const user = { name: 'du', age: 11 }
getAttribute(user, 'name')

//案例2
function getAttribute<T>(obj:T,key:keyof T) :T[keyof T]{
  return obj[key]
}
const user = { name: 'du', age: 11 }
getAttribute(user, 'name')

// 案例3
function getAttribute<T,D extends keyof T>(obj:T,key: D) :T[D]{
  return obj[key]
}
const user = { name: 'du', age: 11 }
getAttribute(user, 'name')

// 不报错  => 指示string => 为match
getAttribute('aaa', 'match')
```

### typeof 关键字

```ts
let name:string = "du"
```

### Exclude 实现

问题导向: **过滤无需类型**

> https://www.typescriptlang.org/docs/handbook/utility-types.html#excludeuniontype-excludedmembers

```ts
// 声明
// 作用 去除
type EXCLUDE<T, U> = T extends U ? never : T;

// 大 ==(小中存在的类型去除)==> exclude值 
type Dog = string
type Animal = string | number | boolean

type AS = EXCLUDE<Animal, Dog>   // number | boolean

// Exclude TS官方提供
type AS = Exclude<Animal, Dog>  

let as:AS = 1
```

### Extract 实现

问题导向;  **Extrace在TS的含义  ==> 保留需要类型**

> https://www.typescriptlang.org/docs/handbook/utility-types.html#extracttype-union

```ts
type EXTRACT<T, U> = T extends U ? T : never;

type Dog = string
type Animal = string | number | boolean

// 保留右边参数
type AS = EXTRACT<Animal, string | number> 
// type AS = Extract<Animal, string | number>

let as: AS = 1	
```

### TS类型重复声明错误

复现场景: 在同一个编译目录下,存在多个文件,且例如都编写以name,age的类型声明!

解决方案: 在文件内容块添加块标签,以作为局部声明变量

```typescript
{
  // 解决不报错出红线横线
  type name = string
  type age = number
}
```

### Partial实现

问题导向: **属性类型转为可选**

> https://www.typescriptlang.org/docs/handbook/utility-types.html#partialtype

```ts
// 对象声明 ==> 需要 keyof 关键字遍历
type OBJ = { name: string; age: number }

type PARTIAL<T> = {
  [P in keyof T]?: T[P]
}

// 可选写OBJ中全部类型
type AS = PARTIAL<OBJ>

let as: AS = { name: "du" }
```

### Record 实现

问题导向: **RdcordTS类型定义**

> https://www.typescriptlang.org/docs/handbook/utility-types.html#recordkeys-type

```typescript
// 一: 基础写法
type RECORD<P extends (string | number | symbol), V> = {
  [K in P]: V
}

// 二: 略参快捷写法
type MyRecord<K extends keyof any, T> = { 【P in K】: T }

// 看源码普遍查看到,挺重要一知识点
type AS = RECORD<'name' | 'age', string | number>

let as: AS = { name: "du", age: 11 }
```

### infer实现

问题导向: **a**

> https://www.typescriptlang.org/docs/handbook/type-inference.html#handbook-content

```typescript
type T1 = { name: string; age: number }

type AttrT<T> = T extends { name: infer M; age: infer M } ? M : T

type AS = AttrT<T1>
// type AS = string | number
```

```typescript
//迭代写法1
type T1 = { name: string; age: number }

type AttrT<T> = T extends { name: infer M; age: infer N } ? [M, N] : T

type AS = AttrT<T1>
// type AS = [string, number]
```

```typescript
// 迭代写法2
type T1 = { name: string; age: number }

type AttrT<T> = T extends { name: infer M; age: infer N } ? { name: M, age: N } : T

type AS = AttrT<T1>
// type AS = {
//   name: string;
//   age: number;
// }
```
