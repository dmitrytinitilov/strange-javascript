# Мемоизация

```js
var fibonacci = (function () { // Self-executing anonymous function
    var memo = [0, 1];         // local variable within anonymous function
    var fib = function (n) {   // actual fib function (takes one argument)
        var result = memo[n];
        if (typeof result !== 'number') {
            result = fib(n - 1) + fib(n - 2);
            memo[n] = result;
        }
        return result;
    };
    return fib; // return fib (fibonacci is now set to the function fib //defined above, which takes one argument)
}());

for(var i = 0; i <= 10; i += 1) {
    document.writeln('// ' + i + ': ' + fibonacci(i));
}
```

////////////////

```js
var memoizer = function(memo,formula) {
	var recur = function(n) {
		var result = memo[n];
        if (typeof result!== 'number'){
        	result = formula(recur,n);
        	memo[n]= result;

		}
		return result;
	}
	return recur;
}


var fibonacci = memoizer([0,1], function(recur,n){
	return recur(n-1)+recur(n-2);
});
```

Практика:

1. Построить функцию факториал через memoizer
2. Построить решение задачи про пешку через memoizer