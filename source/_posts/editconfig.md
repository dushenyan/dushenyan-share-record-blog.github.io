---
title: editconfig
date: 2022-07-31 22:54:50
categories: 配置工具
---

## EDITORCONFIG是什么

---

当大家在公司工作时，不可能永远是一个人维护一个项目，当多个人参与一个项目，每个人使用的编辑器不一样，代码风格自然也不一样，那么如何让使用不同编辑器的开发者能够轻松惬意的遵守最基本的代码规范呢？最后终于找到了[editorConfig](https://editorconfig.org/)这个东东，发现在这里配置的代码规范规则优先级高于编辑器默认的代码格式化规则。如果我没有配置editorconfig，执行的就是编辑器默认的代码格式化规则；如果我已经配置了[editorConfig](https://editorconfig.org/)，则按照我设置的规则来，从而忽略浏览器的设置。<br />[EditorConfig](https://editorconfig.org/)包含一个用于定义代码格式的文件和一批编辑器插件，这些插件是让编辑器读取配置文件并以此来格式化代码。
<a name="KIKI5"></a>
## 安装

---

VSCode安装非常简单，直接在插件市场搜索[EditorConfig for vs code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig) 安装就行了，安装完毕记得重启编辑器。
<a name="KGXPk"></a>
## 使用

---

- 在当前项目根目录下添加.editorconfig文件
- 安装EditorConfig扩展 
- 全局安装或局部安装editorconfig依赖包(npm install -g editorconfig | npm install -D editorconfig)
- 打开需要格式化的文件并手动格式化代码（Mac OS ：shift+option+f  Windows ：shift+alt+f）

可以通过资源管理器侧栏的上下文菜单右键选择Generate .editorconfig，然后这个目录下面就会创建出一个.editorconfig文件了，当然如果团队里有已经配置好的这个文件，直接复制过来就行了。
<a name="Gly5U"></a>
## 配置

---

<a name="Nl7vs"></a>
#### 常用属性配置 
1、root<boolean>  :  是否是顶级配置文件，设置为true的时候才会停止搜索.editorconfig文件<br />2、charset<"latin" | "utf-8" | "utf-8-bom" | "utf-16be" | "utf-16le">     :    文件编码格式<br />3、indent_style<"tab" | "space">    ：  缩进方式<br />4、indent_size<number>    ：    缩进大小<br />5、end_of_line<"lf" | "cr" | "crlf">    ：    换行符类型<br />6、insert_final_newline<boolean>   ：     是否让文件以空行结束<br />7、trim_trailing_whitespace<boolean>  ：   是否删除行尾空格 <br />8、max_line_length<number>    ：    最大行宽。
<a name="FfkKp"></a>
#### 常用文件名匹配
1、*                  匹配除/之外的任意字符<br />2、**                 匹配任意字符串<br />3、?                 匹配任意单个字符<br />4、[name]                 匹配name字符 <br />5、[!name]                 不匹配name字符<br />6、[s1,s2,s3]                 匹配给定的字符串<br />7、[num1..num2]                 匹配num1到mun2直接的整数

目前VSCode并不是所有属性都支持，所以只需要配置下面几个属性即可：

- indent_style
- indent_size
- tab_width
- end_of_line （保存时）
- insert_final_newline （保存时）
- trim_trailing_whitespace （保存时）
<a name="gI2oo"></a>
## 使用建议

---

这个插件只能简单的配置一些规范，并不能完全满足需求，所以还需要其它代码检查工具配合使用，比如说：ESLint或StyleLint，统一代码风格。
<a name="W6j5F"></a>
## .editorconfig文件规格

---

```markdown
# EditorConfig helps developers define and maintain consistent
# EditorConfig帮助开发人员定义和维护一致性
# coding styles between different editors and IDEs
# 不同编辑器和ide之间的编码样式
# 打开需要格式化的文件并手动格式化代码（Mac OS ：shift+option+f  Windows ：shift+alt+f）
# editorconfig.org
# editorconfig顶级配置文件,停止向上寻找配置文件
root = true

[*]
# change these settings to your own preference
# 将这些设置更改为您自己的首选项
# 缩进样式=空格
indent_style = space
# 缩进大小=2
indent_size = 2

# we recommend you to keep these unchanged
# 我们建议你保持这些不变
# 换行符类型 = lf
end_of_line = lf
# 字符集=utf-8
charset = utf-8
# 删除行尾空格 = 是
trim_trailing_whitespace = true
# 插入最后一行=真
insert_final_newline = true

[*.md]
# 删除行尾空格 = 否
trim_trailing_whitespace = false

[package.json]
# 缩进样式=空格
indent_style = space
# 缩进大小=2
indent_size = 2
```
<a name="DWUdc"></a>
## 
<a name="gKxWQ"></a>
## 相关网站

---

[https://www.cnblogs.com/jiaoshou/p/11252055.html](https://www.cnblogs.com/jiaoshou/p/11252055.html) * 
