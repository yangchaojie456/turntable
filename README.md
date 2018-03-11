## 声明
> 本插件可以帮助你，快速创建一个 活动抽奖转盘，并提供旋转转盘的方法。
> 插件基于jquery，使用canvas创建转盘。
## 兼容性
> 适用于所有主流浏览器及移动端的浏览器。**IE8及以下不支持**
## demo
>> http://www.yangchaojie.top/plugin/turntable
## 用法
```html
    <body>
        <canvas id="myCanvas" width="600" height="600"></canvas>
    </body>

    <script src="http://code.jquery.com/jquery-1.12.4.js"></script>
    <script src="./turntable.js"></script>
    <script>
        // 定义转盘奖品
        var wheelSurf = $('#myCanvas').WheelSurf({
            list: list, // 奖品 列表，(必填)
            outerCircle: {
                color: '#df1e15' // 外圈颜色(可选)
            },
            innerCircle: {
                color: '#f4ad26' // 里圈颜色(可选)
            },
            dots: ['#fbf0a9', '#fbb936'], // 装饰点颜色(可选)
            disk: ['#ffb933', '#ffe8b5', '#ffb933', '#ffd57c', '#ffb933', '#ffe8b5', '#ffd57c'], //中心奖盘的颜色，默认7彩(可选)
            title: {
                color: '#5c1e08',
                font: '19px Arial'
            } // 奖品标题样式(可选)
        })

        // 初始化转盘
        wheelSurf.init()

        // 转动转盘，
        wheelSurf.lottery(旋转角度, function () {
            console.log("旋转结束的回调函数")
        })
    </script>
```
## API

|方法|对象|参数|返回值|
|:-:|:-:|:-|:-:|
|WheelSurf()|canvas的JQuery对象|  @param {Object} options<br>@param {Array}  options.list  存储奖品的的列表，example [{1:{name:'谢谢参与',image:'1.jpg'}}]<br>@param {Object} options.outerCircle {color:'#df1e15'} 外圈颜色，默认红色<br>@param {Object} options.innerCircle {color:'#f4ad26'} 里圈颜色，默认黄色<br>@param {Array}  options.dots ['#fbf0a9', '#fbb936'] 装饰点颜色 ，默认深黄浅黄交替<br>@param {Array}  options.disk ['#ffb933', '#ffe8b5', '#ffb933', '#ffd57c', '#ffb933', '#ffe8b5', '#ffd57c'] 中心奖盘的颜色，默认7彩<br>@param {Object} options.title {color:'#5c1e08',font:'19px Arial'} 奖品标题颜色| WheelSurf对象 |
|init()|WheelSurf对象|null|null|
|lottery()|WheelSurf对象|@param {number} 角度<br> @param {function} callback 旋转完成后的回调|null|


## 注意

> **因为无法得知获取奖品接口的格式及抽中奖品返回的格式，**

> 1. 本插件只提供初始化转盘和旋转转盘的接口。
> 2. 需要按照demo 格式化成指定参数格式，才能正确初始化转盘
> 3. 需要手写一点逻辑计算旋转角度 （顺时针数第几个奖品*360/奖品数量+（360/奖品数量）/2）

