# HadTeam(原 FWNT) Git Commit Protocol · HadTeam Git 提交协议

> 版本(Version): v1.3-pre
>
> 时间(Time): 2022-5-15 18:46:27 (UTC+8)

### 概述

准许本协议的所有的 git commit 应该形如下方

````
[Type] Title
zh:
1.

en:
1.

破坏性修改说明:
BEEAKING CHANGE:

Translation: 
````

````
[Type]: Title
zh:
1.

en:
1.

破坏性修改说明:
BEEAKING CHANGE:

Translation: 
````


### Title

此处的Title必须明确说明此次提交的主要内容 若有多个重要的模块可用 `|` 分割

### Git Commit 类型(Type)

#### 常用

1. `Feat`: 此次提交包含新的特性

2. `Fix`: 此次提交用于解决已经发现的问题(包括但不限于 `issue`)

3. `Style`: 此次提交用于规范代码格式, 没有功能上的改动 (修改文档的格式,请使用`Docs`)

4. `Clean`: 同`Style`，但是包括清理 Debug 代码或者冗余代码(包括但不限于 实现了部分功能但是没有引用的代码 已经正式弃用的代码), **不能与`Style`叠加使用**

5. `Refactor`: 此次提交用于修改代码形式, 没有功能上的改动(包括但不限于 移动文件或某些目录)
- 如果移动的目录为子模块目录, 请使用`Change`
  
- 如果仅仅是修改小段的代码格式, 或者修改缩进, 请使用`Style`
  
6. `Docs`: 修改项目文档 (包括但不限于 `README.md` `JavaDoc` `PHPDoc`)

7. `Change`: 修改项目结构 (包括但不限于重新设计项目目录 分离子模块)

此类类型**不推荐但可以叠加使用**, 叠加时将重要的前置, 例如`[Feat&Refactor] Add HTTP download module and refactor HTTP header generator | 添加 HTTP 下载模块并重构 HTTP Header 生成器`

#### 用于表述状态的类型

此类类型**建议与常用类型叠加使用**, 例如`[Init&Feat] Upload the existing basic function files | 初始化并上传已存在的基础功能文件`

1. `Init`: 本次提交为此存储库的第一次提交, 或者为分支的第一次提交
2. `Release`: 本次提交, 用于生成`Release`级别的发布文件, 可包括已经构建的二进制文件等
3. `Pre-release`: 本次提交, 用于生成`Pre-release`级别的发布文件, 不建议但可包括已经构建的二进制文件等

#### 自定义类型

自定义类型**仅仅可以用于特殊情况**, 使用之前建议提前提交申请, 或者在存储库主`README.md`文件添加`Custom commit Type Intro`(或`自定义提交类型说明`)


### 破坏性说明(BREAKING CHANGE)

**一般提交无需此声明,请慎用破坏性说明**

如果出现此声明, 表示此提交后的版本, 与此提交之前的版本不兼容

包括但不限于下列情况

1. 多次`Change`后, 结构大幅度与之前不相同
2. 修改`api`, 使之前的`api`不适用于此版本
3. 修改项目方向, 即使没有破坏性情况, 也需要破坏性声明, 用于标记存档

### 关于双语提交

如果应用了此提交协议, 请使用`简体中文 zh_CN` 与 `English(United States) en_US` (方便起见, 下文使用中文 英文进行代替) 进行编写

**在大多数情况下, 请使用双语提交或者使用英语提交**

#### 标题(Title)与主体(Body)

顺序是: 

- **标题**: 英文先 中文后
- **主体**: 中文先 英文后

#### 翻译说明(Translation)

我们**允许使用翻译器**来转换文本为双语, 但是保险起见, 请将使用的翻译器填写在`Translation`一栏

这样查看者可以用更加平滑的方式转译内容

比如, 使用了谷歌翻译, 那么应该如此:

```````
Translation: By Google Translate
```````

推荐使用谷歌中国的谷歌翻译 [translate.google.cn](https://translate.google.cn)