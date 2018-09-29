# 背景
最近一个项目用到 vue 和 element ui开发前端。为了减少页面的加载速度，提高用户体验，对于一些图片决定使用图标代替，但是发现element-ui的图标少得可怜，
完全满足不了我的要求，于是决定在element-ui的项目里引入第三方的图标库。本文记录引入第三方图标（基于阿里巴巴矢量图标库）的一些具体步骤和注意事项。
首先进入阿里巴巴矢量图标库：http://www.iconfont.cn/

## 步骤
1、进入网站登录账户后，进入【图标管理】-【我的项目】-【添加项目】，新建一个项目，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/001.jpg) 
<br>
2、点击【新建项目】后，弹出项目名称等信息框图，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/002.jpg) 
<br>
3、完成后，点击确定，然后在跳转之后的页面上选择【Font class】
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/003.jpg) 
<br>
4、接着点击【图标库】-【官方图标库】，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/004.jpg) 
<br>
5、选择一个图标库，将图标库中希望加到项目中的图标添加进购物车，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/004-1.jpg) 
<br>
6、添加完成之后，点击购物车图标，进入购物车页面，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/006.jpg) 
<br>
7、然后，点击【添加至项目】按钮，选择自己的项目，确定后，选择的图标会进入到刚才创建的项目目录下，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/007.jpg) 
<br>
8、点击下载到本地 会下载一个download.zip 解压后 打开文件夹大致如下图：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/008.jpg) 
<br>
9、有一些demo 和 样例 不用导入项目，但是为了给其他人一个提示也最好直接把所有文件拷贝到自己的vue项目中的：src/assets 下 新建一个 icon文件夹。效果如图<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/009.jpg) 
<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/010.jpg) 
<br>
10、然后打开iconfont.css，添加代码如下：<br>
```
[class^="el-icon-vpn"], [class*=" el-icon-vpn"] {
  font-family: "fontFamily" !important;
  // 以下内容参照第三方图标库本身的规则
  font-size: 18px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

注意：其中2个class 处 和 font-family 的设置是来自在 阿里矢量库项目设置的参数 请填写一致（注意：第二个class处前面有个空格）<br>
修改完该文件 效果如下图：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/012.jpg) 
<br>
11、然后在项目中要使用图标的页面 引入上面修改的css，如下图所示：<br>
![](https://github.com/clearloverP/vue/blob/master/demo/images/icon/011.jpg) 
<br>
12、在项目中使用图标有两种方式,如:我的图标全称为el-icon-shop-home，<br>
1> icon属性<br>
```
<el-button size="small" icon="ump-addition" type="primary">首页</el-button>
```
2> class属性<br>
```
<el-button size="small" class="el-icon-shop-addition" type="primary">首页</el-button>
```
效果如下图所示：<br>

<br>
至此：在element-ui + vue项目中引入第三方图标库的一般步骤就完整了。






