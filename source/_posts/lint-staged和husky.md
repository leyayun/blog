---
title: 使用lint-staged和husky在pre-commit阶段做代码检查
date: 2017-11-16 19:44:45
categories:
    - 工程化
tags:
    - lint-staged
    - husky
    - eslint
    - stylelint
    - pre-commit
    - lint
---


## 为什么要使用lint-staged和husky

良好的编码规范是保障项目质量和可维护性的重要因素，通常我们是通过`eslint`和`stylelint`这些lint工具来检查代码的规范与否。我们假设你已经在你的项目里使用了eslint和stylelint等lint工具，那我们何时来运行这些lint来检查你的代码呢？为了防止那些不符合规范的代码溜进你的代码仓库，我们需要在git的pre-commit阶段来检测你的代码。


### 什么是lint-staged

[lint-staged](https://github.com/okonet/lint-staged)可以帮助我们在git staged阶段的文件上执行linters，简单点来说就是当我们运行`eslint`或`stylelint`的命令时，它只会检查我们通过`git add`添加到暂存区的文件。这样可以避免我们每次检查都把整个项目的代码都检查一遍，毕竟这样太蠢了。如果你对git中文件的状态不是很熟可以看下面的这张图：

![](/images/lifecycle.png)
<!--more-->

### 什么是husky

[husky](https://github.com/typicode/husky)可以让git hooks的使用变得更简单方便。当我们运行`npm install --save-dev husky`安装的过程中，它会在我们项目根目录下面的`.git/hooks`文件夹下面创建`pre-commit`、`pre-push`等hooks。这些hooks可以让我们直接在`package.json`的`script`里运行我们想要在某个hook阶段执行的命令。
```
// package.json
{
  "scripts": {
    "precommit": "npm test",
    "prepush": "npm test",
    "...": "..."
  }
}
```

## 现在让我们来使用lint-staged和husky在pre-commit阶段执行lintters

> 假设你已经安装并配置好了`eslint`或`stylelint`这类代码检查工具

1. `npm install --save-dev lint-staged husky`
1. 编辑你的`package.json`文件:

```
{
  "scripts": {
    "precommit": "lint-staged"
  },
  "lint-staged": {
    "src/**/*.{js,jsx}": ["eslint --fix", "git add"],
    "src/**/*.{css,less}": ["stylelint --fix", "git add"]
  }
}
```

lint-staged和husky的详细配置，请参考相应的官方文档:
- [lint-staged文档](https://github.com/okonet/lint-staged)
- [husky文档](https://github.com/typicode/husky)