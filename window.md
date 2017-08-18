- 获取window下用户默认工作路径

 ```
function getUserHome() {
  return process.env[(process.platform == 'win32') ? 'USERPROFILE' : 'HOME'] + '\\pfile';
}
```
