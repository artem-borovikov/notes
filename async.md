# Конспекты

## Callback-функции

Под капотом любых асинхронных функций callback, программирование через колбэк наиболее производительно. Обычно первым аргументом в колбэк передается ошибка. Но callback приводит к большим вложенностям - callback-hell.

```code
(callback) => callback(data)
(...args, callback) => callback(err, data)
```

### Event Emitter

события триггерят друг друга

```code

const ee = new EventEmitter();
const f1 = () => ee.emit('step1');
const f2 = () => ee.emit('step2');

ee.on('step1', f2)

```
