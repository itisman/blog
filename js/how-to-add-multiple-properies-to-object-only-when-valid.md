# How to add multiple properties to the object only when valid

> it would be useful if you don't want to add if the field is undefined.

```js
const a = "a";
const b = "b";
const c = undefined;
const obj = {
    ...(a && { a }),
    ...(b && { b }),
    ...(c && { c }),
};
console.log(obj); // {a: 'a', b: 'b'}
```

it also can work for arrays

```js
const a = "a";
const b = "b";
const arr = [
    ...(a !== undefined ? [{ a }] : []),
    ...(b !== undefined ? [{ b }] : []),
    ...(c !== undefined ? [{ c }] : []),
];
console.log(arr); // [{"a":"a"},{"b":"b"}]
```

## use case

> it can be used in sequelize where condition

```js
async User.findOne({
    where: {
        ...(name && { name }),
        ...(email && { email }),
        ...(phone && { phone }),
    },
})
```

```js
async User.findOne({
    where: {
        [Op.OR]: [
            ...(name && [{ name }]),
            ...(email && [{ email }]),
            ...(phone && [{ phone }]),
        ]
    },
})
```
