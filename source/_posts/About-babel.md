---
title: About Babel
date: 2017-12-10 23:07:59
categories:
    - 工程化
tags:
    - babel
    - AST
    - plugins
---

## 什么是Babel
Babel是一个编译器。像大多数编译器一样他的编译过程有三个阶段：`parsing`、`transforming`和`generation`。

![](/images/ast.png)
1. parsing阶段： 根据代码转换成一棵抽象语法树(AST)。
1. transforming阶段：对第一步生成的抽象语法树进行操作。
1. generation阶段：根据操作后的语法树生成新的代码。

> 关于抽象语法树的分析(AST)，我们可以使用[astexplorer.net](https://astexplorer.net/)。

## 预设(presets)
preset可以理解为是plugin的集合。一个preset通常包含一个及以上的plugin。

### 官方提供的presets
- [evn](https://babeljs.io/docs/plugins/preset-env/)
- [es2015](https://babeljs.io/docs/plugins/preset-es2015/)
- [es2016](https://babeljs.io/docs/plugins/preset-es2016/)
- [es2017](https://babeljs.io/docs/plugins/preset-es2017/)
- [react](https://babeljs.io/docs/plugins/preset-react/)
- [flow](https://babeljs.io/docs/plugins/preset-flow/)

> 每一个年份的preset可以编译当年被批准的那些语法，`babel-preset-env`包含了每年被TC39批准进入ECMAScript标准最新的语法，还有一些第三方的preset可以在[npm上](https://www.npmjs.com/search?q=babel-preset)发现。

### 实验阶段的presets(stage-x)
> 这里说的实验阶段的preset指的是preset里面的feature处于实验阶段，而不是preset处于实验阶段。

TC39根据阶段对提案，分为以下五类：
- [stage-0](https://babeljs.io/docs/plugins/preset-stage-0/) - 稻草人(*Strawman*)。组织成员或者注册开发者提交的建议。
- [stage-1](https://babeljs.io/docs/plugins/preset-stage-1/) - 提案(*Proposal*)。筛选出来的提案。在这个阶段的feature就表明TC39愿意花时间去做这个事情。
- [stage-2](https://babeljs.io/docs/plugins/preset-stage-2/) - 草案(*Draft*)。主要的语法和API已经完成，剩下一些修修补补的工作。
- [stage-3](https://babeljs.io/docs/plugins/preset-stage-3/) - 候选(*Candidate*)。这个阶段提案里面的描述的语法和API全部实现并完成浏览器的实现。
- stage-4 - 完成(*Finished*)。准备纳入到下一版ECMAScript标准的发布中。

> 注意: 没有stage-4这个preset，因为它已经将要已经纳入到新的标准中

## plugins






