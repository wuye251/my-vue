模板中可以直接访问到组件中声明的变量

## v-bind == :

```vue
<script setup>
  import {ref } from "vue"
  const imgPath = ref("/favicon.ico")
  function changeImg() {
     imgPath.value = "/test.png"
  }
</script>

<template>
  <!-- '/'默认访问当前项目public/路径 -->
  <img :src="imgPath" alt="梅西">
  <button @click="changeImg">切换图片</button>
</template>
```

## style:scoped

```
<style>
  h1{
    background-color: aqua;
  }
</style>
```

会对所有组件产生影响

```vue
<style scoped>
  h1{
    background-color: aqua;
  }
</style>
```

加上scoped回使其局部/当前组件产生影响

> 单根组件，多根组件

## style:module

```vue
<template>
  <!-- '/'默认访问当前项目public/路径 -->
  <div :class="$style.box1">App中的box1</div>
  <MyBox></MyBox>
</template>

<style module>
  .box1{
    background-color:blue;
  }
</style>
```

当前模块使用的样式，不会影响子组件

