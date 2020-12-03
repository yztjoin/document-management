# Commonjs

```javascript
导入
const moudleA = require('./moudleA')

导出
moudle.exports = moudleA.someFunc
```

优点：

- 通过NPM发布的大多数第三方模块都采用了Commonjs

缺点在于这样的代码无法再浏览器中运行必须通转换工具转换成标准的ES5

几种渲染方式

SSR:服务端渲染，服务端吐出有数据的HTML页面

CSR:客户端渲染，指的是客户端使用ajax请求请求数据拼装页面，此时页面是在客户端拼接好的

前端同构应用：指的是再服务端执行虚拟DOM，此时前端和服务端的渲染层时同一套代码，因为服务端使用和前端相同的虚拟dom的原理拼接HTML模板，所以前端同构应用一般也是SSR