## Readable

```javascript

  const rs = fs.createReadStream('путь к файлу', 'utf8');
  
  // как только файл откроется для чтения
  // до этого мы не можем сделать read()
  // readable случается всегда
  rs.on('readable', () => {
    const buffer = rs.read();
    
    // возможно, что вернет null | undefined
    if (buffer) {
      console.log(buffer);
    }
  });
  
  // случается, когда есть данные
  // считывание стрима
  // не вызовется, когда в буффере null
  rs.on('data', chunk => {
    console.log('data');
    console.log(chunk)'
  });

```

## Writable

```javascript

  const ws = fs.createWriteStream('путь у файлу','utf8');
  const gs = zlib.createGzip();

  rs.on('data', chunk => {
    console.log('data');
    ws.write(chunk);
  });

  // простой способо передачи потока - pipe()
  rs.pipe(ws); // автоматически навешивает 'data' и делает write
  rs.pipe(gs).pipe(ws); // склеили потоки, пример - архив
  
  
   rs.on('end', () => {
    console.log('end');
  });
  
  // у этих потоков тоже есть события, мы можем этот файл сложить в буффер
  const buffers = [];
  let buffer = null;
  gs.on('data', buffer => {
    buffers.push(buffer);
  });
  
  gs.on('end', () => {
    buffer = Buffer.concat(buffers);
  });
  
  // этот буффер мы можем отдать, например, по http
  
  ...
    response.writeHead(200, {
      'Content-Encoding':'gzip'
    });
    response.end(buffer);
  ...
  
```
