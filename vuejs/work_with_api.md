# Работа с API

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script src="https://unpkg.com/vue@2.3.4"></script>
</head>
<body>
    <div id="app">
        <ul>
            <li v-for="product in products">
            {{product.price}} {{product.name}}
            </li>
        </ul>
    </div>

    <script type="">
        var app = new Vue({
          el: '#app',
          data: {
            products: []
          },
          created() {

              fetch('products.json')
              .then(response=>response.json())
              .then(products=>this.products = products)
              .catch(function(error) {
                  console.log(error);
              });
          }
        })
    </script>
</body>
</html>
```

Создаем products.json, чтобы протестировать подгрузку данных

```json
[{"name":"iPhone","price":3000},{"name":"Android","price":2000}]
```