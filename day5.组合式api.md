## setup()

### 第一种

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

### 第二种

```vue
<script setup>
// 此处全是setup中的内容，但如果需要响应式，还是需要引入reactive
// (个人觉得还是用前面那种方式好一些)
const msg = "我爱vue"

</script>

<template>
<h1>{{msg}}</h1>
</template>
```

上面捎带介绍了reactive作为响应式，但需要注意reactive只能声明对象，所以如果声明一个基本类型的变量时候，需要引入新的`ref`

> 需要注意的是 如果要在script使用ref的变量 需要通过.value访问到， **template中使用则不要加value(会自动解包)**

```vue
<script setup>
import {ref} from 'vue'
// 使用ref
const msg = ref("我爱vue")
console.log("ref----",msg)
console.log("ref.value----",msg.value)

</script>

<template>
<h1>{{msg}}</h1>
</template>
```



![image-20230418215929913](http://img.hahagblog.com/local/image-20230418215929913.png)

1. setup中的变量通常不是响应式的，如果需要响应式，需要import reactive使用
2. 如果要在页面中使用变量 则需要再setup 中return
3. setup的设计是为了使用组合式api