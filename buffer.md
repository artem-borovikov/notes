Буффер

```javascript
  // выделение пямяти
  // шестнадцатеричный формат вывода

  // будет заполнено нулями
  const b1 = Buffer.alloc(1024);
  console.log(b1);
  
  // не очищенный кусок пямяти, выше скорость
  const b2 = Bugger.alloUnsafe(1024);
  console.log(b2)
  
  // создание буффера из массива или из строки
  const b3 = Buffer.from([1,2,3,4]);
  console.log(b3);
  
  const b4 = Buffer.from('Hello');
  
  // можно выводить в разном формате
  console.log(b.toString('hex')); // base64, utf8, binary
  
```
