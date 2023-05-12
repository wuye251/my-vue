

>  `v-on`或简写`@`来监听事件，如`v-on:click="handler"`或者`@click="handler"`

## 内联事件

简单场景使用， 例:

```vue
const count = ref(0)

<button @click="count++">Add 1</button>
<p>Count is: {{ count }}</p>
```

也就是事件执行逻辑写在dom块内的简单逻辑操作称为内联事件

## 方法事件

将更复杂的内联事件的逻辑写到script方法中, 参数是event,自动传入 例:

```vue
const name = ref('Vue.js')

function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` 是 DOM 原生事件
  if (event) {
    alert(event.target.tagName)
  }
}
template
<!-- `greet` 是上面定义过的方法名 -->
<button @click="greet">Greet</button>
```

## 事件修饰符

```vue
<!-- 单击事件将停止传递 -->
<a @click.stop="doThis"></a>

<!-- 提交事件将不再重新加载页面 -->
<form @submit.prevent="onSubmit"></form>

<!-- 修饰语可以使用链式书写 -->
<a @click.stop.prevent="doThat"></a>

<!-- 也可以只有修饰符 -->
<form @submit.prevent></form>

<!-- 仅当 event.target 是元素本身时才会触发事件处理器 -->
<!-- 例如：事件处理器不来自子元素 -->
<div @click.self="doThat">...</div>

<!-- 添加事件监听器时，使用 `capture` 捕获模式 -->
<!-- 例如：指向内部元素的事件，在被内部元素处理前，先被外部处理 -->
<div @click.capture="doThis">...</div>

<!-- 点击事件最多被触发一次 -->
<a @click.once="doThis"></a>

<!-- 滚动事件的默认行为 (scrolling) 将立即发生而非等待 `onScroll` 完成 -->
<!-- 以防其中包含 `event.preventDefault()` -->
<div @scroll.passive="onScroll">...</div>
```

## 按键修饰符

输入某个键触发事件, 如:

```vue
<!-- 仅在 `key` 为 `Enter` 时调用 `submit` -->
<input @keyup.enter="submit" />
```

> 更多按键修饰符可以看：[官网按键修饰符节内容](https://cn.vuejs.org/guide/essentials/event-handling.html#key-modifiers)

### 鼠标修饰符

相同的也提供了鼠标的触发事件

- `.left`
- `.right`
- `.middle`

## 附录

- [vuejs官方事件处理文档](https://cn.vuejs.org/guide/essentials/event-handling.html)