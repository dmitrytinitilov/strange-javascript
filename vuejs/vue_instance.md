#Экземляр Vue 



```js
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.a === data.a

vm.a = 2
data.a // -> 2

vm.$data === data // -> true
vm.$el === document.getElementById('example') // -> true
// $watch is an instance method
vm.$watch('a', function (newVal, oldVal) {
  // этот callback сработает, когда `vm.a` изменяется
})
```