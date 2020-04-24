# Типы узлов в DOM

DOM-объект еще также называют узлом. Согласно спецификации есть 12-ть типов узлов. Нам понадобятся узлы всего лишь трех типов

 .nodeType==1 - html-элемент, то есть узел образованный тегом
 
 .nodeType==3 - текстовый узел

 .nodeType==8 - комментарии
 
 ```html
 
 <div id="block">
 </div>
 
 <script>
 var type =document.getElementById("block").nodeType;
 var nodeName =document.getElementById("block").nodeName;
 console.log(type);// выведет 1
 console.log(nodeName);// выведет DIV
 console.log(tagName);// выведет DIV
 </script>
 
 ```
 

**Практика:**

1. Есть блоки в перемешку с текстом - вывести nodeType всех элементов body

