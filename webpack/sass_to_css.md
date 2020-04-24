#SASS в CSS

Нам понадобятся модули sass-loader и node-sass

```cmd
npm install sass-loader node-sass webpack --save-dev
```

```json
// webpack.config.js

module.exports = {
    ...
    module: {
        rules: [{
            test: /\.scss$/,
            use: [{
                loader: "style-loader"
            }, {
                loader: "css-loader"
            }, {
                loader: "sass-loader",
                options: {
                    includePaths: ["absolute/path/a", "absolute/path/b"]
                }
            }]
        }]
    }
};
```


**Полезное чтиво:**

1. SASS cheatsheet
https://devhints.io/sass

2. & в SASS
https://css-tricks.com/the-sass-ampersand/

3. Фишки с амперсандом в SASS
https://css-tricks.com/snippets/sass/caching-current-selector-sass/

4. https://ru.stackoverflow.com/questions/653118/%D0%9A%D0%BE%D0%BC%D0%BF%D0%B8%D0%BB%D1%8F%D1%86%D0%B8%D1%8F-sass-%D0%B2-webpack-2-%D0%BF%D1%80%D0%BE%D1%81%D1%82%D0%B5%D0%B9%D1%88%D0%B8%D0%B9-%D1%81%D0%BB%D1%83%D1%87%D0%B0%D0%B9
5. Применение циклов и анимации в SASS
http://jonibologna.com/sass-function-demos/
6. Использование random в SASS
https://muffinman.io/sass-random-and-circle-animation/
