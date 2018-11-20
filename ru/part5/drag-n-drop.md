# Drag-n-Drop

Создадим картинку и блок

```html
<div style="width:100px;height:100px;background:red" id="block" >
</div>

<img src="gull.jpg">
```

Давайте попробуем перетащить эти объекты. Перетаскивание не удается, но не удается по разному. Обратите внимание, что картинка все-таки перетаскивается, но возвращается назад. В то время как блок просто никак не реагирует.

Чтобы исправить эту ситуацию допишем в наш блок атрибут draggable="true"

```html
<div style="width:100px;height:100px;background:red" id="block" draggable="true">
</div>

<img src="gull.jpg">
```


Теперь давайте сделаем два DIV'a

**drag_object** и **dropzone**

```html
<!DOCTYPE HTML>
<html>
<head>
<style>
#drag_object {
width:100px;
height:100px;
border:1px solid #aaaaaa;
background:cornflowerblue;
}
#dropzone {
background:grey;
width:500px;
height:500px;
}
</style>

</head>
<body>
<div id="dropzone"></div>
<br>
<div id="drag_object" draggable="true" ondragstart="event.dataTransfer.setData('text/plain',null);" >
</div>

<script>

var dragged = null;

function dragStart(event) {
	dragged = event.target;
	// сохраняем ссылку на перетаскиваемый объект

	console.log('dragstart');
}
drag_object.addEventListener('dragstart',dragStart,false);


function dragOver(event) {
	console.log('dragover');
	event.preventDefault();
	//отменяем обработчик по умолчанию, который блокирует ondrop
}

function drop(event) {
	event.preventDefault(); //обработчик по умолчанию пытается перейти по ссылке

	console.log('drop');
	//event.target в этом событии содержит ссылку на место, куда "кидают" перетаскиваемый объект
	if ( event.target.id == "dropzone" ) {
        event.target.appendChild( dragged );
    }
}

//теперь установим обработчики на dropzone'у
dropzone.addEventListener('dragover',dragOver,false);
dropzone.addEventListener('drop',drop,false);

</script>
</body>
</html>
```

**ev.dataTransfer.setData("text", ev.target.id);**


```html
<!DOCTYPE HTML>
<html>
<head>
<style>
    #drag_object {
        width:100px;
        height:100px;
        border:1px solid #aaaaaa;
        background:cornflowerblue;
    }
    
    #dropzone {
        background:grey;
        width:500px;
        height:500px;
    }
    
</style>
<script>

function drag_start(ev) {

    ev.dataTransfer.setData("text", ev.target.id);
    //сохраняем id перетаскиваемого объекта в dataTransfer
}

function drag_over(ev) {
    ev.preventDefault();
    //отменяем действие по умолчанию
}


function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
</script>
</head>
<body>

<div id="dropzone" ondrop="drop(event)" ondragover="drag_over(event)"></div>

<br>
<div id="drag_object" draggable="true" ondragstart="drag_start(event)" >
</div>
</body>
</html>
```


Без dataTransfer перетаскивание не будет работать в Firefox!

**Интересное чтиво:**

Простой пример
https://developer.mozilla.org/en-US/docs/Web/Events/dragstart

http://www.html5rocks.com/en/tutorials/dnd/basics/<BR>
http://html5doctor.com/native-drag-and-drop/<BR>
https://learn.javascript.ru/drag-and-drop<BR>

Наложение эффектов при перетаскивании<BR>
http://www.kryogenix.org/code/browser/custom-drag-image.html

Перетаскивание файлов
http://www.thecssninja.com/javascript/gmail-dragout

Чтобы срабатывал стандартный обработчик объект должен быть draggable. Картинки и так являются draggable объектами
Нам нужно поставить preventDefault у dragover и drop

Перетаскивание элемента по экрану
http://stackoverflow.com/questions/6230834/html5-drag-and-drop-anywhere-on-the-screen
Реализация http://jsfiddle.net/robertc/kKuqH/


**Практика:**

1. Есть две области. Перетаскиваем объект из одной в другую

2. Есть область, есть много объектов. При перетаскивании объектов в область, номер в блоке увеличивается.
3. Перетащить объект в произвольное место

4. Сделать ползунок

5. Редактор ToDo-листов

6. Игра Civilization Wars


