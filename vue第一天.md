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
```addFormData.category``` 值和 ```categoryList``` 的每一项的 ```label``` 对应。
