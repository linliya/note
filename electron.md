- 通过spawn命令执行命令行语句，可以设置参数

```
child = spawn('./daemon.exe', [], {
    cwd: currentpath,
    detached: true // 后台开启
  });
```

- 通过electron kill命令可以关闭一个程序

```
child.kill('SIGKILL');
```

- 通过ipcRenderer模块可以给主程序发送消息

```
const ipcRenderer = require('electron').ipcRenderer;

function login() {
  ipcRenderer.send('login');
}
```

- 主程序可以监测渲染程序发过来的信号

```
ipcMain.on('login', function() {
  mb.window.reload();
});
```

- electron 的 dialog模块可以创建一个窗口让用户选择路径

```
dialog.showOpenDialog({
    title: '请设置您的根目录',
    properties: [ 'openDirectory' ]
  }, function(path) {
    ...
  });
```

- electron可以通过node-localstorage保存数据

```
const LocalStorage = require('node-localstorage').LocalStorage;
let storage = LocalStorage('./userdata');

// 获取LocalStorage
function getStorage(key) {
  return storage.getItem(key);
}

// 设置LocalStorage
function setStorage(key, value) {
  return storage.setItem(key, value);
}
```
