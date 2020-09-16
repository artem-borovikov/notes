# Async / Await

Если такая функция вызывается без await, то возвращается заресолвленный или нет промис. Awaut распаковывает промисы и ждет, пока они не заресолвятся.

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

Await ждет любой объект, упакованный или не упакованный в промис.

```code
...
const a = await 10;

```

## Асинхронные итерации

```code

const range = {
  start: 1,
  end: 10,
  [Symbol.asyncIterator]() {
    let value = this.start;
    return {
      next: () => new Promise(resolve => {
        setTimeout(() => {
          resolve({
            value,
            done: value++ === this.end + 1
          });
        }, 0);
      })
    };
  }
};

console.dir({ range });

(async () => {

  for await (const number of range) {
    console.log(number);
  }

})();

```

