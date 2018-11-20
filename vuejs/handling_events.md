#Обработка событий


```html
<script src="https://unpkg.com/vue@2.3.4"></script>

<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>

<script type="text/javascript">
  var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
}) 
</script>
```

Мы можем генерировать кастомные события с помощью $emit

```html
<script src="https://unpkg.com/vue"></script>

<div id="todo-list-example">
  <input
    v-model="newTodoText"
    v-on:keyup.enter="addNewTodo"
    placeholder="Add a todo"
  >
  <ul>
    <li
      is="todo-item"
      v-for="(todo, index) in todos"
      v-bind:key="todo"
      v-bind:title="todo"
      v-on:remove="todos.splice(index, 1)"
    ></li>
  </ul>
</div>



<script type="text/javascript">
  Vue.component('todo-item', {
  template: `
    <li>
      {{ title }}
      <button v-on:click="$emit('remove')">X</button>
    </li>
  `,
  props: ['title']
})
new Vue({
  el: '#todo-list-example',
  data: {
    newTodoText: '',
    todos: [
      'Do the dishes',
      'Take out the trash',
      'Mow the lawn'
    ]
  },
  methods: {
    addNewTodo: function () {
      this.todos.push(this.newTodoText)
      this.newTodoText = ''
    }
  }
})

</script>

```