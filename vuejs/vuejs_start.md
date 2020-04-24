# Vue JS Быстрый старт

```html
<!DOCTYPE html>
<html lang="en">
  <meta>
    <meta charset="UTF-8">
    <title>Hello World in Vue.js</title>
  </meta>

  <body>
	
    <div id="hello-world-app">
      <h1>{{ msg }}</h1>
    </div>

    <script src="https://unpkg.com/vue@2.3.4"></script>

    <script>
      new Vue({
        el: "#hello-world-app",
        data() {
          return {
            msg: "Hello World!"
          }
        }
      });
    </script>

  </body>
</html>
```

**Полезное чтиво:**

1. Примеры приложений на vuejs https://tutorialzine.com/2016/03/5-practical-examples-for-learning-vue-js