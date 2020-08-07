# Timers, timeouts, EventEmitter

Когда вызывается функция, она заливается в стек вызовов с текущим контекстом. После return она удаляется. Когда мы вызваем асинхронные функции, они попадают в отдельное место и выполнение основного кода продолжается. Когда случается событие возврата, функция-callback попадает в стек вызовов.

Время таймера задается по логике "не менее количества переданных миллисекунд". Мы можем блокировать его исполнение синхронным кодом. Тяжелая операция отодвинет их.

```code 

// можно добавлять параметры, они попадут в аргументы лямбды
setTimeout((a) => {
  console.log('callback');
}, 0, 'hello!')

```

SetInterval создает постоянно исполняемый таймер через n миллисекунд.

```code

const t = setInterval(() => {
  //удаление таймера
  clearInterval(t)
})

```

nextTick in Node js. Самый быстрый отложенный вызов. Выполняется строго после основного кода.

```code
process.nextTick(() => {
  console.log(``);
})
```

Порядок исполнения:
* setTimeout
* setInterval
* callbacks
* idle, prepare
* poll - возвращение данных из операционной системы, устройств ввода и вывода
* setImmediate
* close callbacks

.ref и .unref - ручное управление таймером. .ref - ожидание .unref - мгновенное выполнение.
.enroll(timer, 1000) - активация таймера, timer.active(timer) - активация.

## EventEmitter

Событие с коллбэком и именем события. Абстракция, шина событий.
Пример:

```code 
const emitter = () => {
  const events = {};
  return {
    on: (name, fn) => {
      const event = events[name];
      if (event) event.push(fn);
      else events[name] = [fn];
    },
    emit: (name, ...date) => {
      const event = events[name];
      if (event) event.forEach(fn => fn(...data));
    }
  }
}


```
