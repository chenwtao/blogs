+++
title="nvm nrm 初探"
authors = ["winter"]
date="2021-01-22"
+++

npm 的全称是 Node Package Manager 是 JavaScript 世界的包管理工具,并且是 Node.js 平台的默认包管理工具。通过 npm 可以安装、共享、分发代码,管理项目依赖关系。

##### 常用命令

```
npm install 安装模块
npm uninstall 卸载模块
npm update 更新模块
npm outdated 检查模块是否已经过时
npm ls 查看安装的模块
npm init 在项目中引导创建一个package.json文件
npm help 查看某条命令的详细帮助
npm root 查看包的安装路径
npm config 管理npm的配置路径
npm cache 管理模块的缓存
npm start 启动模块
npm stop 停止模块
npm restart 重新启动模块
npm test 测试模块
npm version 查看模块版本
npm view 查看模块的注册信息
npm adduser  用户登录
npm publish 发布模块
npm access 在发布的包上设置访问级别
npm package.json的语法

```

##### nvm

- 为解决 node 的版本管理而生
- 不支持 windows，windows 可以使用 n 或者 nvm-windows

##### 安装

采用 curl 安装

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
```

完成后会出现~/.nvm,然后设置环境变量,如果安装了 zsh，在~/.zshrc 添加,否则在~/.bash_profile 或者~/.profile 添加(如果没有~/.bash_profile 或~/.profile 新建一个)

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
```

然后新开一个 bash，或者 source  配置文件,使配置生效。

##### 常用命令

```
npm  install   -g   nrm //安装
nvm install ## 安装指定版本，可模糊安装，如：安装v6.2.0，既可nvm install v6.2.0，又可nvm install 6.2
nvm uninstall ## 删除已安装的指定版本，语法与install类似
nvm use ## 切换使用指定的版本node
nvm ls ## 列出所有安装的版本
nvm ls-remote ## 列出所以远程服务器的版本（官方node version list）
nvm current ## 显示当前的版本
nvm alias ## 给不同的版本号添加别名
nvm unalias ## 删除已定义的别名
nvm reinstall-packages ## 在当前版本node环境下，重新全局安装指定版本号的npm包
```

##### nrm

- nrm 是一个用来管理 npm 源的工具

```
$ nrm ls
  npm -------- https://registry.npmjs.org/
  yarn ------- https://registry.yarnpkg.com/
  cnpm ------- http://r.cnpmjs.org/
* taobao ----- https://registry.npm.taobao.org/
  nj --------- https://registry.nodejitsu.com/
  npmMirror -- https://skimdb.npmjs.com/registry/
  edunpm ----- http://registry.enpmjs.org/
```

##### 安装

```
npm install -g nrm # 如果报权限错误，使用sudo npm install -g nrm安装
```

##### 常用命令

- [私有源可以用 cnpm 架设](https://segmentfault.com/a/1190000000368906)

```
nrm ls # 列出npm源
nrm use <registry> #选择源
nrm add  <registry> <url> [home] #增加源
nrm delete <registry> #删除源
nrm test #测速
```

##### 参考

[nrm](https://www.npmjs.com/package/nrm)

[node 版本管理工具 nvm-Mac 下安装及使用](https://segmentfault.com/a/1190000004404505)

[npm npx nvm nrm 你分的清吗](https://juejin.im/post/5bf51eda51882508851b5c22)
