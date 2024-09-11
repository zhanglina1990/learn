# 1. setup
相比于普通的` <script>` 语法，`<script setup>`具有更多优势：

+ 更少的样板内容，更简洁的代码。
+ 能够使用纯 TypeScript 声明 props 和自定义事件。
+ 更好的运行时性能 (其模板会被编译成同一作用域内的渲染函数，避免了渲染上下文代理对象)。
+ 更好的 IDE 类型推导性能 (减少了语言服务器从代码中抽取类型的工作)

## 1.1. `setup() vs <script setup>`
setup()钩子函数适用场景
1. 在非单文件组件中使用组合式api时
2. 需要在选项式api中集成组合式api时

除此之外，官方都推荐使用优先使用`<script setup>`。`<script setup>`是在单文件组件中使用组合式API的编译时语法糖。


## 1.2.`<script setup>` 
`<script setup>` 中的代码会在每次组件实例被创建的时候执行。
它会在解析属性的时候将顶层的变量声明提升到当前组件的 `<template>` 中。
任何在`<script setup>` 声明的顶层的绑定 (包括变量，函数声明，以及 import 导入的内容（组件）) 都能在模板中直接使用。
**不用使用this**。[详见](https://cn.vuejs.org/api/sfc-script-setup)


# 2.响应式基础
## 2.1.ref
ref 函数用来创建响应式的数据。它接收一个参数，并返回一个包含该参数的响应式数据。
1. 可以使用ref()方法创建一个可以使用任何值类型的响应式。它将传入的参数包装成一个带.value属性的ref对象。声明Object类型时内部通过reactive来转为代理对象。
2. ref能创造一种对任意值的“引用”，并且不丢失响应性，此功能常用于将逻辑提取到组合函数中。

**注意：**
1. 可以响应式的替换整个对象（重写）。
2. 解构或者被传入函数时，不会丢失响应性。

## 2.2.reactive
reactive 函数用来创建响应式的数据。它接收一个参数，并返回一个包含该参数的响应式数据。
1. 可以使用reactive() 函数创建一个响应式对象或数组。
2. reactive仅对对象类型有效（对象、数组、Map、Set），原始类型（string、number、boolean）无效。

**注意：**
1. 不可用随意“替换”（复写）一个响应式对象，会导致对于初始应用的响应性连接丢失。
2. 响应式对象被赋值给另一个本地变量时，本地变量调整不会影响响应式变量。
3. 将响应式变量解构，之后修改值，不会影响原始响应式变量。
4. 将响应式变量传入一个函数时，之后的调整不影响响应式变量。

## 2.3.computed
computed 函数用来创建计算属性。它接收一个参数，并返回一个包含该参数的响应式数据。
使用场景：常用于计算衍生值。
默认是只读的。
return返回的是一个计算属性ref，其他方法中可通过hasBook.value取值
计算属性值会被缓存。方法会被重复调用。

**注意：**
1. 计算属性只做计算，不要在此处做异步请求或者更新DOM

```vue
<template>
  <p>{{bookObj.author}}:是否写过书？</p>
  <span>{{hasBook}}</span>

  <h1>{{authorInfo}}</h1>
  <button @click="changeFullName">
    修改fullName
  </button>
</template>

<script setup lang="ts">
  import{ reactive,computed}from 'vue'
  const bookObj = reactive({
    author:'张爱玲',
    age:'40',
    books:['book1','book2','book3']
  });

  // 定义一个计算属性
  const hasBook = computed(()=>{
    return bookObj.books.length > 0 ? 'Yes':'No'
  })


  const authorInfo = computed({
  // getter
  get() {
    return bookObj.author + ' ' + bookObj.age 
  },
  // setter
  set(newValue) {
    [bookObj.author, bookObj.age ] = newValue.split(',,,')
  }
})

 const changeFullName=()=>{
  authorInfo.value = {
     author:'大明星',
    age:'100',
  }
}
</script>
```


## 2.4.watchEffect
watchEffect 函数用来监听响应式数据的变化。它接收一个参数，并返回一个包含该参数的响应式数据。
## 2.5.watch
watch 函数用来监听响应式数据的变化。它接收两个参数，并返回一个包含该参数的响应式数据。
# 2.6.toRefs
toRefs 函数用来将响应式数据转换为普通对象。它接收一个参数，并返回一个包含该参数的响应式数据。
# 2.7.toRef
toRef 函数用来将响应式数据转换为普通对象。它接收两个参数，并返回一个包含该参数的响应式数据。
# 2.8.isRef
isRef 函数用来判断一个值是否是一个响应式数据。它接收一个参数，并返回一个包含该参数的响应式数据。
# 2.9.isReactive
isReactive 函数用来判断一个值是否是一个响应式数据。它接收一个参数，并返回一个包含该参数的响应式数据。

# 3.生命周期
## 3.1.beforeCreate
在组件创建之前执行。

## 3.2.created
在组件创建之后执行。

## 3.3.beforeMount
在组件挂载到 DOM 前执行。

## 3.4.mounted
在组件挂载到 DOM 后执行。

## 3.5.beforeUpdate
在组件更新前执行。

## 3.6.updated
在组件更新后执行。

## 3.7.beforeDestroy
在组件销毁前执行。

## 3.8.destroyed
在组件销毁后执行。

