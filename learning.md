# learning......

## 移动端rem兼容插件amfe-flexible

### 安装

```undefined
npm install amfe-flexible -S
npm install postcss-px2rem -S
```

### 源码理解

#### 设置根元素的font-size 为整个布局提供baseSize

```
1、为body元素设置基础的baseSize，大小为12px乘以dpr，dpr：屏幕物理像素与CSS像素比例  window.devicePixelRatio获取
2、计算rem 使用屏幕的宽度除以想要的比例  一amfe-flexible为例 此插件是缩小10   width/10 rem
3、监听事件用于重置rem的值 用于各个设备的匹配  pageShow(此事件用于监听是否是从浏览器历史打开的此网页，以防用户在缓存中拿到数据导致rem的值不会重置) 
resize(监听屏幕的变化用于重置rem的基础值) 
4、该插件检测了各个适配器中是否支持0.5像素的边框
```

### postcss-px2rem

```
此插件是利用amfe-flexible插件计算出来的baseSize，把我们设置在css中的px转换为rem的适配
计算公式比较简单 根元素的px知道了 使用px除以根元素的px就可以得出rem的值
```

### 简单的实现rem适配

html三个盒子分别给予三种不同的属性

```
<body>
  <h1>123</h1>
  <div class="div1">

  </div>
  <div class="div2">

  </div>
  <div class="div3">

  </div>
</body>
<style type="text/css">
  body {
    font-size: .5rem;
  }
  .div1 {
    width: 1rem;
    height: 1rem;
    background-color: aquamarine;
  }

  .div2 {
    width: 160px;
    height: 160px;
    background-color: red;
  }

  .div3 {
    width: 10vh;
    height: 10vh;
    background-color: aquamarine;
  }
</style>
```

script

```
<script>
  // 设置基础的比例值，也就是根元素的fontSiz基于界面宽度的比例
  const base = 10 
  let div2 = document.getElementsByClassName('div2')[0]
  window.onload = function () {
  	// 页面加载成功后初始化rem的值 此步可以封装成一个函数用于后续的重置
    let bodyWidth = document.body.clientWidth
    let dpr = window.devicePixelRatio
    document.documentElement.style.fontSize = (bodyWidth / base * dpr) + 'px'
  }
  window.onresize = function (e) {
  	// 重置rem
    let bodyWidth = document.body.clientWidth
    let dpr = window.devicePixelRatio
    document.documentElement.style.fontSize = (bodyWidth/ base * dpr) + 'px'
  }
  window.onclick = function() {
  	// 使用一个点击来改变第二个盒子的值 用于观看当屏幕变化后各个比值变化 
    div2.style.width = div2.clientWidth/parseInt(document.documentElement.style.fontSize) + 'rem'
    div2.style.height = div2.clientHeight/parseInt(document.documentElement.style.fontSize) + 'rem'
    console.log(div2.clientWidth,div2.clientHeight)
  }
</script>
```

### 使用vh作为基础单位单位配合rem

```
basePx的计算方式和元素rem的计算方式 如html的 fontSize = 10vh
basePx =  document.documentElement.clientWidth * 0.1
像素转换rem的计算： realBoxwidth.style.width = realBoxwidth.clientWidth / basePx + 'rem'
```



## 一键复制插件clipboard

```undefined
npm install --save clipboard
```

> html
>
> ```
> <div>
> 	copy_text应该是对应的data-clipboard-target中标签 用于映射你想要获取的哪一个元素的内容
> 	<span id="copy_text">{{想要拷贝的内容，标签不受限制}}</span>
> 	<p class="sharecodebtn cobyOrderSn"
>         @click="copy"
>         data-clipboard-target="#copy_text">
>         复制分享
>     </p>
> </div>
> 
> methods: {
>     copy() {
>         let _this = this
>         let clipboard = new this.clipboard('.cobyOrderSn') // 实例化对象 填写出发的元素 cliphoard需要在main文件中引入
>         clipboard.on('success', function (e) {
>         	_this.$uPop.msg('已复制')
>         	clipboard.destroy()
>         })
>         clipboard.on('error', function (err) {
>         	clipboard.destroy()
>         })
>     }
> }
> ```
>
> 

## 二维码生成插件：qwcodejs2

引入

```
import QRCode from 'qrcodejs2'
```

使用

```
let qrcode = new QRCode("test", {
    text: "http://jindo.dev.naver.com/collie", // 内容
    width: 128, // 宽度
    height: 128,// 高度
    colorDark : "#000000",
    colorLight : "#ffffff",
    correctLevel : QRCode.CorrectLevel.H
});
qrcode.clear(); // 删除二维码
qrcode.makeCode("http://naver.com"); // 创建另一个二维码
```

## 

# uu跑腿接口查看

进入页面应调用了一下接口，并大概梳理了其中的数据展示

>进入页面调用的接口，t为token令牌
>
>```
>https://m.uupt.com/fewebapi/BaseService/GetQuickOperations?t=1604125860439  
>获取到的是支付页面内的配送物品选择列表：蛋糕、鲜花、钥匙等
>https://m.uupt.com/fewebapi/UserSearch/GetGoingOrderCount?t=1604125988884
>返回的是goingcount，应该是配送或者正在配送的数目
>https://m.uupt.com/fewebapi/BaseService/GetCityList?ctype=1&token=e6f043be23c641df9ec51c3affa6196d
>第一次进入页面时如果没有定位出城市的化需要手动选择城市，此接口返回城市数据的渲染列表
>https://m.uupt.com/fewebapi/BaseService/GetCommonConfig
>不需要参数返回的是城市json数据字符串且为转成对象格式，暂时不知作用
>https://m.uupt.com/fewebapi/Activitys/GetActivityInfo?t=1604125989276
>此参数应该是要获取用户在此页面的活动信息，
>```
>
>选择完城市调用的接口
>
>```
>https://m.uupt.com/fewebapi/UserSearch/GetGoingOrderCount?t=1604125988884
>在此页面同样调用了此方式
>```
>
>进入帮我送
>
>```
>https://m.uupt.com/fewebapi/UserSearch/BeforeAddOrder?t=1604126746269
>返回了几组数据，关于蛋糕的计价标准，优惠政策，重量大小的计价标准等，
>```
>
>选择过配送物品后会调用此方法
>
>```
>https://m.uupt.com/fewebapi/UserSearch/GetOrderPriceSimple?t=1604127064277
>应该是前端把数据返回到后台，然后后台经过计算把计算结果返回，也就是说在每一次切换且影响到价格后都会重复调用此接口。
>```
>
>点击保价
>
>```
>https://m.uupt.com/fewebapi/UserSearch/GetInsuranceConfig?t=1604127579109
>调用此接口用于展示保价界面的信息
>```
>
>因为使用保价后会改变提交金额所以还是会调用
>
>```
>https://m.uupt.com/fewebapi/UserSearch/GetOrderPriceSimple?t=1604127708508
>在PriceInfoList数据列表下面多了保价列表。
>```
>
>计算完结果后把前端用户填写的数据返回到后台进行保存
>
>这时买端的操作已经结束，然后把消费者的位置信息进行保存并且放到平台上进行对商家的匹配
>
>由于商家没有网页版，所以使用我的理解进行商家和消费者加第三方的交互逻辑进行简单的描述
>
>在消费者支付完成后，第三方用消费地理位置和商家的地理位置进行匹配，达到一定的匹配度后匹配成功（这是一个大坑）
>
>订单的状态应该是有几种种状态：1、消费者已支付、2、消费者待支付  3、商家待完成  4、未有商家接单返还费用  5、商家完成此单结束
>
>匹配成功后待商家进行任务完成，完成后，一个周期已经结束。





