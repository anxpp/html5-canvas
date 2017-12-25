# Canvas简明教程

    <canvas> 是 HTML5 新增的元素，可用于通过使用 JavaScript 中的脚本来绘制图形。例如，它可以用于绘制图形，制作照片，创建动画，甚至可以进行实时视频处理或渲染。

    本例包含个人主页全部源码。

## 浏览器兼容：

| 元素    | chrome | IE   | firefox | Safari |
| :----:  | :-----:| :---:| :----:  | :----: |
| Canvas  | 4.0+   | 9.0+ | 2.0+    | 3.1+   |

## Canvas 能干什么

- 图表
- 小游戏
- 活动页
- 特效
- 背景等

## 获取 Canvas 对象

方法：
- canvas.getContext(contextType, contextAttributes);

通常我们在创建好一个 Canvas 标签的时候，我们要做的第一步就是要先获取到这个 Canvas 的上下文昌对象。

上下文类型（contextType）：
- 2d（本小册所有的示例都是 2d 的）：代表一个二维渲染上下文
- webgl（或"experimental-webgl"）：代表一个三维渲染上下文
- webgl2（或"experimental-webgl2"）：代表一个三维渲染上下文；这种情况下只能在浏览器实现 WebGL 版本2 (OpenGL ES 3.0)。

## 绘制路径

    请结合源码查看效果

### 方法列表

    熟悉有些什么方法，能做什么即可

| 方法    | 描述 | 
| :----  | :-----|
| fill()| 	填充路径 | 
| stroke()| 	描边 | 
| arc()	| 创建圆弧 | 
| rect()	| 创建矩形 | 
| fillRect()	| 绘制矩形路径区域 | 
| strokeRect()	| 绘制矩形路径描边 | 
| clearRect()	| 在给定的矩形内清除指定的像素 | 
| arcTo()| 	创建两切线之间的弧/曲线 | 
| beginPath()	| 起始一条路径，或重置当前路径 | 
| moveTo()| 	把路径移动到画布中的指定点，不创建线条 | 
| lineTo()	| 添加一个新点，然后在画布中创建从该点到最后指定点的线条 | 
| closePath()	| 创建从当前点回到起始点的路径 | 
| clip()| 	从原始画布剪切任意形状和尺寸的区域 | 
| quadraticCurveTo()	| 创建二次方贝塞尔曲线 | 
| bezierCurveTo()| 	创建三次方贝塞尔曲线 | 
| isPointInPath()| 	如果指定的点位于当前路径中，则返回 true，否则返回 false | 

### 方法介绍

    该部分可以跳过，当参考手册即可。

**arc() 方法：创建弧/曲线（用于创建圆或部分圆）**

`context.arc(x,y,r,sAngle,eAngle,counterclockwise);`

- x:圆的中心的 x 坐标。
- y:圆的中心的 y 坐标。
- r:圆的半径
- sAngle:起始角，以弧度计。（弧的圆形的三点钟位置是 0 度）。
- eAngle:结束角，以弧度计。
- counterclockwise:可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。

**moveTo(x,y)：把路径移动到画布中的指定点，不创建线条**

**lineTo(x,y)：添加一个新点，然后在画布中创建从该点到最后指定点的线条**

样式：
- lineCap | 设置或返回线条的结束端点样式
- lineJoin | 设置或返回两条线相交时，所创建的拐角类型
- lineWidth | 设置或返回当前的线条宽度
- miterLimit | 设置或返回最大斜接长度

**fillRect(x,y,width,heighr)：绘制一个实心矩形**

**strokeRect(x,y,width,height)：绘制一个空心矩形**

### 画一个点

```
    var canvas4 = document.getElementById("canvas4");
    var context4 = canvas4.getContext("2d");
    canvas4.width = 400;
    canvas4.height = 400;
    context4.beginPath();
    context4.arc(100, 100, 1, 0, Math.PI * 2, true);
    context4.closePath();
    context4.fillStyle = 'rgb(255,255,255)';
    context4.fill();
```

### 绘制弧/曲线

```
    var canvas5 = document.getElementById("canvas5");
    var context5 = canvas5.getContext("2d");
    canvas5.width = 400;
    canvas5.height = 400;
    context5.beginPath();
    context5.arc(100, 100, 50, 0, Math.PI * 0.5, false);
    context5.strokeStyle = "white";
    context5.stroke();
```

### 绘制线条

- 直线：

```aidl
    var canvas6 = document.getElementById("canvas6");
    var context6 = canvas6.getContext("2d");
    canvas6.width = 400;
    canvas6.height = 400;
    context6.beginPath();
    context6.moveTo(50,50);
    context6.lineTo(100,100);
    context6.strokeStyle = '#fff';
    context6.stroke();
```

- 折线：

```aidl
    var canvas7 = document.getElementById("canvas7");
    var context7 = canvas7.getContext("2d");
    canvas7.width = 400;
    canvas7.height = 400;
    context7.beginPath();
    context7.lineTo(200, 200);
    context7.lineTo(200, 100);
    context7.lineTo(100, 50);
    context7.strokeStyle = '#fff';
    context7.stroke();
```
- 添加样式

```aidl
    var canvas8 = document.getElementById("canvas8");
    var context8 = canvas8.getContext("2d");
    canvas8.width = 400;
    canvas8.height = 400;
    context8.beginPath();
    context8.moveTo(10,10);
    context8.lineTo(100,100);
    context8.lineWidth = 10;
    context8.lineCap = 'round';
    context8.strokeStyle = '#fff';
    context8.stroke()
```

### 绘制矩形

```aidl
    var canvas9 = document.getElementById("canvas9");
    var context9 = canvas9.getContext("2d");
    canvas9.width = 400;
    canvas9.height = 400;
    context9.beginPath();
    context9.fillStyle = '#fff';
    context9.fillRect(10, 10, 100, 100);
    context9.strokeStyle = '#fff';
    context9.strokeRect(130, 10, 100, 100);
```

## 颜色、样式和阴影

- fillStyle | 设置或返回用于填充绘画的颜色、渐变或模式
- strokeStyle | 设置或返回用于笔触的颜色、渐变或模式
- shadowColor | 设置或返回用于阴影的颜色
- shadowBlur | 设置或返回用于阴影的模糊级别
- shadowOffsetX | 设置或返回阴影距形状的水平距离
- shadowOffsetY | 设置或返回阴影距形状的垂直距离

### 阴影

```aidl
    var canvas10 = document.getElementById("canvas10");
    var context10 = canvas10.getContext("2d");
    canvas10.width = 400;
    canvas10.height = 400;
    context10.beginPath();
    context10.arc(100,100,50,0,2*Math.PI,false);
    context10.fillStyle = '#fff';
    context10.shadowBlur = 20;
    context10.shadowColor = '#fff';
    context10.fill()
```

### 渐变

- createLinearGradient()	创建线性渐变（用在画布内容上）
- createPattern()	在指定的方向上重复指定的元素
- createRadialGradient()	创建放射状/环形的渐变（用在画布内容上）
- addColorStop()	规定渐变对象中的颜色和停止位置

**context.createLinearGradient(x0,y0,x1,y1)：**

- x0：开始渐变的 x 坐标
- y0：开始渐变的 y 坐标
- x1：结束渐变的 x 坐标
- y1：结束渐变的 y 坐标

**gradient.addColorStop(stop,color)：**

- stop：介于 0.0 与 1.0 之间的值，表示渐变中开始与结束之间的位置。
- color：在结束位置显示的 CSS 颜色值

粉色到白色的由上向下的渐变：

```aidl
    var canvas11 = document.getElementById("canvas11");
    var context11 = canvas11.getContext("2d");
    canvas11.width = 400;
    canvas11.height = 400;
    var grd11 = context11.createLinearGradient(100,100,100,200);
    grd11.addColorStop(0,'pink');
    grd11.addColorStop(1,'white');
    context11.fillStyle = grd11;
    context11.fillRect(100,100,200,200);
```

彩虹渐变：

```aidl
    var canvas12 = document.getElementById("canvas12");
    var context12 = canvas12.getContext("2d");
    canvas12.width = 400;
    canvas12.height = 400;
    var grd12 = context12.createLinearGradient(0,0,0,400);
    grd12.addColorStop(0,'rgb(255, 0, 0)');
    grd12.addColorStop(0.2,'rgb(255, 165, 0)');
    grd12.addColorStop(0.3,'rgb(255, 255, 0)');
    grd12.addColorStop(0.5,'rgb(0, 255, 0)');
    grd12.addColorStop(0.7,'rgb(0, 127, 255)');
    grd12.addColorStop(0.9,'rgb(0, 0, 255)');
    grd12.addColorStop(1,'rgb(139, 0, 255)');
    context12.fillStyle = grd12;
    context12.fillRect(0,0,400,400);
```

## 图形转换

- scale()	缩放当前绘图至更大或更小
- rotate()	旋转当前绘图
- translate()	重新映射画布上的 (0,0) 位置
- transform()	替换绘图的当前转换矩阵
- setTransform()	将当前转换重置为单位矩阵。然后运行 transform()

### 缩放

```aidl
    var canvas13 = document.getElementById("canvas13");
    var context13 = canvas13.getContext("2d");
    canvas13.width = 400;
    canvas13.height = 400;
    context13.strokeStyle = 'white';
    context13.strokeRect(5, 5, 50, 25);
    context13.scale(2, 2);
    context13.strokeRect(5, 5, 50, 25);
    context13.scale(2, 2);
    context13.strokeRect(5, 5, 50, 25);
```

设置 scale() 方法之后在设置的矩形，无论是线条的宽度还是坐标的位置，都被放大了。
并且 scale() 的效果是可以叠加的，也就是说，我们在上面的例子中使用了两次 scale(2,2)。
那么，最后一个矩形相对于第一个矩形长和宽，以及坐标的位置就放大了 4 倍。

### 旋转

**context.rotate(angle)**

angle : 旋转角度，以弧度计。
如需将角度转换为弧度，请使用 degrees*Math.PI/180 公式进行计算。
举例：如需旋转 5 度，可规定下面的公式：5*Math.PI/180。

```aidl
    var canvas14 = document.getElementById("canvas14");
    var context14 = canvas14.getContext("2d");
    canvas14.width = 400;
    canvas14.height = 400;
    context14.fillStyle = 'white';
    context14.rotate(20*Math.PI/180);
    context14.fillRect(70,30,200,100);
```

在进行图形变换的时候，需要画布旋转，然后再绘制图形。

这样的结果是使用的图形变换的方法都是作用在画布上的，既然对画布进行了变换，那么在接下来绘制的图形都会变换。

比如对画布使用了 rotate(20*Math.PI/180) 方法，就是将画布旋转了 20°，然后之后绘制的图形都会旋转 20°。

## 图像绘制

**context.drawImage(img,sx,sy,swidth,sheight,x,y,width,height)**

- img:规定要使用的图像、画布或视频。
- sx:可选。开始剪切的 x 坐标位置。
- sy:可选。开始剪切的 y 坐标位置。
- swidth:可选。被剪切图像的宽度。
- sheight:可选。被剪切图像的高度。
- x:在画布上放置图像的 x 坐标位置。
- y:在画布上放置图像的 y 坐标位置。
- width:可选。要使用的图像的宽度。（伸展或缩小图像）
- height:可选。要使用的图像的高度。（伸展或缩小图像）

```aidl
    document.getElementById("tulip").onload = function () {
        var canvas15 = document.getElementById("canvas15");
        var context15 = canvas15.getContext("2d");
        context15.width = 400;
        context15.height = 400;
        var img = document.getElementById("tulip");
        context15.drawImage(img, 90, 130, 90, 80, 20, 20, 90, 80);
    }
```

## 随机粒子

- 创建粒子类

```aidl
function Round_item(index,x,y) {
        this.index = index;
        this.x = x;
        this.y = y;
        this.r = Math.random() * 2 + 1;
        var alpha = (Math.floor(Math.random() * 10) + 1) / 10 / 2;
        this.color = "rgba(255,255,255," + alpha + ")";
    }
```

- 定义粒子

```aidl
Round_item.prototype.draw = function () {
        content.fillStyle = this.color;
        content.shadowBlur = this.r * 2;
        content.beginPath();
        content.arc(this.x, this.y, this.r, 0, 2 * Math.PI, false);
        content.closePath();
        content.fill();
    };
```

- 初始化粒子

```aidl
function init() {
        for(var i = 0; i < initRoundPopulation; i++ ){
            round[i] = new Round_item(i,Math.random() * WIDTH,Math.random() * HEIGHT);
            round[i].draw();
        }
    }
```

- **完整代码**

```aidl
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>随机粒子</title>
    <style>
        html, body {
            margin: 0;
            overflow: hidden;
            width: 100%;
            height: 100%;
            /*cursor: none;*/
            background: black;
        }
    </style>
</head>
<body>
<canvas id="canvas"></canvas>
<script>
    var ctx = document.getElementById('canvas'),
        content = ctx.getContext('2d'),
        round = [],
        WIDTH,
        HEIGHT,
        initRoundPopulation = 80;
    WIDTH = document.documentElement.clientWidth;
    HEIGHT = document.documentElement.clientHeight;

    ctx.width = WIDTH;
    ctx.height = HEIGHT;

    function Round_item(index, x, y) {
        this.index = index;
        this.x = x;
        this.y = y;
        this.r = Math.random() * 2 + 1;
        var alpha = (Math.floor(Math.random() * 10) + 1) / 10 / 2;
        this.color = "rgba(255,255,255," + alpha + ")";
    }

    Round_item.prototype.draw = function () {
        content.fillStyle = this.color;
        content.shadowBlur = this.r * 2;
        content.beginPath();
        content.arc(this.x, this.y, this.r, 0, 2 * Math.PI, false);
        content.closePath();
        content.fill();
    };

    function init() {
        for (var i = 0; i < initRoundPopulation; i++) {
            round[i] = new Round_item(i, Math.random() * WIDTH, Math.random() * HEIGHT);
            round[i].draw();
        }
    }

    init();
</script>
</body>
</html>
```

### 动起来

- 定义粒子的运动

```aidl
    Round_item.prototype.move = function () {
        this.y -= 0.15;
        if (this.y <= -10)
            this.y = HEIGHT + 10;
        this.draw();
    };
```

- 添加定时器

```aidl
    function animate() {
        content.clearRect(0, 0, WIDTH, HEIGHT);
        for (var i in round)
            round[i].move();
        requestAnimationFrame(animate)
    }
```

- 完整代码

```aidl
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        html, body {
            margin: 0;
            overflow: hidden;
            width: 100%;
            height: 100%;
            /*cursor: none;*/
            background: black;
        }
    </style>
</head>
<body>
<canvas id="canvas"></canvas>
<script>
    var ctx = document.getElementById('canvas'),
        content = ctx.getContext('2d'),
        round = [],
        WIDTH,
        HEIGHT,
        initRoundPopulation = 200;

    WIDTH = document.documentElement.clientWidth;
    HEIGHT = document.documentElement.clientHeight;

    ctx.width = WIDTH;
    ctx.height = HEIGHT;

    function Round_item(index, x, y) {
        this.index = index;
        this.x = x;
        this.y = y;
        this.r = Math.random() * 2 + 1;
        var alpha = (Math.floor(Math.random() * 10) + 1) / 10 / 2;
        this.color = "rgba(255,255,255," + alpha + ")";
    }

    Round_item.prototype.draw = function () {
        content.fillStyle = this.color;
        content.shadowBlur = this.r * 2;
        content.beginPath();
        content.arc(this.x, this.y, this.r, 0, 2 * Math.PI, false);
        content.closePath();
        content.fill();
    };

    function animate() {
        content.clearRect(0, 0, WIDTH, HEIGHT);
        for (var i in round)
            round[i].move();
        requestAnimationFrame(animate)
    }

    Round_item.prototype.move = function () {
        this.y -= 0.15;
        if (this.y <= -10)
            this.y = HEIGHT + 10;
        this.draw();
    };

    function init() {
        for (var i = 0; i < initRoundPopulation; i++) {
            round[i] = new Round_item(i, Math.random() * WIDTH, Math.random() * HEIGHT);
            round[i].draw();
        }
        animate();
    }

    init();
</script>
</body>
</html>
```

## 鼠标

主要是监听鼠标移动事件：

```javascript 1.8
window.onmousemove = function (event) {/*...*/}
```

其他都差不多了，一分完整的示例代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>鼠标互动</title>
    <style>
        html, body {
            margin: 0;
            overflow: hidden;
            width: 100%;
            height: 100%;
            /*cursor: none;*/
            background: black;
        }
    </style>
</head>
<body>
<canvas id="canvas"></canvas>
<script>
    var canvas = document.getElementById('canvas'),
        ctx = canvas.getContext('2d'),
        WIDTH = canvas.width = document.documentElement.clientWidth,
        HEIGHT = canvas.height = document.documentElement.clientHeight,
        para = {
            num: 100,
            color: false,    //  颜色  如果是false 则是随机渐变颜色
            r: 0.9,
            o: 0.09,         //  判断圆消失的条件，数值越大，消失的越快
            a: 1
        },
        color,
        color2,
        round_arr = [];
    window.onmousemove = function (event) {
        mouseX = event.clientX;
        mouseY = event.clientY;
        round_arr.push({
            mouseX: mouseX,
            mouseY: mouseY,
            r: para.r,
            o: 1
        })
    };
    // 判断参数中是否设置了 color，如果设置了 color，就使用该值、
    // 如果参数中的 color 为 false，那么就使用随机的颜色
    if (para.color) color2 = para.color;
    else color = Math.random() * 360;

    function animate() {
        if (!para.color) {
            color += .1;
            color2 = 'hsl(' + color + ',100%,80%)';
        }
        ctx.clearRect(0, 0, WIDTH, HEIGHT);
        for (var i = 0; i < round_arr.length; i++) {
            ctx.fillStyle = color2;
            ctx.beginPath();
            ctx.arc(round_arr[i].mouseX, round_arr[i].mouseY, round_arr[i].r, 0, Math.PI * 2);
            ctx.closePath();
            ctx.fill();
            round_arr[i].r += para.r;
            round_arr[i].o -= para.o;
            if (round_arr[i].o <= 0) {
                round_arr.splice(i, 1);
                i--;
            }
        }
        window.requestAnimationFrame(animate);
    }
    animate();
</script>
</body>
</html>
```

**home 目录即为 http://anxpp.com 主页全部源码**

**写得很乱，有待整理~~~**