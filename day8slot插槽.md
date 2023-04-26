> 组件中通过slot显示不同父组件的内容，优化了props传递

## 简介

```vue
// 父组件
<script setup>
  import mybutton from './components/mybutton.vue'

</script>

<template>
  <h1>App组件</h1>
  <!-- 子组件中间写内容 -->
  <mybutton>啊哈</mybutton>
</template>

//子组件
<template>
    <button>
      // 填坑地方
      <slot></slot>
    </button>
</template>

<style scoped>
    button{
        width: 200px;
        height: 100px;
    }
</style>
```

### 多个slot

简介实例中是单个slot的使用，这里再示例一个组件中使用多个插槽

```vue
// 父组件
<script setup>
  import mybutton from './components/mybutton.vue'

</script>

<template>
  <h1>App组件</h1>
  <mybutton>
    <template v-slot:aaa>aaa插槽</template>
    <!-- 简写 #slot-name -->
    <template #bbb>bbb插槽</template>
  </mybutton>
</template>

// 子组件
<template>
    <button>
        子组件
        <slot name="aaa"></slot>
        <slot name="bbb"></slot>
    </button>
</template>

<style scoped>
    button{
        width: 200px;
        height: 100px;
    }
</style>

```

### 具名插槽 和 默认插槽

slot带name的叫做具名插槽、不带name的称为默认插槽

```vue
<script setup>
  import mybutton from './components/mybutton.vue'

</script>

<template>
  <h1>App组件</h1>
  <mybutton>
    <template v-slot:aaa>aaa插槽</template>
    <!-- 简写 #slot-name -->
    <template #bbb>bbb插槽</template>
    <template #default>父组件默认插槽</template>
  </mybutton>
</template>

<template>
    <button>
        子组件
        <slot name="aaa"></slot>
        <slot name="bbb"></slot>
        <slot></slot>
    </button>
</template>

<style scoped>
    button{
        width: 200px;
        height: 100px;
    }
</style>

```

### 插槽传变量 slotProps

将插槽(子组件)中的变量传到使用该子组件的父组件中

- defineProps 接收父组件传值
- #bbb="slotProps" 接收插槽传出的内容赋值给slotProps

```vue
//子组件slot.vue
<template>
    <div>
        子组件
        // 将text传给使用他插槽的父组件
        <slot name="bbb" :text="text"></slot>
    </div>
</template>

<style scoped>
    div{
        width: 200px;
        height: 100px;
        background-color: aquamarine;
    }
</style>

<script setup>
const text = "hahaha"
</script>

// 父组件
<script setup>
  import mybutton from './components/mybutton.vue'
  import A from "./components/A.vue"
</script>

<template>
  <h1>App组件</h1>
  <mybutton>
    <!-- 通过slotProps接收到插槽传出的值 -->
    <template #bbb="slotProps">
      <!-- 将text内容传给A子组件 -->
      <A :text="slotProps.text"></A>
    </template>
  </mybutton>
</template>

// A子组件
<script setup>
    const props = defineProps(["text"])
</script>
<template>
    <h2>A组件接收的name值:{{props.text}}</h2>
</template>
```





## 附录

- [官方插槽文档](https://cn.vuejs.org/guide/components/slots.html)

