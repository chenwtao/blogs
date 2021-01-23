+++
title="yarn workspace"
authors = ["winter"]
date="2021-01-21 21:10:00"
+++

项目地址:[workspace-demo](https://gitee.com/simod/notes/tree/master/workspace-demo)
用来对一系列相互耦合比较大、又相互独立的子项目进行管理。

##### Monorepo vs Multirepo？

Multirepo 是比较传统的做法，即每一个 package 都单独用一个仓库来进行管理，Monorep 是把所有相关的 package 都放在一个仓库里进行管理，每个 package 独立发布。
![02a9fd14ba0f5cf1dd96274ea3eba9535c8.jpg](https://oscimg.oschina.net/oscnet/02a9fd14ba0f5cf1dd96274ea3eba9535c8.jpg)
而 yarn workspace 则是 Monorep 解决方法之一。(其他工具: [Lerna](https://github.com/lerna/lerna) ）

##### 最终项目结构

workapce-b 依赖于 workapce-a，最终的 workapce-b 和 workapce-a 都被安装在根目录下的 node_mudules。

```
workspace-demo
    ├── package.json
    ├── packages
    │   ├── workspace-a
    │   │   ├── node_modules
    │   │   ├── index.js  #测试代码
    │   │   └── package.json
    │   └── workspace-b
    │       ├── node_modules
    │       ├── index.js  #测试代码
    │       └── package.json
    ├── yarn-error.log
    └── yarn.lock
```

##### 如何使用

按照上面给的目录结构创建项目

##### package.json

```
{
  "name": "workspace-demo",
  "version": "1.0.0",
  "private": true,
  "workspaces": [
    "packages/*"
  ]
}
```

##### workspace-a/package.json

```
{
  "name": "workspace-a",
  "version": "1.0.0",
  "dependencies": {
    "cross-env": "5.0.5"
  }
}
```

##### workspace-a/index.js

```
const obj = {
    name: "simod",
    age: 18
}
module.exports = obj;
```

##### workspace-b/package.json

```
{
  "name": "workspace-b",
  "version": "1.0.0",
  "dependencies": {
    "cross-env": "5.0.5",
    "workspace-a": "1.0.0"
  }
}
```

##### workspace-b/index.js

```
const obj = require("workspace-a");
console.log(obj)
```

##### Run

```
$ node packages/workspace-b/index.js
{ name: 'simod', age: 18 }
```

输出正确结果则表示测试成功
