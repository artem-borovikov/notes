# Асинхронность

## Callback-функции

Под капотом любых асинхронных функций callback, программирование через колбэк наиболее производительно. Обычно первым аргументом в колбэк передается ошибка. Но callback приводит к большим вложенностям - callback-hell.

```code
(callback) => callback(data)
(...args, callback) => callback(err, data)
```

## Event Emitter

события триггерят друг друга. Основной недостаток - функции должны знать друг о друге.

```code

const ee = new EventEmitter();
const f1 = () => ee.emit('step1');
const f2 = () => ee.emit('step2');

ee.on('step1', f2)

```

## Promise

Вместо возврата данных мы возвращаем объект, который подписан на получение данных. Успешность придет в один коллбэк, неуспешность в другой. Ошибка может прийти во второй колбэк then или catch.

```code

new Promise((resolve, reject) => {
    resolve(data);
    reject(new Error(...));
})
    .them(result => {}, error => {})
    .catch(err => {})



// параллельное исполнение, общий then происходят, когда ///////// промисы ресолвятся

Promise.all([])

```

## async/await

Функции объявляются ключевым словом. Если функция возвращает значение, оно автоматически оборачивается в Promise.resolve() или в Promise.reject().

## Functor + Chaining + composition

Последовательное исполнение с навешиванием колбэков.

```code

    const c1 = chain()
        .do(func1)
        .do(func2);

    c1();

```
