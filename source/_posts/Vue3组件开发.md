# Vue3组件开发

### AnimateList动画

```vue
<script setup lang="ts">
import gsap from "gsap";
import { RendererElement } from "vue";

interface props {
  tag?: string;
  duration?: number;
  delay?: number;
}

const props = withDefaults(defineProps<props>(), {
  tag: undefined,
  duration: 0.5,
  delay: 0.2,
});

const beforeEnter = (el: RendererElement) => {
  gsap.set(el, {
    opacity: 0,
  });
};

const enter = (el: RendererElement) => {
  gsap.to(el, {
    opacity: 1,
    duration: props.duration,
    delay: el.dataset.index * props.delay ?? 0,
  });
};
</script>

<template>
  <div class="animate-list">
    <TransitionGroup
      :tag="props.tag"
      appear
      name="animate"
      @before-enter="beforeEnter"
      @enter="enter"
    >
      <slot />
    </TransitionGroup>
  </div>
</template>

<style  scoped>
.animate-list {
  position: relative;
}

.animate-leave-active {
  transition: all 1s ease;
  position: absolute;
  width: 100%;
}
.animate-leave-to {
  opacity: 0;
}
.animate-move {
  transition: all 1s ease;
}
</style>
```

使用

```vue
<template>

  <AnimateList tag="ul" :duration="1" :delay="0.8">
    <li v-for="(num, index) of 10" :data-index="index" :key="index">
      {{ num }}
    </li>
  </AnimateList>
</template>

<script setup lang="ts">
import AnimateList from "../components/AnimateList.vue";
</script>

<style>
ul li {
  background-color: peru;
  padding: 2px;
  margin-bottom: 2px;
  color: white;
  list-style: none;
}
</style>
```

