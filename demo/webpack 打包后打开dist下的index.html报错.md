## 问题描述：npm run dev 没报错。是可以正常运行的，npm run build 过程也没报错，但是打开dist   index.html  就报错了

## 解决方法：
### 1、将 ```npm run build```  改成 ```cnpm run build``` 
### 2、将config/index.js/中的build对象的```assetsPublicPath`: '/'```改成``` assetsPublicPath: './'```
