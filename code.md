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

#### 通过闭包实现单例模式
```
# 第一次执行时会执行let instance = null这一行，之后就是执行return里面的内容
SingleDog.getInstance = (function() {
    // 定义自由变量instance，模拟私有变量
    let instance = null
    return function() {
        // 判断自由变量是否为null
        if(!instance) {
            // 如果为null则new出唯一实例
            instance = new SingleDog()
        }
        return instance
    }
})()
```

### 单例模式应用

> 实现Storage，使得该对象为单例，基于 localStorage 进行封装。实现方法 setItem(key,value) 和 getItem(key)。

```
function StorageBase () {
  StorageBase.prototype.getItem = function (key) {
    return localStorage.getItem(key)
  }
  StorageBase.prototype.setItem = function(key, value) {
    return localStorage.setItem(key, value)
  }
}

const Storage = (function() {
  let instance = null
  return function () {
    if (!instance) {
      instance = new StorageBase()
    }
    return instance
  }
})()
```
