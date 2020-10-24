## Canvas

    1.  getContext("2d")  画布需要一个context定义 2d
    2.  beginPath()   开始一个路径
    3.  moveTo(x, y)  路径移动到画布的指定点(起点)
    4.  lineTo(x, y)  添加一个新点 画线
    5.  closePath()   关闭绘制路径
    6.  fillStyle     设置填充颜色
    7.  fill()        填充已定义好的路径(调用方法)
    8.  lineWidth     画线 宽度
    9.  strokeStyle   设置描边颜色
    10. stroke()      绘制定义好的路径(调用方法)
    11. lineJoin      设定边角样式    round 圆角   bevel 斜角     miter 直角

## save

    save() 是canvas 2D API 通过将当前状态放入栈中 保存canvas全部状态的方法
        保存的状态有:
            - strokeStyle   fillStyle   lineWidth   lineCap     lineJoin等

## restore

    restroe() 是canvas 2D API 通过绘图状态栈中弹出顶端的状态    将canvas 恢复到最近保存的状态   不保存 不做改变

## 绘制矩形

    1. rect(X,Y,W,H)
    2. fillRect(X,Y,W,H)  默认填充黑色  如需自己定义样式 需要在上面定义 否则没有效果
    3. strokeRect(X,Y,W,H)  绘制边框 默认边框黑色  如需自己定义样式 需要在上面定义 否则没有效果
        - lineWidth     边框宽度
        - lineJoin      边框样式    round 圆角   bevel 斜角
    4. clearRect(x,y,w,h)  绘制一个与画板颜色相同的矩形

## lineCap

    lineCap     绘制线段末端的属性
        - butt      方形
        - round     圆形
        - square    方形  加长

## 绘制圆形

    arc(X, Y, r, 开始角度, 结束角度, false/true)
    角度的写法：360度 2*Math.PI , 270度 1.5*Math.PI , 180度 1*Math.PI , 90度 0.5*Math.PI ,
    false 顺时针   true逆时针

## 贝塞尔曲线

    moveTo(x, y) 首先需要一个开始点
    二次贝塞尔曲线: 需要一个控制点 一个结束点   quadraticCurveTo(控制点X, 控制点Y, 结束点X, 结束点Y);
    三次贝塞尔曲线: 需要两个控制点 一个结束点   bezierCurveTo(控制点X, 控制点Y, 控制点X, 控制点Y, 结束点X, 结束点Y);

## 变换

    translate(x,y)  移动canvas画布的原点
    rotate(deg)     顺时针以画布的原点旋转
    scale(x,y)      缩放canvas 画布中 图像大小

## 绘制文字

    1. 填充
        - fillStyle 填充颜色
        - fillText(字体, X, Y, max-width);  max-width指字体最大宽度
    2. 描边
        - strokeStyle 设置描边颜色
        - strokeText(字体, X, Y, max-width);  max-width指字体最大宽度
    font 文本样式  大小, 字体样式(sans-serif默认)
    textAlign 设置文字水平对齐方式 left right center
    textBaseline  设置文字垂直对齐方式  top middel botttom

## 渐变

    线性渐变:
        createLinearGradient(x1, y1, x2, y2)   接受 4 个参分别表示渐变的起点 (x1,y1) 与终点 (x2,y2)
    径向渐变:
        createRadialGradient(x1, y1, r1, x2, y2, r2,...)   接受 6 个参数，前三个定义一个以 (x1,y1) 为原点，半径为 r1 的圆，后三	个参数则定义另一个以 (x2,y2) 为原点，半径为 r2 的圆
    
        gradient.addColorStop(position, color)  方法接受 2 个参数，position 参数必须是一个 0.0 与 1.0 之间的数值，表示渐变中	颜色所在的相对位置

## 图片

    drawImage(img,x,y,w,h)  图片路径 起始坐标  图片大小

## 设置背景

    createPattern(img,repetition)   图片    平铺方式 repear no-repeat repeat-x reprat-y
    一般讲createPuttern()返回的对象作为fillStyle的值

## 渐变

    1. 线性渐变
        createLinearGradient(x1,y1,x2,y2)  起始点  终止点
        addColorStop(position,color)        位置 颜色

## 像素

    1. 得到画布像素数据
        - getImageData(x,y,w,h)     x,y 起始坐标      w,h 大小
    
    2.ImageData对象
        - ImageData对象中储存着canvas对象真是的像素数据 包含几个只读属性:
            - width     图片的宽度  像素单位
            - height    图片的高度
            - data      是一个数组 包含每一个像素rgba的信息
    
    3. 写入像素数据
        - putImageData(imageData,x,y)
    
    4. 创建ImageData对象
        createImageData(w,h)    x: 新 ImageData 对象的宽度      y: 新 ImageData 对象的高度

## 全局透明度

    globalAlpha 影响画布中所有内容的透明度  0-1

## 合成

        globalCompositeOperation     控制图形组合方式
            source-over  默认值  新图覆盖在旧图上
            source-atop  只绘制旧图和重叠部分 其他透明
            source-in    只绘制新图的重叠部分  其他透明
            source-out   只绘制新图 重叠部分和旧图透明
            destination-over     默认值旧图覆盖在新图上
            destination-atop     只绘制新图和重叠部分 其他透明
            destination-in       只绘制旧图和重叠部分  其他透明
            destination-out      只绘制旧图 重叠部分和新图透明
            lighter  旧图与新图都绘制 重叠部分混色处理
            xor  旧图与新图重叠处透明
            copy   只绘制新图形 不会只旧图形

## 将画布导出为图像

    toDataURL()

## 事件操作

    isPointInPath(x,y)  判断当前路径是否包含监测点    (给最新的canvas图像添加事件)
