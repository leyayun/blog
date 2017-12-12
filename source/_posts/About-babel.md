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
Babel是一个编译器。像大多数编译器一样，它的编译过程有三个阶段：`解析(parsing)`、`转换(transforming)`和`生成(generation)`。

![](/images/ast.png)
1. 解析阶段：根据代码转换成一棵抽象语法树(AST)。
1. 转换阶段：对第一步生成的抽象语法树进行操作。
1. 生成阶段：根据操作后的语法树生成新的代码。

> 关于抽象语法树(AST)的分析，我们可以使用[astexplorer.net](https://astexplorer.net/)来进行。

## 预设(presets)
preset可以理解为是plugin的集合。一个preset通常包含一个及以上的plugin。

### 官方提供的presets
- [env](https://babeljs.io/docs/plugins/preset-env/)
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
除了可以通过preset来引入一些预设的插件，我们也可以单独引入我们想要使用的插件。babel的插件可以根据功能分为三类：

1. 转换插件(Transform Plugins) - 此类作用于编译的第二阶段转换阶段，用于对AST语法树进行转换。
1. 混合插件(Misc Plugins) 
1. 语法插件(Syntax Plugins)

## 如何使用presets/plugins
1. 安装要使用的preset/plugin
```
npm install babel-preset-env --save-dev
```

1. 在`.babelrc`中配置preset/plugins
```
{
  "presets": [
    ["env", {

    }],
    "stage-0"
  ],
}
```






