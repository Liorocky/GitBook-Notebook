# JavaScript 判空封装方法

```javascript
/**
 * 判空
 * @param {*} val 
 */
export const isEmpty = val => {
  // null or undefined
  if (val == null) return true;

  if (typeof val === 'boolean') return false;

  if (typeof val === 'number') return !val;

  if (val instanceof Error) return val.message === '';

  switch (Object.prototype.toString.call(val)) {
    // String or Array
    case '[object String]':
    case '[object Array]':
      return !val.length;

      // Map or Set or File
    case '[object File]':
    case '[object Map]':
    case '[object Set]': {
      return !val.size;
    }
    // Plain Object
    case '[object Object]': {
      return !Object.keys(val).length;
    }
  }

  return false;
}

/**
 * 判不空
 * @param {*} val 
 */
export const isNotEmpty = val => {
  return !isEmpty(val)
}
```

