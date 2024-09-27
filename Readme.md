
# 前端知识积累

## 简介
基于前端知识总结梳理。

## 技术栈
+ [链接](./package.json)

## 功能
+ [x] Git
+ [x] Java
+ [x] Node
+ [x] Vue


## 开发
+ 安装依赖
```js
npm install
```

+ 启动服务
```js
npm run start
```

+ 发布
```js
npm run build
```

+ 添加更新日志
```js
npm run release

// 首次发布版本
npm run release -- --first-release

// 不同版本更新
npm run release-major
npm run release-minor
npm run release-patch

```

+ 预发布版本
```js
// 结果将会标记版本为：1.0.1-alpha.0。
npm run release -- --prerelease alpha

// 指定版本
npm run release -- --release-as 1.1.0
```

+ 跳过更改版本
```js
npm run release -- --skip.bump
```
+ 跳过生成changelog
```js
npm run release -- --skip.changelog
```
+ 跳过提交
```js
npm run release -- --skip.commit
```

### 快速上手
待补充
