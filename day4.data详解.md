- data()元素的值是被js.proxy代理

## methods

```vue
methods: {
    sum(a, b) {
        return a + b
    }
}

<template>
    <button @click="sum">
     点我 
  </button>
</template>
```

## Computed

> 尽量只在computed写读取操作逻辑，不要有修改、更新操作(应该写在method中)

```vue
  computed:{
    // info变量计算方法 只监听msg.age变量  其他变化不会调用
    info(){
       return this.msg.age >= 18 ? "成人了" : "未成年"
    }
  }
```

### setter

### getter