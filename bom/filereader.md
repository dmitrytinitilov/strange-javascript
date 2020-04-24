# FileReader

https://developer.mozilla.org/ru/docs/Web/API/FileReader/readAsDataURL

http://www.javascripture.com/FileReader


```js
<input type='file' onchange='openFile(event)'>
<script>
  var stateNames = {};
  stateNames[FileReader.EMPTY]   = 'EMPTY';
  stateNames[FileReader.LOADING] = 'LOADING';
  stateNames[FileReader.DONE]    = 'DONE';

  var openFile = function(event) {
    var input = event.target;

    var reader = new FileReader();
    reader.onload = function(){
      console.log('After load: ' + stateNames[reader.readyState]);
    };

    console.log('Before read: ' + stateNames[reader.readyState]);
    reader.readAsDataURL(input.files[0]);
    console.log('After read: ' + stateNames[reader.readyState]);
  };
  
</script>  
```