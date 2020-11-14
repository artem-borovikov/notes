Буффер

```javascript
  // выделение пямяти
  // шестнадцатеричный формат вывода

  // будет заполнено нулями
  const b1 = Buffer.alloc(1024);
  console.log(b1);
  
  // не очищенный кусок пямяти, выше скорость
  const b2 = Bugger.allocUnsafe(1024);
  console.log(b2)
  
  // создание буффера из массива или из строки
  const b3 = Buffer.from([1,2,3,4]);
  console.log(b3);
  
  const b4 = Buffer.from('Hello');
  
  // можно выводить в разном формате
  console.log(b.toString('hex')); // base64, utf8, binary
  
  // можно сложить буфферы
  
  // заполнение буффера буквой А
  const b5 = Buffer.alloc(10).fill('A');
  
  // конкатенация буфферов
  Buffer.concat(b3,b5);
  
 
  // другие методы
  const b6 = Buffer.from('test');
  
  b6.includes('t');  // поиск подстроки
  b6.indexOf('e'); // позиция подстроки
  b6.slice(3,6); // мы можем вырезать кусок
  
  // итерация по буфферу
  for (const char of b6.values()) {
    log(char)
  }
  
  for (const [index, code] of buffer.entries()) {
    const char = String.fromCharCode(code);
    console.log({
      index, 
      code, 
      char
    });
  }
  
```
