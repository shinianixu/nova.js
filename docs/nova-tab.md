# &lt;nova-tab&gt;

Tab组件。使用硬件加速实现切换，动画流畅且tab之间无缝，支持循环，自动轮播，切换事件监听，回弹效果等。

## Demo

<style type="text/css">
    nova-tab {
        background: #FBFBFB;
        display: block;
        height: 300px;
    }
    nova-tab[unresolved] {
        opacity: 0;
    }
    nova-tab .controls {
        cursor: pointer;
    }
    nova-tab img {
        width: 120px;
        height: 120px;
        border-radius: 60px;
        position: relative;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    nova-tab .contents>* {
        text-align: center;
        font-size: 32px;
        font-weight: bold;
        line-height: 200px;
    }
</style>

<script>
    _loader.add('customEle', '{{urls.tab}}');
    _loader.use('customEle', function() { });
</script>

<div>
<nova-tab default-style unresolved>
    <span class="tab">Tab1</span>
    <span class="tab">Tab2</span>
    <span class="tab">Tab3</span>
    <div>Hello</div>
    <div>Welcome</div>
    <div>Sweetie</div>
</nova-tab>
</div>

## 使用方法

### HTML

| 选择器          |  作用  |
|-------------------|---------|
| .tab  | 触发切换的标签 |

```markup
<nova-tab default-style>
    <span class="tab">Tab1</span>
    <span class="tab">Tab2</span>
    <span class="tab">Tab3</span>
    <div>Hello</div>
    <div>Welcome</div>
    <div>Sweetie</div>
</nova-tab>
```

### Javascript
需先引入依赖的文件：Zepto基础库，Zepto touch模块, Zepto fx模块
```markup
<script src="{{urls.nova_polyfills}}"></script>
<script src="{{urls.nova}}"></script>
<script src="{{urls.tab}}"></script>
```

## 配置

```markup
<nova-tab></nova-tab>
<!-- 可配置如下attributes
    default-style                       // 是否使用默认样式。默认false
    animate                             // 切换时是否使用动画过渡。默认true, 可通过animate="false"关闭动画。
    index="0"                           // 初始index
    loop                                // 是否可循环。默认false
    duration-ms="200"                   // 切换动画的时长
    autoplay                            // 是否自动轮播。默认false
    autoplay-interval-ms="10000"        // 自动轮播时间间隔
    swipable                            // 是否可滑动。默认true，可通过swipable="false"关闭。
    direction="horizontal"              // 滑动方向。horizontal:水平，vertical:垂直
    current-class-name="current"        // 当前元素的类名
-->
```

## 方法
```javascript
var tab = document.querySelector('nova-tab');
tab.next();                        // 切换到下一个内容
tab.prev();                        // 切换到上一个内容
tab.switch(n);                     // 切换到第n个内容
tab.autoplay = false;              // 关闭自动轮播
```

## 扩展
```javascript
// 1. 在切换前后执行代码
tab.on('beforeSwitch', function(ev, toIndex, fromIndex) {
    console.log('before Sliding from ' + fromIndex + ' to ' + toIndex);
});

tab.on('afterSwitch', function(ev, toIndex, fromIndex) {
    console.log('after Sliding from ' + fromIndex + ' to ' + toIndex);
});

// 2. 在上述方法前后执行代码
tab.before('prev', function() {
    // ....
});

tab.after('next', function() {
    // ...
});

```

## 日志

### 1.0.5
1. 使用Nova.1.0.0.js作为底层框架
2. 将配置recyclable名称改为loop

### 1.0.4
1. 修复新版webkit动画渲染问题
2. 支持两个滑动项循环滑动
3. 新增current类，当前切换到的滑动项上会有此类
4. 将配置recursive名称改为recyclable
5. 支持多个&lt;nova-tab&gt;嵌套

### 1.0.3
1. 支持垂直滑动
2. 修复2.3滑动失效问题，bug原因是使用关键字switch作为方法ogz..

### 1.0.2
1. 当切换内容数小于或等于2个时，关闭循环轮播
2. 当切换内容数为1时，关闭滑动
3. 新增refresh方法，当显示，或尺寸更改时调用

### 1.0.1
升级依赖widget.js版本为1.0.2

### 1.0.0
首次发布

