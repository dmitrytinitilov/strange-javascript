# navigator, screen, location

navigator.platform

navigator.userAgent


**Получение координат**

```js
var x = document.getElementById("demo");

function getLocation() {
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition);
    } else { 
        x.innerHTML = "Geolocation is not supported by this browser.";
    }
}

function showPosition(position) {
    x.innerHTML = "Latitude: " + position.coords.latitude + 
    "<br>Longitude: " + position.coords.longitude; 
}
```


**screen**
    width - ширина экрана
    height - высота экрана

```html    
<script>  
    width=document.body.clientWidth; // ширина  
    height=document.body.clientHeight; // высота  
    alert ("Разрешение окна клиента: "+width+"x"+height);  
</script>  
```

**location**
    location.href=URL
    
```js    
	location.href = "mailto:someone@example.com"; 
```
будет пытаться открыть почтовый клиент

location.assign - перенаправляет на текущую страницу

location.replace

location.reload

```js
	location.reload();
             assign()
             replace()
```

```js
document.getElementById("demo").innerHTML =
"Page location is " + window.location.href;
```

**document**

document.activeElement

**history**

.back()<BR>
.forward<BR>
.go(-1) (равносильно back)<BR>

**pushState** – добавляет записи в историю. Первый параметр содержит объект, который говорит о состоянии

```js
history.pushState({foo: 'bar'}, 'Title', '/baz.html')
```
**оnpopstate** – срабатывает при изменении history (нельзя отменить действие кнопки back с помощью prevent default)
в event onpopstate передается свойство state

```js
window.onpopstate = function(event) {
  alert("location: " + document.location + ", state: " + JSON.stringify(event.state));
};
```

replaceState – заменяет текущее состояние stateObject

Изначально в history хранится пустой объект  {}, вот его то и неплохо при запуске страницы поменять

**Плавный скроллинг к заданному месту на странице**

https://css-tricks.com/snippets/jquery/smooth-scrolling/


**Практика:**

1. Сделать так, чтобы при изменении размеров окна, нам выводились его текущие размеры
