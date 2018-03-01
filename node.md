### Node 定时器
- node提供了4个定时器，分别是
  - setTimeout()
  - setInterval()
  - setImmediate() (node独有的)
  - process.nextTick() (node独有的)

#### 例子
```
setTimeout(() => console.log(1));

setImmediate(() => console.log(2));

process.nextTick(() => console.log(3));

Promise.resolve().then(() => console.log(4));

(() => console.log(5))();

运行结果：

5
3
4
1
2
```
#### 分析
- 异步任务可以分为两种
  - 追加在本轮循环的异步任务
  - 追加在次轮循环的异步任务
  > 本轮循环一定早于次轮循环，而process.nextTick和Promise属于本轮循环，Promise又叫微任务，会在process.nextTick之后执行,只有前一个队列全部清空后才会执行下一个队列

- 例子

```
process.nextTick(() => console.log(1));

Promise.resolve().then(() => console.log(2));

process.nextTick(() => console.log(3));

Promise.resolve().then(() => console.log(4));

1
3
2
4
```
####  本轮循环总结
  - 同步任务
  - process.nextTick()
  - 微任务

#### 次轮循环
- 事件循环的六个阶段（依次执行）
  - timers
  - I/O callbacks
  - idle, prepare
  - poll
  - check
  - close callbacks

1. setTimeout()和setInterval()在timer阶段执行
2. setImmediate在check阶段执行
> 但是setTimeout()和setImmediate的实际执行顺序不确定，这是因为setTimeout的第二个参数默认为0。但是实际上，Node 做不到0毫秒，最少也需要1毫秒，根据官方文档，第二个参数的取值范围在1毫秒到2147483647毫秒之间。也就是说，setTimeout(f, 0)等同于setTimeout(f, 1)。

  > 实际执行的时候，进入事件循环以后，有可能到了1毫秒，也可能还没到1毫秒，取决于系统当时的状况。如果没到1毫秒，那么 timers 阶段就会跳过，进入 check 阶段，先执行setImmediate的回调函数。
