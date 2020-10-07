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


```
5. Магические строки. 
```code

const str = '\x1b[2:10H'; // escape-последовательность

// лучше

const pos = (row, col) => `\x1b[${row}:${col}H`;


```

