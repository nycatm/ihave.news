---
title: 前端技术学习札记
date: 2017-02-14 21:07:07
tags:
- js
categories:
- js
---

## 模态对话框（Modal）加载远程内容
Bootstrap默认提供的Modal是无法实现加载远程功能的，当出现重复的内容则需编写多遍，或使用`iframe`来实现。其实这个功能可以使用`Sco.js`提供的Modal增强插件，即可轻松实现Modal加载远程内容。具体可查看[sco.modal.js](/post/front-end/scojs.html)

## 页面局部刷新功能
页面中的部分元素需要刷新，或者部分链接需要通过Ajax获取远程数据，此时没有必要再手写一套`$.ajax`，`Sco.js`的Ajax增强插件也提供了该功能实现。具体可查看[sco.ajax.js](/post/front-end/scojs.html)

<!--more-->

## Node.js & NPM
[Node.js](https://nodejs.org/en/)

[NPM淘宝映像](https://npm.taobao.org/)
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
[Webpack官网](https://webpack.bootcss.com/)

[Webpack安装说明](https://webpack.bootcss.com/get-started/install-webpack/)
```
npm install webpack@beta -g
```
Webpack使用
```
webpack app/index.js dist/bundle.js
```
或使用配置文件`webpack.config.js`：
```js
module.exports = {
  entry: './app/index.js',
  output: {
    filename: 'bundle.js',
    path: './dist'
  }
}
```
```
webpack --config webpack.config.js
```
> 如果存在 webpack.config.js 文件，webpack 命令默认加载此文件。

通过 npm 使用 webpack
```js
{
  ...
  "scripts": {
    "build": "webpack"
  },
  ...
}
```
```
npm run build
```
