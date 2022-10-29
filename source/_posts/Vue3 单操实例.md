## Vue3 单操实例

> 只存在两种版本写法

### 模板记载

- script ==> setup   

  - 快捷获取键入 vue3

    ```vue
    <script setup lang="ts" name="">
    interface Props {
      title?: string
    }
    const props = withDefaults(defineProps<Props>(), {
      title: 'ss'
    });
    
    </script>
    
    <template>
      <div>
        <slot></slot>
      </div>
    </template>
    ```

- script ==> defineComponents

  - 直接键入vue2

    ```vue
    <template >
      <div>
        <slot></slot>
      </div>
    </template>
    
    <script>
    export default defineComponent({
      name: "",
      setup() {
    
        return {
    
        }
      }
    })
    </script>
    ```


### 插槽

- [Vue 插槽(slot)使用(通俗易懂)](https://juejin.cn/post/6844903920037281805#heading-6)

```vue
<script setup lang="ts" name="Son">
const slot = useSlots()
console.log('slot', slot.default())
</script>

<template>
  <slot></slot>
  <slot name="header" ></slot>
  <slot name="main" style="color:yellow" h1="one"></slot>
  <slot name="footer" style="color:green"></slot>
</template>
```

```vue
<script setup lang="ts" name="Home">
import Son from './Son.vue';
const text1 = ref('这是一段文本可用于测试UseContext钩子')

const props = withDefaults(defineProps<{
  data: boolean
}>(), {})
</script>

<template>
  <Son >
    <h4>{{text1}}</h4>
    <template v-slot:header>
      <h5>略略略略略略略略略略略略略略11略略略略略略略略略略略略略略略略</h5>
    </template>
    <slot name="other" :show="props.data"></slot>
  </Son>
</template>
```

```vue
<template>
  <Home :data="randomSlot.type">
    <template #other="{show}">
      <span :style="show?'color:red':'color:yellow'">{{show}}</span>
    </template>
  </Home>
</template>

<script setup lang="ts" >
import * as vue from 'vue';
import Home from './views/Home.vue';
console.log('vue', vue)

const randomSlot = reactive<{
  type: boolean
}>({
  type: true,
})
setInterval(() => {
  randomSlot.type = !randomSlot.type
}, 1500)
</script>
```



### Ref引用

- [通过 ref 获取子组件实例](https://juejin.cn/post/7031921830852034591)

```vue
<template>
  <Home ref="SonRef"></Home>
</template>

<script setup lang="ts" name="Home">
import Son from './views/Son.vue';
let SonRef = ref<InstanceType<typeof Son> | null>(null)
onMounted(() => {
  console.log('SonRef', SonRef.value?.count)
  SonRef.value?.eventCount(8)
})
</script>
```

```vue
<script setup lang="ts" name="Son">
const count = ref(0)

const eventCount = (num: number) => {
  count.value += num
}

defineExpose({
  count,
  eventCount
})

</script>

<template>
  <h1> {{count}}</h1>
  <el-button @click="eventCount">+1</el-button>
</template>
```

### Attrubit

```vue
<script setup lang="ts" name="Son">
console.log("Son中的attrs", useAttrs())
</script>

<template>
  <div class="text">
    <slot></slot>
  </div>
</template>
```

```vue
<script setup lang="ts" name="Home">
import Son from './Son.vue';
</script>

<template>
  <!-- 根元素为Son组件则会合并透传过来的属性和emit以及方法 -->
  <Son>
    {{$attrs.h1}}
    往死里透
  </Son>
</template>
```

```vue
<template>
  <Home class="home" h1="lala" @click="eventClick"></Home>
</template>

<script setup lang="ts" >
import * as vue from 'vue';
import Home from './views/Home.vue';
console.log('vue', vue)
const eventClick = () => {
  console.log("触发")
}

</script>
```



### Emit



### Transtion

- [补习-前端动画](https://juejin.cn/post/7067146867062079519)



### 注入

- [Vue3 官网文档 依赖注入](https://cn.vuejs.org/guide/components/provide-inject.html#inject)

```vue
<script setup lang="ts" name="Son">
import { Provide } from '../App.vue';
console.log("Son中的attrs", useAttrs())

const ev = inject<Provide>('ev')
</script>

<template>
  <h3>Son组件</h3>
  <h4>{{ev?.count}}</h4>
  <el-button @click="ev?.ECount(5)">按钮</el-button>
</template>
```

```vue
<script setup lang="ts" name="Home">
import Son from './Son.vue';
</script>

<template>
  <h3>Home组件</h3>
  <Son></Son>
</template>
```

```vue
<template>
  <Home></Home>
</template>

<script setup lang="ts" name="App">
import * as vue from 'vue';
export interface Provide {
  count: vue.Ref<number>;
  ECount: (e: number) => void;
}
import Home from './views/Home.vue';
console.log('vue', vue)

const count = ref(0)
const ECount = (e: number) => {
  count.value += e
}
// 跨服穿值
provide<Provide>("ev", {
  count,
  ECount
})
</script>
```

