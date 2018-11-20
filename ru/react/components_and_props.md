#Компоненты и свойства

Внутри функции Fullname, мы сможем получать доступ к свойствам компонента Fullname через props

```js
function Fullname(props) {
  return <h1>Hello, {props.name} {props.surname}</h1>;
}

const element = <Fullname name="Ostap" surname="Bender"/>;
        
ReactDOM.render(element,
        document.getElementById('mount-point')
);
```

Посмотрите этот пример на Codepen
https://codepen.io/dmitrytinitilov/pen/eRzdWX

**Подробнее:**
https://facebook.github.io/react/docs/components-and-props.html