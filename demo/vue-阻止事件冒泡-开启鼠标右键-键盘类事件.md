## 一、 阻止事件冒泡
### 布局如下：当点击按钮时，会触发button的click 也会触发父级的方法
```
<div id="box">
     <div @click="parentShow">
    　　  <button type="button" @click="show()">点 击</button>
     </div>
</div>
```

### 具体实现：

#### 第一种方法,传入一个event对象，然后对象里有cancelBubble 方法，设置为true
```
<div id="box">
     <div @click="parentShow">
          <button type="button" @click="show($event)">点 击</button>
     </div>
</div>
```

```
methods: {
     show: function(ev){
          alert(1);
          ev.cancelBubble = true;
     },
     parentShow: function(){
          alert(2);
     }
}
```

####  第二种方法是vue封装好的，直接在click的后面加上 ```.stop```，简单好记，建议使用
```
<div id="box">
     <div @click="parentShow">
           <button type="button" @click.stop="show()">按钮</button>
     </div>
</div>
```

## 二、阻止左键，开启右键行为
### 按钮的右键行为，vue事件。这里的prevent 是关闭默认行为，相当于    传个$event   然后 event.preventDefault();
```
<button type="button" @contextmenu.prevent="show1()">按钮</button>
```

## 三、键盘类事件
### keyup、keydown 是监听键盘按下，弹起事件，后面的.enter是指定键盘的按键，比如常见的：up、down、left、right、enter、tab 等
```
<input type="text" @keyup.enter="show2()" />
```

### 也可以通过$event的keyCode 来获取键盘的值。比如：
```
<input type="text" @keydown="show2($event)" />
```
```
show2: function(ev){
       console.log(ev.keyCode);
}
```


