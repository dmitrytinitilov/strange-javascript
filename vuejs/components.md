#Компоненты

Напишем наш компонент

```js
// register
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
// create a root instance
new Vue({
  el: '#example'
})
```

Такой компонент будет менять вот такой html-код

```js
<div id="example">
  <my-component></my-component>
</div>
```

в вот такой

```js
<div id="example">
  <div>A custom component!</div>
</div>
```

**Продвинутый вариант**


```js
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">Счётчик кликов — {{ count }}</button>'
})
```

```html
<div id="components-demo">
  <button-counter></button-counter>
</div>
```

```js
new Vue({ el: '#components-demo' })
```

**v-for и компоненты**



```html
<blog-post
  v-for="post in posts"
  v-bind:key="post.id"
  v-bind:title="post.title"
></blog-post>
```
данные мы возьмем из posts в объекте Vue 


```js
new Vue({
  el: '#blog-post-demo',
  data: {
    posts: [
      { id: 1, title: 'My journey with Vue' },
      { id: 2, title: 'Blogging with Vue' },
      { id: 3, title: 'Why Vue is so fun' }
    ]
  }
})
```

**Прослушивание событий в родительских компонентах**


```js
Vue.component('blog-post', {
  props: ['post'],
  template: `
    <div class="blog-post">
      <h3>{{ post.title }}</h3>
      <button>
        Увеличить размер текста
      </button>
      <div v-html="post.content"></div>
    </div>
  `
})
```

Допустим мы хотим, чтобы компонент реагировал на события

```html
<blog-post
  ...
  v-on:enlarge-text="postFontSize += 0.1"
></blog-post>
```

Нам нужно добиться, чтобы кнопка генерировала событие при нажатии на нее

```html
<button v-on:click="$emit('enlarge-text')">
  Увеличить размер текста
</button>
```

**Импорт из внешнего файла**


Мы можем делать импорт из файлов .js или .vue


```js
import ComponentA from './ComponentA'
import ComponentC from './ComponentC'

export default {
  components: {
    ComponentA,
    ComponentC
  },
  // ...
}
```

**Свойства компонента**

```js
Vue.component('blog-post', {
  // camelCase in JavaScript
  props: ['postTitle'],
  template: '<h3>{{ postTitle }}</h3>'
})
```

В html свойства передаются в шашлычном регистре

```html
<blog-post post-title="hello!"></blog-post>
```

**Полезное чтиво:**

1. Пример calculator PWA
https://github.com/fh48/vue-calculator-pwa

2. Получение данных из компонента
https://stackoverflow.com/questions/43677645/vuejs-how-to-get-data-from-vue-component

3. Однофайловые компоненты
https://vue-loader.vuejs.org/ru/spec.html#%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5

**Практика:**

1. Написать компонент для товара
