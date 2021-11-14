# 查询URL中指定的参数值
### method

```javascript
const queryUrlParam = (name, url = window.location.href) => {
    name = name.replace(/[\[\]]/g, '\\$&');
    const regex = new RegExp('[?&]' + name + '(=([^&#]*)|&|#|$)');
    const results = regex.exec(url);
    if (!results) {
        return null;
    }
    if (!results[2]) {
        return '';
    }
    return decodeURIComponent(results[2].replace(/\+/g, ' '));
};
```
### usage
```javascript
const testUrl = 'https://www.baidu.com/?id=1&user=iCodingShow';
queryUrlParam('id', testUrl); // '1'
queryUrlParam('user', testUrl); // 'iCodingShow'
```
