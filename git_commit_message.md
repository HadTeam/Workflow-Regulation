# HadTeam（原 FWNT） Git Commit Protocol · HadTeam Git 提交协议

> 版本（Version）：v1.4-pre
>
> 时间（Time）：2023-1-6 11:01:21 （UTC+8）

### 概述

准许本协议的所有的 git commit（下文简述为提交）应该形如下方

```text
[<Type>] <Title>
<Body>

<Breaking Change>

<Translation Info>
```

#### 解释
- `<Type>`：提交类型概括
- `<Title>`：提交标题
- `<Body>`：提交主体概括（可选）
- `<Breaking Change>`：破坏性说明（可选）
- `<Translation Info>`：机器翻译（下文简称为机翻）说明（可选）

### 国际化
如果应用了此提交协议，请使用 `简体中文 zh_CN` 与 `English（United States） en_US` （下文使用中文、英文分别进行代替，双语则同时代指） 进行编写

**在大多数情况下，请使用双语提交或者使用英文提交**

如果使用双语提交，请在主体中分别使用 `zh` `cn` 来标识语言。

#### 放置顺序
按顺序依次向后排列：`en` `zh`

#### 翻译说明（Translation Info）

我们**允许使用机翻**来转换文本到多语言，以允许查看者更轻松的阅读提交。

鉴于机翻质量的参差不齐，保险起见，请将机翻信息填写在 `Translation` 一栏。


例如，使用了谷歌翻译，应填写以下内容
```text
Translation: By Google Translate
```

[//]: # (推荐使用谷歌翻译 translate.google.com )

### 标题（Title）
标题须明确此次提交的主要内容，若有多个主要内容可用分隔符或使用语义进行分割。

注意：
- 多语言提交时，需要用分隔分割两语言的标题语句，例如 `[Feat] Add navbar | 添加导航条`
- 标题不需要句末点号

#### 使用分隔符进行分割
分隔符为 `|` ，如为英语需要开头大写。
#### 使用语义进行分割
可以使用如 `and` ` also` `和` `以及` 的词语进行分割，需要保证语句遵循语法。

### 主体（Body）
应使用列表或纯语言详细描述提交内容。
使用双语提交时，应该使用语言标识，例如：
```text
en:
- Add a button
- Remove useless code

zh:
- 添加了一个按钮
- 清除无用代码
```
否则，可以忽略语言标识，例如：
```
- Add a button
- Remove useless code
```

#### 列表
使用有序列表和无序无序皆可，需要重点尽可能在前。

### 类型（Type）
#### 常用
1. `Feat`：添加了新的特性
2. `Fix`：此次提交用于解决已经发现的问题，包括但不限于 `issue`
3. `Style`：此次提交用于规范代码格式，没有功能上的改动
   - 如果仅仅是修改文档的格式，请使用 `Docs`
   - 如果是修改大段代码，如移动函数的位置，请使用 `Refactor`
4. `Clean`：同 `Style`，但是包括清理 Debug 代码或者冗余代码（包括但不限于实现了部分功能但是没有引用的代码、已经正式弃用的代码），**不能与 `Style` 叠加使用**
5. `Refactor`：此次提交用于修改代码形式，没有功能上的改动，包括但不限于移动文件或某些目录
   - 如果移动的目录为子模块目录，请使用 `Change`
   - 如果仅仅是修改小段的代码，或者修改缩进，请使用 `Style`
6. `Docs`：修改项目文档，包括但不限于修改 `README.md` `JavaDoc` `PHPDoc`
7. `Change`：修改项目结构，包括但不限于重新设计项目目录、分离子模块
8. `Chore`：更改依赖库，包括但不限于使用了新的三方库
   - 如果仅仅是修改了项目内对子模块的调用，请使用 `Change`

常用类型**不推荐但可以叠加使用**，叠加时将重要的前置，例如 `[Feat&Refactor] Add HTTP download module and refactor HTTP header generator | 添加 HTTP 下载模块并重构 HTTP Header 生成器`。

#### 用于表述状态的类型
此类型**建议与常用类型叠加使用**，例如 `[Init&Feat] Upload the existing basic function files | 初始化并上传已存在的基础功能文件`。

1. `Init`：本次提交为此存储库的第一次提交，或者为分支的第一次提交
2. `Release`：本次提交，用于生成 `Release` 级别的发布文件，可包括已经构建的二进制文件
3. `Pre-release`：本次提交，用于生成 `Pre-release` 级别的发布文件，不建议可以包括已经构建的二进制文件

#### 自定义类型
自定义类型**仅仅用于特殊情况**，使用之前建议与同组成员交流，或者在存储库主分支的 `README.md` 中添加 `Custom Commit Type Intro` 或 `自定义提交类型说明` 栏目。

### 破坏性说明（Breaking Change）
格式例如
```text
BREAKING CHANGE: <Content>
```
建议在 `<Content>` 内详细说明原因和改动！

**一般提交无需此声明，请慎用**！
如果出现此声明，表示此提交后的版本，与此提交之前的版本出现不兼容，包括但不限于如下情况
1. 进行重构，结构与之前大范围不相同
2. 修改 API，使之前的 API 不适用于此版本
3. 修改项目开发方向，用于标记存档
