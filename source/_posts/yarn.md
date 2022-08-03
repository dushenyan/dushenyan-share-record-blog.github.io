---
title: yarn
date: 2022-07-31 22:54:50
categories: '配置工具'
cover: 'https://i.ytimg.com/vi/7n467QmiANM/maxresdefault.jpg'
---

## YARN是什么

---

Yarn 是 Facebook, Google, Exponent 和 Tilde 开发的一款新的 JavaScript 包管理工具。 你可以通过它使用全世界开发者的代码，或者分享自己的代码。代码通过包（package）（或者称为模块（module））的方式来共享。 一个包里包含所有需要共享的代码，以及描述包信息的文件，称为package.json。它的优点是更快、更安全、更可靠。它的主要特性有离线模式、确定性、网络性能、多注册、网络恢复能力、扁平模式以及 Emoji。就像我们可以从官方文档了解那样，它的目的是解决这些团队使用 npm 面临的少数问题.
<a name="Sst42"></a>
## <br />官网指引

---

中文：[https://yarn.bootcss.com/](https://yarn.bootcss.com/)<br />英文：[https://classic.yarnpkg.com/en/docs/install#windows-stable](https://classic.yarnpkg.com/en/docs/install#windows-stable)
<a name="K3F9g"></a>
## 优点

---

快速：Yarn 缓存了每个下载过的包，所以再次使用时无需重复下载。 同时利用并行下载以最大化资源利用率，因此安装速度更快。<br />可靠：使用详细、简洁的锁文件格式和明确的安装算法，Yarn 能够保证在不同系统上无差异的工作。<br />安全：在执行代码之前，Yarn 会通过算法校验每个安装包的完整性。
<a name="x2CsK"></a>
## 安装

---

<a name="BGC1w"></a>
### 在window上安装

- 下载安装包安装  

[点我下载Yarn安装包](https://link.juejin.cn?target=https%3A%2F%2Fclassic.yarnpkg.com%2Flatest.msi)，你将下载到一个 .msi文件，当它运行时会指引你将 Yarn 安装到 Windows 上。如果你使用此安装程序，需要先安装 [Node.js](https://link.juejin.cn?target=https%3A%2F%2Fnodejs.org%2F)。

- 通过Chocolatey安装

[Chocolatey](https://link.juejin.cn?target=https%3A%2F%2Fchocolatey.org%2F) 是一个 Windows 专用的软件包管理工具。 请按照此 [说明](https://link.juejin.cn?target=https%3A%2F%2Fchocolatey.org%2Finstall) 安装 Chocolatey 。安装 Chocolatey 之后，你就可以在控制台执行如下命令安装 Yarn 了
> choco install yarn 

- 通过 Scoop 安装

[Scoop](https://link.juejin.cn?target=http%3A%2F%2Fscoop.sh%2F) 是一个用于 Windows 的基于命令行的安装工具。 请按照此 [说明](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Flukesampson%2Fscoop%2Fwiki%2FQuick-Start) 安装 Scoop 。Scoop 安装后，你就可以在控制台执行如下命令安装 Yarn 了
> scoop install yarn 

<a name="sp3WV"></a>
### 在linux上安装

- 官网脚本执行安装
> curl -o- -L https://yarnpkg.com/install.sh | bash -s -- --nightly 

- 通过npm安装
> npm install -g yarn

<a name="lYfVd"></a>
## 常用命令

---

【1】初始化新项目
> yarn init -y 

【2】添加依赖包
> yarn add [package] // 会自动安装最新版本，会覆盖指定版本号 
> yarn add [package] [package] [package] // 一次性添加多个包 
> yarn add [package]@[version] // 添加指定版本的包 
> yarn add [package]@[tag] // 安装某个tag（比如beta,next或者latest）  

【3】将依赖项添加到不同依赖项类别<br />不指定依赖类型默认安装到dependencies里，你也可以指定依赖类型分别添加到 devDependencies、peerDependencies 和 optionalDependencies
> yarn add [package] --dev 或 yarn add [package] -D // 加到 devDependencies yarn add [package] --peer 或 yarn add [package] -P // 加到 peerDependencies yarn add [package] --optional 或 yarn add [package] -O // 加到 optionalDependencies  

【4】升级依赖包
> yarn upgrade [package] // 升级到最新版本
>  yarn upgrade [package]@[version] // 升级到指定版本
>  yarn upgrade [package]@[tag] // 升级到指定tag  

【5】移除依赖包
> yarn remove [package] // 移除包  

【6】安装package.json里的包依赖，并将包及它的所有依赖项保存进yarn.lock
> yarn 或 yarn install // 安装所有依赖 
> yarn install --flat // 安装一个包的单一版本
>  yarn install --force // 强制重新下载所有包 
> yarn install --production // 只安装生产环境依赖  

【7】发布包
> yarn publish  

【8】运行脚本
> yarn run // 用来执行在 package.json 中 scripts 属性下定义的脚本  

【9】显示某个包的信息
> yarn info [package] // 可以用来查看某个模块的最新版本信息  

【10】缓存
> yarn cache 
> yarn cache list // 列出已缓存的每个包 
> yarn cache dir // 返回全局缓存位置 
> yarn cache clean // 清除缓存

<a name="bMJZQ"></a>
## npm 与 yarn相关比较

---

npm存在一些 **历史遗留**问题，请看下图：<br />![](https://cdn.nlark.com/yuque/0/2022/png/1427114/1643166233222-2ffd3f53-08c7-4433-96ea-d9d625321cfd.png#clientId=uc7358c1a-99aa-4&from=paste&id=ua21782ed&margin=%5Bobject%20Object%5D&originHeight=305&originWidth=647&originalType=url&ratio=1&status=done&style=none&taskId=u1ad4ef81-1c06-46ff-b9bc-408d535e732)

> 比如说你的项目模块依赖是图中描述的，@1.2.1代表这个模块的版本。在你安装A的时候需要安装依赖C和D，很多依赖不会指定版本号，默认会安装最新的版本，这样就会出现问题：比如今天安装模块的时候C和D是某一个版本，而当以后C、D更新的时候，再次安装模块就会安装C和D的最新版本，如果新的版本无法兼容你的项目，你的程序可能就会出BUG，甚至无法运行。这就是npm的弊端，而yarn为了解决这个问题推出了yarn.lock的机制，这是作者项目中的yarn.lock文件。

<a name="U6Mq7"></a>
### npm模块的依赖
yarn.lock文件格式<br />![](https://cdn.nlark.com/yuque/0/2022/png/1427114/1643166253209-efb3ccbf-a445-4d8e-b17b-417e47c175a6.png#clientId=uc7358c1a-99aa-4&from=paste&id=u072a76a7&margin=%5Bobject%20Object%5D&originHeight=313&originWidth=955&originalType=url&ratio=1&status=done&style=none&taskId=u20ffbeab-7603-4ed1-bd2f-b1482ab3c84)

大家会看到，这个文件已经把依赖模块的版本号全部锁定，当你执行yarn install的时候，yarn会读取这个文件获得依赖的版本号，然后依照这个版本号去安装对应的依赖模块，这样依赖就会被锁定，以后再也不用担心版本号的问题了。其他人或者其他环境下使用的时候，把这个yarn.lock拷贝到相应的环境项目下再安装即可。<br />注意：这个文件不要手动修改它，当你使用一些操作如yarn add时，yarn会自动更新yarn.lock。
<a name="uBfSh"></a>
## 扩展

---

1. **使用yrm工具管理一些npm源**

安装
> yarn global add yrm

查看可用源
> yrm ls

选择源
> yrm use yarn

2. **快速删除node_modules 手动删除真的很慢：**

安装： 
> npm install rimraf -g

使用：
> rimraf node_modules

rimraf是node的一个包，可以快速删除node_modules，再也不用等半天了

<a name="Aj9GL"></a>
## yarn 和 npm 命令对比
| NPM | Yarn | 说明 |
| --- | --- | --- |
| npm init | yarn init | 初始化某个项目 |
| npm install/link | yarn install/link | 默认安装依赖 |
| npm install taco --save | yarn add taco | 安装某个依赖并默认保存到package |
| npm uninstall taco --save | yarn remove taco | 移除某个依赖 |
| npm install taco --save -dev | yarn add taco -dev  | 安装某个开发时的依赖 |
| npm update taco --save | yarn upgrade taco | 更新某个依赖项目 |
| npm install taco --global | yarn global add taco | 安装某个全局依赖项目 |
| npm publish/login/logout | yarn publish/login/logout | 发布/登录/退出 |
| npm run/test | yarn run/test | 运行某个命令 |



---

<br />相关网站<br />[https://www.cnblogs.com/bingcola/p/15183634.html](https://www.cnblogs.com/bingcola/p/15183634.html)<br />[https://blog.csdn.net/yw00yw/article/details/81354533](https://blog.csdn.net/yw00yw/article/details/81354533)<br />[https://www.jianshu.com/p/0657050f29ff](https://www.jianshu.com/p/0657050f29ff)

