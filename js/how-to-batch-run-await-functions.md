# How to batch run await functions?

## Run all the batch functions at a time

> Promise.All

```js
const [result1, result2] = await Promise.all([asyncFunction1(), asyncFunction2()]);
```

## Run all the batch functions one by one

> for loop. notice: we can not use forEach here, because forEach does not support async function.

```js
for (const asyncFunction of [asyncFunction1, asyncFunction2]) {
    await asyncFunction();
}
```
