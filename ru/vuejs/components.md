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

