## setup()

```vue
<script>
import {reactive} from "vue"
  export default{
    data() {

    },
    setup() {
      // Step1:在setup()中可以通过返回值来指定哪些内容要暴露给外部
      let msg = "今天我好爱学习啊"
      // Step2:setup中的变量不是响应式，也不能进行修改 如下面的button @click
      // 就是一个普通的变量
      let count = 0

      // Step3:可以使用reactive使setup里的变量成为响应式的变量 如下面的button @click2
      const stu = reactive({
        name:"wu"
      })
      function changeName(){
        this.stu.name = "hahahah"
      }
      return {
        msg,
        count,
        stu,
        changeName,
      }
    },

  }
</script>

<template>
  <!-- step1 -->
  <h1>{{msg}}</h1>
  <!-- step2 -->
  <h1>{{count}}</h1>
  <button @click="count++">点我</button>
  <!-- step3 -->
  <h1>{{stu.name}}</h1>
  <button @click="changeName">点我</button>
</template>
```

1. setup中的变量通常不是响应式的，如果需要响应式，需要import reactive使用
2. 如果要在页面中使用变量 则需要再setup 中return
3. setup的设计是为了使用组合式api