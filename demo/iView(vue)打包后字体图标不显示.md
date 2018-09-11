## 问题描述：webpack打包后发现iView 字体图标不显示  
## 解决方案：build/webpack.prod.conf.js 这个文件里面,```extract```默认是true ，改成false ，重新打包一下就好啦
```
module: {
    rules: utils.styleLoaders({
      sourceMap: config.build.productionSourceMap,
      extract: false,
      usePostCSS: true
    })
  },
```
