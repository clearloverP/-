# vue 回顾与总结（第一天）

## vue.js+element-ui：el-select下拉列表设置默认值？
template中代码如下：
```
<el-select style="width: 130px" v-model="addFormData.category">
    <el-option v-for="category in categoryList" 
    	:key="category.value" 
	:label="category.label" 
	:value="category.label">
    </el-option>
</el-select>
```

script代码：
```
data() {
    return {
        addFormData: {
	    category: '选项一'
	},
        categoryList: [
	    {
		label: '选项一',
		value: 1
	    },
	    {
		label: '选项二',
		value: 2
	    },
	    {
		label: '选项三',
		value: 3
	    },
	    {
		label: '选项四',
	        value: 4
	    }
	]
    }
}
```
```addFormData.category``` 值和 ```categoryList``` 的每一项的 ```label``` 对应。也就是应该将```v-model```的值与```categoryList``` 的每一项的 ```label``` 对应


## vue项目打包及部署
基于Vue-Cli,通过npm run build来进行打包的操作

- 将打包出来的资源，基于Vue-Cli的一般是dist目录下有static目录和index.html文件，可以直接将这两个文件扔到服务端
- 但有时候，我们会直接将dist文件扔到服务端

可能出现的问题：
- 打包到服务器后，出现资源引用路径的问题
- 打包到服务器后，出现空白页的问题
- 打包到服务器后，出现引入的css的type被拦截转换为"text/plain"问题
- 打包到服务器后，出现路由刷新404的问题

解决：
1. router配置--指定路由起始(在开发模式中，Vue项目被放在了webpack配合nodeJs生成的本地服务器的根目录，但是在真实服务器中，项目肯定不会放在根目录，所以要指定router的base)
```
export default new Router({
	mode: 'history',
	base: '/app/',	// 将要部署的服务器文件夹下的路径,服务器www/html/app
	routes
	...
})
```
2. 编译打包配置: 进入config --> index.js
```
build: {
    env: require('./prod.env'),
    index: path.resolve(__dirname, '../dist/index.html'),
    assetsRoot: path.resolve(__dirname, '../dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: '/app/',  // 同router base属性设置
    productionSourceMap: false,  
    devtool: '#source-map',
    productionGzip: false,
    productionGzipExtensions: ['js', 'css'],
    bundleAnalyzerReport: process.env.npm_config_report
  }
```
3. 在dist文件夹中添加一个```.htaccess```文件，文件内容如下：
```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /app/
    RewriteRule ^index.html$ - [L]
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /app/index.html [L]
</IfModule>
```

4. 使用npm run build进行打包，至此前端能做的配置已经做完


路由跳转出现404，主要原因是后端对这个虚拟的前端路由没有做任何处理，服务器在找不到指定路径下的资源时，只能向客户端返回404。
解决办法（Apache）：进行url重写 --- 将Vue项目所在服务器文件夹下的路径，例如：
```
命令如下：vi /etc/httpd/conf/httpd.conf

添加如下内容：
<Directory "/var/www/html/app">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```
保存上述内容，然后重启Apache，即可





