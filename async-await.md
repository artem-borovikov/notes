# Async / Await

Если такая функция вызывается без await, то возвращается заресолвленный или нет промис.

```code
async function () {
  // функция возвращает данные, обернутые в промис, если возвращается промис, повторно он не оборачивается.
  return 1;
}
```
## Асинхронные конструкторы
```code
class Coming {
  constructor() {
    return new Promise(resolve => setTimeout() => {
      resolve(this);
    }, DAY_OF_JUDGMENT - Date.now());
  }
}

// функцию, которая возвращает промис, тоже можно вызывать через await
(async () => {
  const secondComing = await new Coming();
  console.dir(secondComing);
})()

```


