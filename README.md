# HowLongDidItTake

Measure elapsed time.

- Simple. Lightweight. TypeScript friendly. Small bundling size.
- Format the result. Choose `s`, `ms` or `ns`. Even automatically.
- Limit the precision or the fraction digits.
- Available on both Node.js and browsers (maybe).


## CLI

Use `hldit` command.

```text
hldit (any command)
```

```text
hldit (any *.js filepath)
```

- On CLI, the unit is determined automatically and the precision is always `2`. I.e. just like `autoUnit(2)` via the API (see below).
- If a given JavaScript file has a default export of any `Promise` type, `hldit` awaits until the `Promise` is resolved.


## API

### Import

```js
import * as hldit from "howlongdidittake";
```

### Stopwatch

```js
const getElapsedTime = hldit.stopwatch.autoUnit(2); // give precision
console.log(getElapsedTime());
```

```js
const getElapsedTime = hldit.stopwatch.withUnit("ms", 2); // give unit & fraction digits
console.log(getElapsedTime());
```

### Measure

```js
const anyAsyncCallback = () => Promise.resolve();

const measure = hldit.measure.autoUnit(2); // give precision
measure(anyAsyncCallback).then((elapsedTime) => console.log(elapsedTime));
```

```js
const anyAsyncCallback = () => Promise.resolve();

const measure = hldit.measure.withUnit("ms", 2); // give unit & fraction digits
measure(anyAsyncCallback).then((elapsedTime) => console.log(elapsedTime));
```

`hldit.measure` has functions for sync callbacks as well.
