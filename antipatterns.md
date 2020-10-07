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

```
