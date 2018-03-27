1. 安装nvm 
curl -o- https://raw.githubusercontent.com/creationix/nvm/<version>/install.sh | bash
安装完成后应重启terminal或者执行以下语句：
```
    source ~/.bashrc 
    (source = .) . ~/.bashrc
```
2. 通过nvm安装并使用node
```
    - nvm install node <version>
    - nvm alias default <version> #指定一个默认的node版本
    - nvm use <version>
```
3. 通过npm 全局安装以下工具
    - git
    - bower，管理前端依赖
    - polymer-cli，能为polymer项目提供方便的功能,(已包含wct)
    - gulp，构建工具
    - eslint及对应插件
    - http-server，很方便的服务器
    - java环境