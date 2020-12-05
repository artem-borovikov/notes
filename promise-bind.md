# Сокращение кода на промисах

```javascript

// можно сократить код, вызывая функцию прямо в аргументе
  Promise.resolve()
    .then(readConf.bind(null, 'conf.txt'))
    .then(query.bind(null, 'select 1;'));
    

```
