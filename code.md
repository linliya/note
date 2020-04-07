#### 得到当月天数
```
let d = new Date(year, month+1, 0);
let dayCount = d.getDate();
```

```
const getValue = <T, U extends keyof T>(obj: T, keys: U[]) => {
  return keys.reduce((prev: T, cur: U) => {
    cur in obj && (prev[cur] = obj[cur]);
    return prev;
  }, {} as T);
};
```
