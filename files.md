fs.lstat() - дает информацию о файле в зависимости от файловой системы

```javascript

  fs.lstat('путь к файлу', (err, stat) => {});
```

Можно создать экземпляры функций, например, в итерации через bind() (частично примененные)

```javascript
  fn.bind(null, arg);
```

Слежка за изменением файла.

```javascript
  fs.watch('путь к файлу', (event, file) => {
    console.log('Файл изменен');
  });
```
Работа с файлами через промисы и стримы.

```javascript
 const main = async () => {
  const stream = fs.createReadStream('путь к файлу','utf8');
  for await (const chunk of stream) {
    console.log(chunk);
  }
  
  const data = await fs.promises.readFile('путь к файлу','utf8');
  console.log(data);
 }

```
