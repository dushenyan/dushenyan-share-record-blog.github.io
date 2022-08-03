---
title: npm
date: 2022-07-31 22:54:50
categories: '配置工具'
cover: 'https://user-images.githubusercontent.com/29712634/81721690-e2fb5d80-9445-11ea-8602-4b2294c964f3.png'
---

## NPM是什么

---

 包管理器(Package Manager)，npm 最初它只是被称为 Node Package Manager，用来作为Node.js的包管理器。但是随着其它构建工具(webpack、browserify)的发展，npm已经变成了 "the package manager for JavaScript"，它用来安装、管理和分享JavaScript包，同时会自动处理多个包之间的依赖。
<a name="qGhBt"></a>
## 使用场景

---

- 允许用户从NPM服务器下载别人编写的第三方包到本地使用。
- 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用。
- 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。
<a name="iDoa9"></a>
## 安装

---

**新版的nodejs已经集成了npm**<br />Node.js：nodejs分为了**长期支持版**和**当前版本**。<br />Linux中安装nodejs的方法：

- [官网](https://link.jianshu.com?t=https://nodejs.org/en/download/) 下载压缩包解压到/opt目录，修改解压目录的所属用户和组，然后配置环境变量（推荐）；
- 或者使用PPA安装：[How to Install Latest Nodejs & NPM on Ubuntu with PPA - TecAdmin](https://link.jianshu.com?t=https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/#)

**升级现有npm版本**
> npm install npm -g 

貌似也可使用这种方法安装node，但是安装的是当前版本的node而非长期支持版本的node。

<a name="ea4mY"></a>
## npm包安装

---

npm 的包安装分为`本地安装`（local）、`全局安装`（global）两种。
<a name="gWD5G"></a>
#### 本地安装(默认)
npm install <包>   

- 将安装包放在 ./node_modules 下（运行 npm 命令时所在的目录），如果没有 node_modules 目录，会在当前执行 npm 命令的目录下生成 node_modules 目录。
- 可以通过 require() 来引入本地安装的包。
<a name="cg8Kb"></a>
#### 全局安装
npm install <包> -g

- 将安装包放在 /usr/local 下或者你 node 的安装目录。
- 可以直接在命令行里使用。**这是使用全局安装的主要原因**。

使用下面的命令来查看全局的包安装的位置：
> npm prefix -g 

<a name="FilLm"></a>
#### 创建全局链接
如果你希望具备两者功能（本地安装和全局安装的功能），则需要在两个地方安装它或使用 **npm link**。<br />npm link的功能是在本地包和全局包之间创建符号链接。我们说过使用全局模式安装的包不能直接通过 require 使用,但通过 npm link 命令可以打破这一限制。<br />比如我们将 express安装到了全局环境，使用下面的命令可以将其链接到本地环境：<br />npm link express <br />使用 npm link命令还可以将本地的包链接到全局。使用方法是在包目录( package.json 所在目录)中运行 npm link 命令。<br />如果你的项目不再需要该模块，可以在项目目录内使用npm unlink命令，删除符号链接。<br />像gem 或 pip 总是以全局模式安装，使包可以供所有的程序使用，而 npm 默认会把包安装到当前目录下。这反映了 npm 不同的设计哲学。如果把包安装到全局，可以提高程序的重复利用程度,避免同样的内容的多份副本，但坏处是难以处理不同的版本依赖。
<a name="w2Ke6"></a>
## 更换镜像

---

<a name="eXc1d"></a>
#### 淘宝镜像
对于国内的情形，在使用npm安装JS包之前建议先更改npm的镜像。<br />配置 npm 的国内镜像站点为：https://registry.npm.taobao.org 。<br />方法一：在系统的HOME目录新建.npmrc文件并添加 registry = https://registry.npm.taobao.org<br />方法二：你可以使用淘宝定制的 cnpm 命令行工具代替默认的 npm:
> npm install -g cnpm --registry=https://registry.npm.taobao.org //之后即可使用cnpm来安装包 cnpm install <包> 

详情请参考： [淘宝 NPM 镜像](https://link.jianshu.com?t=https://npm.taobao.org/)

<a name="M7UIx"></a>
#### 源镜像
 安装nrm来管理源：
> npm install -g nrm

 查看可以用的源：
> nrm ls

切换源：
> nrm use 源的名称

 测试源的延迟：
> nrm test

 添加源的地址：
> nrm add 源名称 address

PS D:\code\system-learning\font_page\npm_demo> nrm add zz http://127.0.0.1:8080/


<a name="Xi31n"></a>
## 命令

---

查看命令帮助
> npm help 

列出各命令
> npm -l 

查看安装信息
>  npm ls -g   //全局安装信息 
>  npm ls   //列出当前项目中的包

树型结构列出当前项目安装的所有模块，以及它们依赖的模块
> npm list npm list -global npm list vue   加上global参数，会列出全局安装的模块。

查看版本信息
> npm info jquery

 查看更新版本 
> npm outdated jquery 如已经是最新版本，则无提示消息

更新指定模块版本 
> npm update jquery   会根据npm outdataed jquery的wanted的结果来更新，

更新所有版本 
> npm update

升级npm本身的版本 
> npm install -g npm

卸载包
> npm uninstall <包名> 

更新包
>  npm update <包名>   更新当前项目中安装的某个包
>  npm update   //更新当前项目中安装的所有包
>  npm update <包名> -g    //更新全局安装的包

搜索包
> npm search <关键字> 

列出npm的配置
> npm config list -l 

列出bin目录
> npm bin 


<a name="cB7aR"></a>
## 包管理

---

**版本控制**<br />^3.3.1表示的是版本号  <br />格式如下  主版本号.次版本号.修改
```json
"devDependencies": {
    "jquery": "*3.3.1" //允许主版本更新
    "jquery": "^3.3.1" //允许次版本更新
    "jquery": "~3.3.1" //允许bug更新
}
```
**包的管理**

- aplha 版本底层结构还未确定，改动很大的版本
- beta 底层架构已经定好，会哟一些交互上的改动，此版本可以用于内测，公测
- rc 成熟的版本
- realse 稳定的版本，最终版本

**模块管理**
<a name="GFero"></a>
##  package.json

---

当你的项目需要依赖多个包时，推荐使用 package.json。其优点为：

- 它以文档的形式规定了项目所依赖的包
- 可以确定每个包所使用的版本
- 项目的构建可以重复，在多人协作时更加方便
<a name="V9W38"></a>
#### 创建package.json文件

- 手动创建
- 或者 通过 npm init 命令生成遵守规范的 package.json文件

文件中必须包含： name 和 version
<a name="I3Hpo"></a>
#### 指定依赖包
两种依赖包：

- dependencies: 在生产环境中需要依赖的包。通过npm install <packge> --save命令自动添加依赖到文件（或者使用简写的参数 -S）。
- devDependencies：仅在开发和测试环节中需要依赖的包。通过npm install <packge> --save-dev命令自动添加依赖到文件（或者使用简写的参数 -D）。

当然你也可以在文件中手动添加依赖<br />如果其他人也需要这个项目，只需要把这个 package.json 文件给他，然后进行简单的 npm install 即可
<a name="uYrV3"></a>
#### npm 脚本
[npm scripts 使用指南 - 阮一峰的网络日志](https://link.jianshu.com?t=http://www.ruanyifeng.com/blog/2016/10/npm_scripts.html)<br />[npm 模块安装机制简介 - 阮一峰的网络日志](https://link.jianshu.com?t=http://www.ruanyifeng.com/blog/2016/01/npm-install.html)
<a name="kR4yc"></a>
#### npm run
package.json文件有一个scripts字段，可以用于指定脚本命令，供npm直接调用。<br />  "scripts": {     "lint": "jshint **.js",     "test": "mocha test/"   } 
> npm run lint可以运行脚本中的 lint 命令。npm run test可以运行脚本中的 test 命令。

npm run命令会自动在环境变量$PATH添加node_modules/.bin目录，所以scripts字段里面调用命令时不用加上路径，这就避免了全局安装NPM模块。<br />start和test属于特殊命令，可以省略run：
> npm start  npm test 

如果仅仅使用npm run会列出scripts属性下所有的命令：
> npm run 

<a name="PZofP"></a>
## 包管理配置

---

<a name="w4jz6"></a>
#### 设置默认配置
使用 npm set 命令用来设置环境变量。<br />也可以用它来为 npm init设置默认值，这些值会保存在 ~/.npmrc文件中。
> $ npm set init-author-name 'Your name' 
> $ npm set init-author-email 'Your email' 
> $ npm set init-author-url 'http://yourdomain.com' 
> $ npm set init-license 'MIT' 

<a name="ID548"></a>
#### 更改全局安装目录
使用npm config命令可以达到此目的。
> npm config set prefix <目录> 

或者手动在 ~/.npmrc文件中进行配置：
> prefix = /home/yourUsername/npm 

更改目录后记得在系统环境变量 PATH中添加该路径：
> # .bashrc 文件 export PATH=~/npm/bin:$PATH 

<a name="WvCI1"></a>
## 发布包

---

在发布之前,首先需要让我们的包符合 npm 的规范,npm 有一套以 CommonJS 为基础包规范,但与 CommonJS并不完全一致,其主要差别在于必填字段的不同。通过使用 npm init 可以根据交互问答产生一个符合标准的 package.json。<br />也可简单的使用 npm init -y。其中-y（代表yes）<br />该文件是一个符合 npm 规范的 package.json 文件。这里的 index.js 作为包的接口。<br />创建帐号：
> npm adduser 

测试是否取得帐号：
> npm whoami 

发布
> npm publish 

更新包：
> 修改 `version`字段，再重新发布

取消发布：
> npm unpublish 


---

学习资料<br />[NPM 使用介绍 - 菜鸟教程](https://link.jianshu.com?t=http://www.runoob.com/nodejs/nodejs-npm.html) <br />[npm Documentation](https://link.jianshu.com?t=https://docs.npmjs.com/) <br />[如何卸载使用npm链接安装的软件包？](https://link.jianshu.com?t=https://gxnotes.com/article/45185.html) <br />[package.json文件 -- JavaScript 标准参考教程（alpha）](https://link.jianshu.com?t=http://javascript.ruanyifeng.com/nodejs/packagejson.html) <br />[npm模块管理器 -- JavaScript 标准参考教程（alpha）](https://link.jianshu.com?t=http://javascript.ruanyifeng.com/nodejs/npm.html)

相关网站:<br />[https://blog.csdn.net/qq_33051685/article/details/84931218](https://blog.csdn.net/qq_33051685/article/details/84931218)<br />[https://www.jianshu.com/p/60ac7fe6edce](https://www.jianshu.com/p/60ac7fe6edce)<br />[https://www.runoob.com/nodejs/nodejs-npm.html](https://www.runoob.com/nodejs/nodejs-npm.html)<br />[https://zhuanlan.zhihu.com/p/258080852](https://zhuanlan.zhihu.com/p/258080852)

