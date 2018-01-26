- 新建一个2g大小的测试文件
```
dd if=/dev/zero of=test count=2048 bs=1m
```
- 计算一个文件的哈希值(摘要算法)
```
shasum + 文件名
```
```
md5 + 文件名
```
- 计算完成一个操作需要的时间
```
time + 操作
```
例如：
```
time shasum test
```
