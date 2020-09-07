## 一、概念 

SVG是XML语言的一种形式，有点类似XHTML，它可以用来绘制矢量图形。SVG可以通过定义必要的线和形状来创建一个图形，也可以修改已有的位图，或者将这两种方式结合起来创建图形。图形和其组成部分可以变形，可以合成，还可以通过滤镜完全改变外观，因此使用SVG可以创建简单的动画效果。

## 二、本质

SVG 的本质特征是它基于 XML，它是矢量图形的一种，同 HTML 一样，SVG 是一种文件格式，有自己的 API。

但HTML5引入了内连 SVG，所以 SVG 元素现在可以直接出现在 HTML 标记中。

## 三、优缺点

### 1、优点

* SVG 可被非常多的工具读取和修改（比如记事本）
* SVG 与 JPEG 和 GIF 图像比起来，尺寸更小，且可压缩性更强
* SVG 是可伸缩的，其图像可在任何的分辨率下被高质量地打印，可在图像质量不下降的情况下被放大
* SVG 图像中的文本是可选的，同时也是可搜索的（很适合制作地图）
* SVG 是开放的标准
* SVG 文件是纯粹的 XML
* 与 Flash 相比，SVG 最大的优势是与其他标准（比如 XSL 和 DOM）相兼容。而 Flash 则是未开源的私有技术。

### 2、缺点

* IE9以下IE系列浏览器不支持SVG格式图片
* 没有进行压缩时，比其他矢量图格式稍大

### 3、与Canvas的重要区别


（1）SVG 绘制的文本可选，而 Canvas 不能（因为 Canvas 文本用像素绘制，是图像的一部分）；

（2）SVG 上的文本是可搜索的，Canvas 上的文本无法被搜索引擎获取。

（3）SVG可以绑定事件处理，而Canvas不可以对特定元素绑定事件

（4）SVG不大适合游戏开发，而Canvas比较适合网页游戏的开发

## 四、SVG的使用

在HTML中使用SVG有两种方式：
* 1、可以在HTML文件中直接嵌入svg内容
* 2、也可以直接引入后缀名为.svg的文件，类似引入普通图片
如：

```html
/* svg标签直接嵌入 */
/* 对浏览器要求较高，IE9以上，iOS全面支持，Andriod4.4以上全面支持，Andriod3~4.3不支持遮罩 */
<svg width="200" height="200">
  <rect width="20" height="20" fill="red"></rect>
</svg>

/* 引入后缀名为.svg的文件 */

/* 方法一 通过<embed>引入 */
/* <embed> 标签被所有主流的浏览器支持，并允许使用脚本。*/
/* 当在 HTML 页面中嵌入 SVG 时使用 <embed> 标签是 Adobe SVG Viewer 推荐的方法！*/
/* 然而，如果需要创建合法的 XHTML，就不能使用 <embed>。任何 HTML 规范中都没有 <embed> 标签。 */
<embed src="rect.svg" width="300" height="100" type="image/svg+xml" pluginspage="http://www.adobe.com/svg/viewer/install/" />

/* 方法二 通过<object>引入 */
/* <object> 标签是 HTML 4 的标准标签，被所有较新的浏览器支持。它的缺点是不允许使用脚本。 */
/* 假如安装了最新版本的 Adobe SVG Viewer，那么当使用 <object> 标签时 SVG 文件无法工作（至少不能在 IE 中工作）！ */
<object data="rect.svg" width="300" height="100" type="image/svg+xml" codebase="http://www.adobe.com/svg/viewer/install/" />

/* 方法三 通过<iframe>引入 */
/* <iframe> 标签可工作在大部分的浏览器中。缺点是新的html规范已移除此标签 */
<iframe src="rect.svg" width="300" height="100"></iframe>
```

用以下方式创建独立的SVG文件：

```xml
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
   <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />
</svg>
```


**注意：svg为inline水平元素。且需要绘制的所有图形都应被包含在<svg></svg>标签内**

### 1、SVG坐标系特点

SVG中坐标系的特点：

y轴向下
顺时针方向的角度为正值

![image](http://upload-images.jianshu.io/upload_images/1500315-3ca092074e1f6901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/300)

另外要注意：元素的所有操作都是相对自身坐标系进行的

### 2、SVG颜色设置

**RGB:** 三个分量：红色、绿色、蓝色，每个分量的取值范围[0, 255]，优点是显示器更容易解析。

**HSL:** 三个分量：颜色h、饱和度s%、亮度l%，每个分量的取值范围分别是[0, 359], [0, 100%], [0, 100%],，其中，h=0表示红色， h=0表示120绿色，h=0表示240 蓝色。

[基于HSL的配色方案](http://paletton.com/)

### 3、SVG元素属性
* 1. width，height

用来控制SVG视图的宽度和高度

* 2. viewBox

定义用户视野的位置以及大小，即定义用来观察SVG视图一个矩形区域，如：viewBox ='20 20 100 100'，前两个参数表示viewBox视野相对svg视图的x y坐标，后两个参数表示viewBox的大小。

与svg实际大小的关系如下：

![image](https://camo.githubusercontent.com/7885f3bd1483b9e55113424aeed4579af8e38a7a/687474703a2f2f75706c6f61642d696d616765732e6a69616e7368752e696f2f75706c6f61645f696d616765732f313530303331352d663130303035366439333861333866632e706e673f696d6167654d6f6772322f6175746f2d6f7269656e742f7374726970253743696d61676556696577322f322f772f343030)

如上图所示，用户可以看到蓝色星星的一部分，而星星的另一侧是看不到的。

### 4、基本SVG内部元素及其样式

#### 基本元素类型

* 图形元素（矩形，圆形，椭圆形，线段，折线与多边形，路径，曲线/弧线）
* 文字元素
* 特殊元素（克隆元素，模板元素，组元素，裁剪元素，遮罩元素（安卓存在兼容问题），tspan元素，超链接元素，标记元素，笔刷元素）
* 滤镜元素（[svg滤镜入门，包括了阴影的实现](https://isux.tencent.com/svg-filter.html)）
* 渐变元素（线性渐变，径向渐变）

**[基本元素用法](https://github.com/junruchen/junruchen.github.io/wiki/SVG%E5%9F%BA%E7%A1%80%E4%B9%8B%E5%86%85%E9%83%A8%E5%85%83%E7%B4%A0)**

#### 基本元素样式

**1.填充**

* fill：定义填充颜色以及文字颜色
* fill-opacity：定义填充颜色的透明度
* fill-rule：指定采用的填充规则，符合填充规则 [即位于图形内部的点] 的才可被填充，取值：[nonzero | evenodd | inherit]，默认值为nonzero。
* nonzero： 该规则判断点任意方向的射线与图形路径的相交情况，默认为数值0，射线从左到右时，每穿过一条路径，数值加1；从右到左时，每穿过一条路径，数值减1，最后结果若为0，则表示点不在图形内部，不能填充。
* evenodd：该规则判断点任意方向的射线与图形路径的相交情况，相交个数为奇数，则点在图形内部，可进行填充；反之在外部，不进行填充。

**2.边框**

* stroke：边框颜色
* stroke-width：边框宽度
* stroke-opacity：边框透明度，取值[ 0, 1 ]
* stroke-linecap：单条线端点样式，一般应用于直线或者路径， 取值：[ butt | square | round ]，分别是对接、方形和圆形
* stroke-dasharray：虚线边框，可设置每段虚线的长度和间隔，之间使用逗号分隔或者空格分隔，如：stroke-dasharray="10, 5, 5, 10"
* stroke-dashoffset：设置虚线描边偏移量，使图案向前移动
* stroke-linejoin：两条线段之间衔接点的样式，取值：[ miter | round | bevel ]，分别是尖角、圆角和斜角
* stroke-miterlimit：默认值4，当miterLength / stroke-width < stroke-miterlimit时，stroke-linejoin值会变成换成bevel斜角。

**3. 透明度**

* opacity：定义整个图形元素透明度

**4. 字体**

* font-size：字体大小
* font-family：字体系列的名称
* font-weight : 字体粗细
* font-style：字体样式，斜体或正常
* text-decoration：下划线样式
* text-anchor：设置文本的排列属性，属性值[start | middle | end | inherit]，如：middle表示，将文字定位原点移动至文字中心。


**5. 变换**

基本概念同css

* transform：同css，默认以左上角为旋转中心，如：transform="rotate(30)"
* transform-origin：同css，设置旋转等操作中心
* rotate：设置文字元素中每个文字的旋转角度，正值为顺时针旋转，注意区分rotate与transform中的rotate，如：rotate="30"


![image](https://camo.githubusercontent.com/9e3882b07be8eb4722fab8690af7786705d5428b/687474703a2f2f75706c6f61642d696d616765732e6a69616e7368752e696f2f75706c6f61645f696d616765732f313530303331352d323037343934626430323961626533662e706e673f696d6167654d6f6772322f6175746f2d6f7269656e742f7374726970253743696d61676556696577322f322f772f333030)


 而transform中的rotate是对整个元素进行旋转操作。
 
 ### 5、SVG兼容性
 
 **直接使用svg标签嵌入html**
 
 在这种情况下的兼容性如下所示：
 
 ![image](http://note.youdao.com/yws/public/resource/66c9564cfac4ea8034fdfa9e8dfc65aa/xmlnote/DC499F039C8C4302A8F4E481F6B0F48F/1390)
 
 ![image](http://note.youdao.com/yws/public/resource/66c9564cfac4ea8034fdfa9e8dfc65aa/xmlnote/AD3D41202F9B4CDDBE8662E665F6399C/1391)
 
 **使用svg相关的js库**
 
 在这种情况下兼容性取决于js库的具体实现情况，有的js库就是为了扩展svg兼容性，所以兼容性要好一些，有的则和使用原生svg一样，仅仅只是操作更加便捷，其中需要提一下的是，类似于Raphael的库之所以能做到将SVG兼容到IE6，是因为这个库做了很多兼容处理，对于低版本不支持SVG的浏览器，这些库使用VML（矢量可标记语言）来实现了与SVG相同的效果，从而做到最大限度兼容。
 
 **SVG向下兼容技术**
 
 由于在IE8-以及Android 2.3默认浏览器是不支持SVG的，假如想让使用了SVG的页面在这些页面不显示错误信息，那么需要对SVG文件作一些向下兼容的处理，这里介绍一种比较巧妙的做法：**svg image标签降级技术**
 
 做法很简单，如下面的代码：
 
 ```xml
 <svg width="96" height="96">
  <image xlink:href="svg.svg" src="svg.png" width="96" height="96" />
</svg>
 ```
 
上面这个技术非常巧妙，其创意借鉴了一个研究成果，即所有浏览器，包括IE，会把`<image>`标签渲染成`<img>`标签，而SVG中的`<image>`作用是：

> Provides a way to display a graphics image on the screen.

也就是提供在屏幕上显示一个图形图像的方法。
 
于是，通过上面的方法，如果浏览器支持SVG，则SVG显示；对于不支持的浏览器，例如IE8浏览器，会忽略svg标签的存在，直接渲染image，在其看来，这就是个img标签，于是，图像就以svg.png的形式显示了。
 
参考 [SVG向下兼容优雅降级技术](http://www.zhangxinxu.com/wordpress/2013/09/svg-fallbacks/)
 

### 6、SVG动画能力

- [x] 移动
- [x] 缩放
- [x] 颜色变化
- [x] 大小变化
- [x] 形状变化
- [x] 透明度变化
- [x] 路径变化
- [x] 路径动画


### 7、SVG动画的实现

* svg原生方法实现（SMIL）

通过几个svg动画元素，可以实现一些简单的svg动画

<animate>
<animateMotion>
<animateTransform>
<mpath>

如下代码：

```xml
<svg width="120" height="120" 
     viewPort="0 0 120 120" version="1.1"
     xmlns="http://www.w3.org/2000/svg">
	
    <rect x="10" y="10" width="100" height="100">
        <animate attributeType="XML"
                 attributeName="x"
                 from="-100" to="120"
                 dur="10s"
                 repeatCount="indefinite"/>
    </rect>
	
</svg>
```

代码通过使用`animate`标签来实现矩形的平移动画。通过这种形式，SVG文件不需要JS的操作就能实现动画的执行。


[使用方法](http://www.tuicool.com/articles/2EJj6jF) 和 [效果展示](http://jsrun.net/sspKp)

[入门学习1](https://isux.tencent.com/svg-animate.html)

[入门学习2](http://www.zhangxinxu.com/wordpress/2014/08/so-powerful-svg-smil-animation/)

[Chrome弃用SMIL](http://tgideas.qq.com/webplat/info/news_version3/804/7104/7106/m5723/201610/514918.shtml)

> 注意：以上方法IE不支持，且Chrome也在后期弃用了SMIL，只能以CSS属性动画keyframes来替代

* JS / CSS实现

SVG本质上就是HTML，因此，CSS2/CSS3的一些特性，SVG也是可以受用的。例如，尺寸变化，位置变化，各种颜色变化，transform变换等等。同时SVG一些特有的属性，例如fill,stroke-*等也能直接在CSS中设置。不过上面的动画本质上依然是“CSS3图形动画”。差别仅仅是作用在SVG元素上，并且CSS有很多属性并不能控制到，比如svg元素的半径，中心点，路径等等，所以通常还是使用JS来实现svg动画。

使用JS实现SVG动画有两种选择，一是自己实现，二是选择优秀成熟的JS库，由于保障动画效果和谐的首要因素就是不同图形变化中的插值，而自己用JS实现的话，对于复杂图案的变化，插值的计算会相当耗费精力，如下图：

![image](https://misc.aotu.io/cos2004/snapsvg/demo3-1.gif)

临时编写JS计算无规律曲线到心状图的变化插值将会耗费相当多的时间精力，所以通常来说建议使用已有的JS库来实现动画，借助Snap的animate方法就能非常便捷地实现这一效果。

[弹球动画实例](http://samples.msdn.microsoft.com/workshop/samples/svg/svgAnimation/intermediate/03_circleInBox.html)

### 8、常见SVG动画库
 
 * [Raphael](http://dmitrybaranovskiy.github.io/raphael/)

RaphaelJS 通常是用来在网页上画SVG图和动画的，Raphael.js的优点在于兼容低版本的IE浏览器，缺点是体积较大，常年不再更新（作者去维护Snap了），且不支持一些最新的技术与方法。

* [Snap](http://snapsvg.io/)

SnapSVG 是另一个知名 JS 类库，它是由Raphael的作者开发的，并由Adobe维护。和 Raphael 不同的是，它只提供了 ie 最新版 (IE9, Safari, Chrome, Firefox, and Opera)支持。Snap是面向现代浏览器开发的，虽然其不支持低版本的IE浏览器，但是，正因为不需要考虑到兼容，所以，SVG的一些高级特性其就能很好的支持，同时，库JS文件的大小也小很多，可以更专注、更高效、更精彩。

> [snap中文API文档](http://www.zhangxinxu.com/GitHub/demo-Snap.svg/demo/basic/Element.add.php)

> [snap简易教程](https://aotu.io/notes/2017/01/22/snapsvg/index.html)

> 总的来说，Snap 的 API 兼容性不错，官网声称兼容 IE9 及以上、Safari、Chrome、Firefox、Opera;
> 而移动设备方面， iOS、安卓 X5 内核、安卓原生浏览器兼容性都不错;

* [Velocity.js](http://www.mrfront.com/docs/velocity.js/index.html)

Velocity是一个简单易用、高性能、功能丰富的轻量级JS动画库。它能和 jQuery 完美协作，并和$.animate()有相同的 API， 但它不依赖 jQuery，可单独使用，同时，它支持所有常用的SVG属性，所以也可以很好地实现SVG动画。不过Velocity仅提供了最基本的一些属性变化，不能像snap一样支持更高级的创建与变化动作。
 
* [Vivus](http://maxwellito.github.io/vivus/)

Vivus 是一个专门对SVG图形进行描边动画的JS库，它能够像显示出SVG图被画出来的过程。Vivus无依赖，你仅仅需要在页面中加入这个.js文件，然后传入需要被用来动画的SVG部分就行。同时通过指定一些配置，它能够在页面加载后直接显示动画效果。

* [Progressbar.js](http://kimmobrunfeldt.github.io/progressbar.js/)

ProgressBar.js 可以用来制作进度图案，包括进度条，进度环之类的。它集成了一些实用的形状如Range,Circle和Block。ProgressBar.js 是轻量级的开源库，支持IE9+。

* [Bonsai](http://bonsaijs.org/)

Bonsai 是一个无依赖的轻量svg动画库，支持多种媒体资源，拥有完整的图形处理API，兼容性要求IE9+。



### 8、SVG动画优缺点

**SVG动画优点：**
* 1)矢量图形，不受像素影响——SVG的这个特性使得它在不同的平台或者媒体下表现良好，无论屏幕分辨率如何
* 2)SVG对动画的支持较好，其DOM结构可以被其特定语法或者Javascript控制，从而轻松的实现动画
* 3)Javascript可以完全控制SVGDom元素
* 4)SVG的结构是XML，其可访问性（盲文、声音朗读等）、可操作性、可编程性较好、容易被CSS样式化

**SVG动画缺点：**
* 1)DOM比正常的图形慢，而且如果其结点多而杂，就更慢。
* 2)SVG画图表，线条动画较好，不适合制作元素很多的复杂动画，所以不适用于制作网页游戏
* 3)兼容性不太好，尤其是IE的支持，如果添加了动画，在IE中可能显示不出效果


**与Canvas比较**

<canvas>和<svg>都是HTML5推荐使用的图形技术

Canvas基于像素，提供2D绘制函数，是一种HTML元素类型，依赖于HTML，只能通过脚本绘制图形；

SVG为矢量，提供一系列图形元素，还有完整的动画，事件机制，本身就能独立使用，也可以嵌入到HTML中

两者的主要特点见下面的表格：

![image](https://pic4.zhimg.com/b00e22b6281710f76bb784fe13ff9243_b.jpg)


![image](https://pic1.zhimg.com/7cc17f3b9ce5f0d879fdfa2be9a54ca0_b.jpg)


[SVG与Canvas更加细致的比较](https://msdn.microsoft.com/zh-cn/library/gg193983(v=vs.85).aspx)






