## 创建一个包含当前URL的对象

Creates an object containing the parameters of the current URL.

- Use `String.prototype.match()` with an appropriate regular expression to get all key-value pairs.
- Use `Array.prototype.reduce()` to map and combine them into a single object.
- Pass `location.search` as the argument to apply to the current `url`.


## JavaScript
```javascript
const getURLParameters = url =>
  (url.match(/([^?=&]+)(=([^&]*))/g) || []).reduce(
    (a, v) => (
      (a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1)), a
    ),
    {}
  );
```

## Examples
```javascript
getURLParameters('google.com');
// {}
getURLParameters('http://url.com/page?name=Adam&surname=Smith');
// {name: 'Adam', surname: 'Smith'}
```
