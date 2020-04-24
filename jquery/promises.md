# Promises


```js
var div = $( "<div>" );
 
div.promise().done(function( arg1 ) {
  // Will fire right away and alert "true"
  alert( this === div && arg1 === div );
});
```

```js
$( "button" ).on( "click", function() {
  $( "p" ).append( "Started..." );
 
  $( "div" ).each(function( i ) {
    $( this ).fadeIn().fadeOut( 1000 * ( i + 1 ) );
  });
 
  $( "div" ).promise().done(function() {
    $( "p" ).append( " Finished! " );
  });
});
```