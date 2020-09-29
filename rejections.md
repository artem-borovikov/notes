```code

// случается, когда rejection не обработан, может произойти ошибочно, т.е. до того, как произойдет следующиее событие

process.on('unhandledRejection', (reason, promise) => {
  console.log({ unhandledRejection: { reason, promise }})
});

// когда rejection обработано

process.on('rejectionHandled', promise => {
  console.log({ rejectionHandled: { promise }})
});


```
