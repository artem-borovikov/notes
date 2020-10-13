# Антипаттерны

1. Идентификаторы коротки или длинные. Пример cons n = 'Имя' / const nameForSomePerson = 'Имя'
2. Одни имена с разными контекстами.
 
```code 

let name = 'Иван';
name = 'config.js';

```
3. Одинаковое значение, но разные имена.

```code
const file = 'config.js';
const fileName = 'config.js';

// одни и те же имена
const obj = {
 setPassword: () => {},
 assignLogin: () => {}

};

// непрезентабельное имя
const obj1 = {
 exec: (handler) => handler()
};

```
4. Магические числа. Т.е. идем по коду и обнаруживаем захардкоженные значения.

```code
cb(15);

// решение
const INIT_VALUE = 15;
cb(INIT_VALUE);

// исключения - счетчики, -1

i++;


```
5. Магические строки. 
```code

const str = '\x1b[2:10H'; // escape-последовательность

// лучше

const pos = (row, col) => `\x1b[${row}:${col}H`;


```
6. Хардкод
```code

const data = await fs.readFile('file.js', 'utf8');
const lines = data.split('\n');
const str = lines[6];
const fileName = str.substring(34,56);


```
7. Дублирование. Дублирующие фрагменты надо выносить в отдельную функцию.
8. Необдуманный копипаст из гугла.
9. Неоправданные ожидания.

```code 

fs.fileRead('/config.js', (err, data) => {
 // не проверили, что объект
 const config = JSON.parse(data);
 // не проверили, что свойство есть
 const { port } = config;
});



```
10. Чрезмерная защита от дурака. Проверяем все возможные варианты аргументов на вход.
11. Нагромождение функций. Коллбэк-хэлл - частный пример.
