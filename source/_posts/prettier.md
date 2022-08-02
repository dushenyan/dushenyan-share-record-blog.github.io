---
title: prettier
date: 2022-07-31 22:54:50
categories: '配置工具'
---

## PRETTIER是什么
---

prettier 介绍是一个支持多种语言的 opinionated 代码格式化工具，可以集成到多种编辑器，支持少量的配置。所谓 opinionated，英文翻译为武断的，固执己见的，也就是说 prettier 的配置都是设计好的，不支持自由配置（类似于 Mac，东西都在主板上给你焊死了，不支持自己升级配置）
<a name="GhBxl"></a>
## 原理

---

prettier 的原理很简单，就是把你的代码转化成一个抽象语法树 AST （因为 AST 是跟原本的代码风格无关的），然后根据 AST 将代码按照 prettier 的风格输出即可。想要看看 prettier 的转化过程，可以看 prettier 官方提供的[检测网站](https://prettier.io/playground/)（如果你有 issue 要提交也是先到这个页面复现你的 bug 然后提交链接到 github）。
<a name="oupFq"></a>
## 官网指引

---

中文官网：[https://www.prettier.cn/](https://www.prettier.cn/)<br />在线格式化：[https://prettier.io/playground/](https://prettier.io/playground/)
<a name="QbWv6"></a>
## 安装

---

最基础的使用方式就是使用 yarn 或者 npm 安装，然后在命令行使用。
> npm install --save-dev --save-exact prettier 
> yarn add --dev --exact prettier 

然后在文件夹中创建配置文件和 ignore 文件。关于配置文件支持多种形式：

- 在 package.json 中添加一个 prettier 对象，在内部写入配置。
- 一个 JSON 或 YAML 格式的 .prettierrc 文件。
- 一个 .prettierrc.json, .prettierrc.yml, .prettierrc.yaml, 或 .prettierrc.json5 文件。
- 一个 .prettierrc.js, .prettierrc.cjs, prettier.config.js 或 prettier.config.cjs 文件，文件要用 module.exports exprts 一个对象。
- 一个 prettierrc.toml 文件。
<a name="tVlNs"></a>
## 配置

---

**操作选择在**`**工程目录**`**下进行**<br />**.prettier.js文件创建格式化参考规则**
```json
//此处的规则供参考，其中多半其实都是默认值，可以根据个人习惯改写
module.exports = {
  printWidth: 80, //单行长度
  tabWidth: 2, //缩进长度
  useTabs: false, //使用空格代替tab缩进
  semi: true, //句末使用分号
  singleQuote: true, //使用单引号
  quoteProps: 'as-needed', //仅在必需时为对象的key添加引号
  jsxSingleQuote: true, // jsx中使用单引号
  trailingComma: 'all', //多行时尽可能打印尾随逗号
  bracketSpacing: true, //在对象前后添加空格-eg: { foo: bar }
  jsxBracketSameLine: true, //多属性html标签的‘>’折行放置
  arrowParens: 'always', //单参数箭头函数参数周围使用圆括号-eg: (x) => x
  requirePragma: false, //无需顶部注释即可格式化
  insertPragma: false, //在已被preitter格式化的文件顶部加上标注
  proseWrap: 'preserve', //不知道怎么翻译
  htmlWhitespaceSensitivity: 'ignore', //对HTML全局空白不敏感
  vueIndentScriptAndStyle: false, //不对vue中的script及style标签缩进
  endOfLine: 'lf', //结束行形式
  embeddedLanguageFormatting: 'auto', //对引用代码进行格式化
};
```
**.prettierignore忽略文件格式化**
```makefile
.DS_Store
node_modules
node_modules/**/*
node_modules/**/*.*
/dist


# local env files
.env.local
.env.*.local

# Log files
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*

# Editor directories and files
.idea
.vscode
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?


# 重要的环境依赖文件
package.json
package.lock.json

# 代码格式化插件的配置文件
.prettierrc
.prettierignore

# git忽略文件
.gitignore

# 不对markdown进行格式化, 容易打乱自己编排的样式
*.md
```
<a name="JtDKu"></a>
## 命令

---

**命令行格式化**<br />（1）格式化全部文档
> npx prettier --write .
>  //或 
> yarn prettier --write . 

（2）格式化指定文档
> npx prettier --write src/components/Button.js 
> //或 
> yarn prettier --write src/components/Button.js 

（3）检查文档是否已格式化
> npx prettier --check . 
> //或 
> yarn prettier --check . //检查指定文件同上

<a name="KfD5x"></a>
## 集成

---

<a name="PLga8"></a>
### 利用编辑器插件进行格式化
在编辑器中搜索相应的 Prettier 安装，即可运用编辑器快捷键进行格式化。

| 常见的编辑器 | 对应插件名 |
| --- | --- |
| VS Code | Prettier - Code formatter |
| Emacs | prettier-emacs |
| Vim | vim-prettier |
| Sublime Text | JsPrettier |
| Atom | prettier-atom |

重要提示：编辑器中的 Prettier 格式化规则也可在设置中编写，但实际执行时会以本地规则为优先。

在命令行中使用时非常麻烦的，一般来说我们都是在编辑器中使用 prettier。这里讲一讲我平时在 vscode 中的配置。<br />首先是安装 extension：[prettier – vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)。然后用快捷键 ⇧ + ⌘ + P 来启动 Command palette，找到 format XXX with 然后选择 Configure default formatter，选择 prettier 即可设置为默认的格式化工具。<br />想要在保存时自动格式化，我们可以用 ⌘ + , 打开设置页面，找到 format on save 打上勾即可。<br />这些配置都是可以在 setting.json 中进行配置的，这里我放上我的关于 prettier 的 vscode 配置。
```javascript
{
    "editor.formatOnSave": true,
    //prettier
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[less]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    /*  prettier的配置 */
    "prettier.printWidth": 100, // 超过最大值换行
    "prettier.tabWidth": 4, // 缩进字节数
    "prettier.useTabs": false, // 缩进不使用tab，使用空格
    "prettier.semi": true, // 句尾添加分号
    "prettier.singleQuote": true, // 使用单引号代替双引号
    "prettier.proseWrap": "preserve", // 默认值。因为使用了一些折行敏感型的渲染器（如GitHub comment）而按照markdown文本样式进行折行
    "prettier.arrowParens": "avoid", //  (x) => {} 箭头函数参数只有一个时是否要有小括号。avoid：省略括号
    "prettier.bracketSpacing": true, // 在对象，数组括号与文字之间加空格 "{ foo: bar }"
    "prettier.disableLanguages": ["vue"], // 不格式化vue文件，vue文件的格式化单独设置
    "prettier.endOfLine": "auto", // 结尾是 \n \r \n\r auto
    //"prettier.eslintIntegration": false, //不让prettier使用eslint的代码格式进行校验
    "prettier.htmlWhitespaceSensitivity": "ignore",
    "prettier.ignorePath": ".prettierignore", // 不使用prettier格式化的文件填写在项目的.prettierignore文件中
    "prettier.jsxBracketSameLine": false, // 在jsx中把'>' 是否单独放一行
    "prettier.jsxSingleQuote": false, // 在jsx中使用单引号代替双引号
    "prettier.requireConfig": false, // Require a 'prettierconfig' to format prettier
    "prettier.trailingComma": "es5", // 在对象或数组最后一个元素后面是否加逗号（在ES5中加尾逗号）
}
```
setting.json 中的配置是对所有项目生效的，你也可以在项目中创建 prettier 的配置文件进行覆盖。
<a name="wQ8om"></a>
## 配合其它工具使用

---

通常我们会使用 Linter 来检查代码的规范，比如 ESLint、TSLint、Stylelint。他们在某些规则上会与 Prettier 相互矛盾。<br />解决这个问题我以 ESLint 为例，安装 eslint-config-prettier，并在 ESLint 的配置文件的 extends 添加 prettier。
```javascript
// .eslintrc.json
{····
  "extends": ["eslint:recommended", "prettier"]
}
```
TSLint 和 Stylelint 如法炮制。具体可参看以下项目：

- [tslint-config-prettier](https://github.com/prettier/tslint-config-prettier)
- [stylelint-config-prettier](https://github.com/prettier/stylelint-config-prettier)

<a name="NQrtP"></a>
## 其它
如果你不喜欢 Prettier 将 HTML 、Vue 模板 或者 JSX 等的默认配置 "whitespace-sensitive": "css" 格式化时把一对尖括号分为两行：
```html
<!-- input -->
<span class="dolorum atque aspernatur">Est molestiae sunt facilis qui rem.</span>
<div class="voluptatem architecto at">Architecto rerum architecto incidunt sint.</div>

<!-- output -->
<span class="dolorum atque aspernatur"
  >Est molestiae sunt facilis qui rem.</span
>
<div class="voluptatem architecto at">
  Architecto rerum architecto incidunt sint.
</div>
```
可以配置 Prettier 的 whitespace-sensitive 选项为 ignore。

<a name="QSRGC"></a>
## 相关网站

---

[https://juejin.cn/post/6938687606687432740](https://juejin.cn/post/6938687606687432740)<br />[https://segmentfault.com/a/1190000012909159](https://segmentfault.com/a/1190000012909159)<br />[https://www.cnblogs.com/fitzlovecode/p/code_formater.html](https://www.cnblogs.com/fitzlovecode/p/code_formater.html)  <br />[https://www.clloz.com/programming/front-end/js/2020/08/31/prettier-eslint/](https://www.clloz.com/programming/front-end/js/2020/08/31/prettier-eslint/)<br />[Prettier中文网](https://www.prettier.cn/)<br />[

](https://juejin.cn/post/6938687606687432740)
