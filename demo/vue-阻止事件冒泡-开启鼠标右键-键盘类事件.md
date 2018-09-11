## 一、 阻止事件冒泡
### 布局：当点击按钮时，会触发button的click 也会触发父级的方法
```
<div id="box">
     <div @click="parentShow">
    　　  <button type="button" @click="show()">按钮</button>
     </div>
</div>
```
