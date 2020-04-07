#### 得到当月天数
```
let d = new Date(year, month+1, 0);
let dayCount = d.getDate();
```

#### 获取对象中的某些属性
```
const getValue = <T, U extends keyof T>(obj: T, keys: U[]) => {
  return keys.reduce((prev: T, cur: U) => {
    cur in obj && (prev[cur] = obj[cur]);
    return prev;
  }, {} as T);
};
```
