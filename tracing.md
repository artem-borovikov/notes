Если ошибка срабатывает в setTimeout - ее трудно отловить, т.к. stack trace показывает не в том месте! Мы не видим последовательность вызываемых функций.

Даже здесь собьется stack trace:
```code

  const f1 = async () => {
    await promise();
    throw new Error('error');
  }

```
