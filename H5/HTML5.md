
# HTML5

HTML是W3c与WHATWG合作的结果  

W3C 指 World Wide Web Consortium，万维网联盟。  
WHATWG 指 Web Hypertext Application Technology Working Group。  

WHATWG 致力于 web 表单和应用程序，而 W3C 专注于 XHTML 2.0。在 2006 年，双方决定进行合作，来创建一个新版本的 HTML。

# HTML5新特性
HTML5 中的一些有趣的新特性：
1. 用于绘画的 canvas 元素
2. 用于媒介回放的 video 和 audio 元素
3. 对本地离线存储的更好的支持
4. 新的特殊内容元素，比如 article、footer、header、nav、section
5. 新的表单控件，比如 calendar、date、time、email、url、search


- DOCTYPE及字符编码  
- 大小写都可以  （小写）  
- 布尔值  
- 省略引号  （双引号)  
- 可以进行省略的标签


# Canvas

## 什么是 Canvas？
HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像。

画布是一个矩形区域，您可以控制其每一像素。

canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

## 浏览器支持
Internet Explorer 9+, Firefox, Opera, Chrome, 和 Safari 支持 `<canvas>` 元素.

注意: Internet Explorer 8 及更早 IE 版本的浏览器不支持 `<canvas>` 元素.

## Canvas 对象
Canvas 对象表示一个 HTML 画布元素`<canvas>`。它没有自己的行为，但是定义了一个API 支持脚本化客户端绘图操作。你可以直接在该对象上指定宽度和高度，但是，其大多数功能都可以通过CanvasRenderingContext2D 对象获得。 这是通过 Canvas 对象getContext() 方法并且把直接量字符串 "2d" 作为唯一的参数传递给它而获得的。

## Canvas 对象的方法:

|   方法   |   描述   |
| ---- | ---- |
|   getContext()   |   返回一个用于在画布上绘图的环境。   |

语法：  
Canvas.getContext(contextID)  

参数：  
参数 contextID 指定了您想要在画布上绘制的类型。当前唯一的合法值是 "2d"，它指定了二维绘图，并且导致这个方法返回一个环境对象，该对象导出一个二维绘图 API。  

返回值：  
一个 CanvasRenderingContext2D 对象，使用它可以绘制到 Canvas 元素中。

## Canvas 标签
canvas标签是一个矩形区域，它包含两个属性width和height，分别表示矩形区域的宽和高，这两个属性都是可选的，并且都可以通过css来设定，他们的默认值是300px和150px。canvas在网页中的形式如下：  
```
<canvas id="myCanvas" width="300" height="200" style="border:1px solid #c3c3c3;">
       你的浏览器不支持 Canvas 元素。
</canvas>
```

解析：  
1. 为canvas设置id属性是便于Javascript调用；  
2. 第二行是当浏览器不支持canvas标签时，将显示这行文字。  

> 注意: 标签通常需要指定一个id属性 (脚本中经常引用), width 和 height 属性定义的画布的大小。

提示:你可以在HTML页面中使用多个 `<canvas>` 元素。  

使用 style 属性来添加边框。  

## 通过 JavaScript 来绘制

canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成：
```
<script type="text/javascript">
    var c=document.getElementById("myCanvas");
    var cxt=c.getContext("2d");
    cxt.fillStyle="#FF0000";
    cxt.fillRect(0,0,150,75);
</script>
```
JavaScript 使用id 来寻找 canvas 元素：  

var c=document.getElementById("myCanvas");  
然后，创建 context 对象：  

var cxt=c.getContext("2d");  
getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。  
  
下面的两行代码绘制一个红色的矩形：  
cxt.fillStyle="#FF0000";  
cxt.fillRect(0,0,150,75);  
fillStyle 方法将其染成红色，fillRect 方法规定了形状、位置和尺寸。  

## Canvas - 路径
在Canvas上画线，我们将使用以下两种方法：
1. moveTo(x,y) 定义线条开始坐标
2. lineTo(x,y) 定义线条结束坐标

绘制线条我们必须使用到 "ink" 的方法，就像stroke()。

实例  
定义开始坐标(0,0), 和结束坐标 (200,100). 然后使用 stroke() 方法来绘制线条:  
JavaScript:  
```
<script type="text/javascript">
    var c=document.getElementById("myCanvas");
    var ctx=c.getContext("2d");
    ctx.moveTo(0,0);
    ctx.lineTo(200,100);
    ctx.stroke();
</script>
```

在canvas中绘制圆形, 我们将使用以下方法:
```
arc(x,y,r,start,stop)
```
实例  
使用 arc() 方法 绘制一个圆:
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();
```

## 曲线

```
var canvas = document.getElementById('myCanvas');
var context = canvas.getContext('2d');
context.beginPath();
context.moveTo(188, 150);
context.quadraticCurveTo(288, 0, 388, 150);
context.lineWidth = 10;
// line color
context.strokeStyle = 'orange';
context.stroke();
```
quadraticCurveTo() 方法通过使用表示二次贝塞尔曲线的指定控制点，向当前路径添加一个点。  

1. 开始点：moveTo(188,150)  
2. 控制点：quadraticCurveTo(288, 0, 388, 150);  
3. 结束点：quadraticCurveTo(288, 0, 388, 150)  

## 渐变
渐变可以填充在矩形, 圆形, 线条, 文本等等, 各种形状可以自己定义不同的颜色。  
  
两种不同的方式来设置Canvas渐变：  
  
1. createLinearGradient(x,y,x1,y1) - 创建线条渐变  
2. createRadialGradient(x,y,r,x1,y1,r1) - 创建一个径向/圆渐变  

当我们使用渐变对象，必须使用`两种或两种`以上的停止颜色。  

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以是0至1。  
使用渐变，设置fillStyle或strokeStyle的值为 渐变，然后绘制形状。  

使用您指定的颜色来绘制渐变背景：  
```
var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
var grd=cxt.createLinearGradient(0,0,175,50);
grd.addColorStop(0,"#FF0000");
grd.addColorStop(1,"#00FF00");
cxt.fillStyle=grd;
cxt.fillRect(0,0,175,50);
```

## 图像
把一幅图像放置到画布上, 使用以下方法:
  
drawImage(image,x,y)  
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream");
ctx.drawImage(img,10,10);
```


# SVG
- SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
- SVG 用于定义用于网络的基于矢量的图形
- SVG 使用 XML 格式定义图形
- SVG 图像在放大或改变尺寸的情况下其图形质量不会有损失
- SVG 是万维网联盟的标准

与其他图像格式相比（比如 JPEG 和 GIF），使用 SVG 的优势在于：  
- SVG 图像可通过文本编辑器来创建和修改
- SVG 图像可被搜索、索引、脚本化或压缩
- SVG 是可伸缩的
- SVG 图像可在任何的分辨率下被高质量地打印
- SVG 可在图像质量不下降的情况下被放大


在 HTML5 中，您能够将 SVG 元素直接嵌入 HTML 页面中：  
```
<!DOCTYPE html>
<html>
<body>
<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
  <polygon points="100,10 40,180 190,60 10,60 160,180"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;">
</svg>
</body>
</html>
```
代码解释：  
points 属性定义多边形每个角的 x 和 y 坐标  


## SVG 与 Canvas两者间的区别
SVG 是一种使用 XML 描述 2D 图形的语言。  
Canvas 通过 JavaScript 来绘制 2D 图形。  

SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。  

在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。  

Canvas 是逐像素进行渲染的。在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。  


## Canvas 与 SVG 的比较
Canvas:  
依赖分辨率  
不支持事件处理器  
弱的文本渲染能力  
能够以 .png 或 .jpg 格式保存结果图像  
最适合图像密集型的游戏，其中的许多对象会被频繁重绘  
  
SVG:  
不依赖分辨率  
支持事件处理器  
最适合带有大型渲染区域的应用程序（比如谷歌地图）  
复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）  
不适合游戏应用  


# 拖放（Drag 和 drop）是 HTML5 标准的组成部分。
拖放  
拖放是一种常见的特性，即抓取对象以后拖到另一个位置。  

在 HTML5 中，拖放是标准的一部分，任何元素都能够拖放。  

浏览器支持  
Internet Explorer 9、Firefox、Opera 12、Chrome 以及 Safari 5 支持拖放。  

注释：在 Safari 5.1.2 中不支持拖放。  

## 拖动什么 - ondragstart 和 setData()
然后，规定当元素被拖动时，会发生什么。  
在上面的例子中，ondragstart 属性调用了一个函数drag(event)，它规定了被拖动的数据。  

dataTransfer.setData() 方法设置被拖数据的数据类型和值：  
```
function drag(ev)
{
    ev.dataTransfer.setData("Text",ev.target.id);
}
```
在前面的例子中，数据类型是 "Text"，值是可拖动元素的 id ("drag1")。  

## 放到何处 - ondragover
ondragover 事件规定在何处放置被拖动的数据。

默认地，无法将数据/元素放置到其他元素中。如果需要设置允许放置，我们必须阻止对元素的默认处理方式。

这要通过调用 ondragover 事件的 event.preventDefault() 方法：
```
event.preventDefault()
```

## 进行放置 - ondrop
当放置被拖数据时，会发生 drop 事件。  

在上面的例子中，ondrop 属性调用了一个函数drop(event)：
```
function drop(ev)
{
    ev.preventDefault();
    var data=ev.dataTransfer.getData("Text");
    ev.target.appendChild(document.getElementById(data));
}
```
代码解释：  
1. 调用 preventDefault() 来避免浏览器对数据的默认处理（drop 事件的默认行为是以链接形式打开）
2. 通过 dataTransfer.getData("Text") 方法获得被拖的数据。该方法将返回在 setData() 方法中设置为相同类型的任何数据。
3. 被拖数据是被拖元素的 id ("drag1")
4. 把被拖元素追加到放置元素（目标元素）中


# Video
如需在 HTML5 中显示视频，您所有需要的是：  
```
<video width="320" height="240" controls>
   <source src="/example/video/movie.mp4" type="video/mp4">
   <source src="/example/video/movie.ogg" type="video/ogg">
   您的浏览器不支持Video标签。
</video>
```
<video> 元素提供了 播放、暂停和音量控件来控制视频。  

同时<video> 元素也提供了 width 和 height 属性控制视频的尺寸.如果设置的高度和宽度，所需的视频空间会在页面加载时保留。如果没有设置这些属性，浏览器不知道大小的视频，浏览器就不能再加载时保留特定的空间，页面就会更加原始视频的大小而改变。  

<video> 与</video> 标签之间插入的内容是提供给不支持 video 元素的浏览器显示的。  

<video> 元素支持多个 <source> 元素. <source> 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式：  

视频格式
格式	MIME-type
MP4	video/mp4
WebM	video/webm
Ogg	video/ogg

## <video> 标签的属性
属性	 值	描述
autoplay	autoplay	如果出现该属性，则视频在就绪后马上播放。
controls	controls	如果出现该属性，则向用户显示控件，比如播放按钮。
height	pixels	设置视频播放器的高度。
loop	loop	如果出现该属性，则当媒介文件完成播放后再次开始播放。
preload	preload	
如果出现该属性，则视频在页面加载时进行加载，并预备播放。

如果使用 "autoplay"，则忽略该属性。

src	url	要播放的视频的 URL。
width	pixels	设置视频播放器的宽度。

## Video 标签
标签	描述
video	定义一个视频
source	定义多种媒体资源,比如 video 和audio
track	定义在媒体播放器文本轨迹

## HTML5 <video> - 使用 DOM 进行控制
HTML5 <video> 和 <audio> 元素同样拥有方法、属性和事件。  

<video> 和 <audio>元素的方法、属性和事件可以使用JavaScript进行控制.  

其中的方法有用于播放、暂停以及加载等。其中的属性（比如时长、音量等）可以被读取或设置。其中的 DOM 事件能够通知您，比如说，<video> 元素开始播放、已暂停，已停止，等等。  

例中简单的方法，向我们演示了如何使用 <video> 元素，读取并设置属性，以及如何调用方法。  

## HTML5 <video> - 方法、属性以及事件
下面列出了大多数浏览器支持的视频方法、属性和事件：

方法 属性 事件
play()	currentSrc	play
pause()	currentTime	pause
load()	videoWidth	progress
canPlayType	videoHeight	error
 	duration	timeupdate
 	ended	ended
 	error	abort
 	paused	empty
 	muted	emptied
 	seeking	waiting
 	volume	loadedmetadata
 	height	 
 	width	 


# Audio
```
<audio controls>
   <source src="/example/video/horse.ogg" type="audio/ogg">
   <source src="/example/video/horse.mp3" type="audio/mpeg">
   您的浏览器不支持 audio 元素。
</audio>
```
control 属性供添加播放、暂停和音量控件。

在<audio> 与 </audio> 之间你需要插入浏览器不支持的<audio>元素的提示文本 。  

<audio> 元素允许使用多个 <source> 元素. <source> 元素可以链接不同的音频文件，浏览器将使用第一个支持的音频文件  

音频格式的MIME类型
Format	MIME-type
MP3	audio/mpeg
Ogg	audio/ogg
Wav	audio/wav

## `<audio>` 标签的属性
属性  值  描述
autoplay 	autoplay 	如果出现该属性，则音频在就绪后马上播放。
controls controls 如果出现该属性，则向用户显示控件，比如播放按钮。
loop   loop 如果出现该属性，则每当音频结束时重新开始播放。
preload	preload	
如果出现该属性，则音频在页面加载时进行加载，并预备播放。

如果使用 "autoplay"，则忽略该属性。

src	url	要播放的音频的 URL。

## HTML5 Audio 标签
标签	描述
audio	定义了声音内容
source	规定了多媒体资源, 可以是多个，在 <video>与 <audio>标签中使用


## web 存储
HTML5 提供了两种在客户端存储数据的新方法：

1. localStorage - 没有时间限制的数据存储
2. sessionStorage - 针对一个 session 的数据存储

之前，这些都是由 cookie 完成的。但是 cookie 不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得 cookie 速度很慢而且效率也不高。  

在 HTML5 中，数据不是由每个服务器请求传递的，而是只有在请求时使用数据。它使在不影响网站性能的情况下存储大量数据成为可能。  

对于不同的网站，数据存储于不同的区域，并且一个网站只能访问其自身的数据。  

HTML5 使用 JavaScript 来存储和访问数据。  

HTML5 web 存储,一个比cookie更好的本地存储方式。  


## localStorage 和 sessionStorage
这是在客户端存储数据的两个新的对象：

1. localStorage - 没有时间限制的数据存储
2. sessionStorage - 针对一个 session 的数据存储

在使用 web 存储前,应检查浏览器是否支持 localStorage 和sessionStorage:
```
if(typeof(Storage)!=="undefined"){
  // Yes! localStorage and sessionStorage support!
  // Some code.....
} else {
  // Sorry! No web storage support..
}
```

## localStorage 对象
localStorage 对象存储的数据没有时间限制。第二天、第二周或下一年之后，数据依然可用。
```
localStorage.lastname="Smith";
document.getElementById("result").innerHTML="Last name: "+   localStorage.lastname;
```
使用 key="lastname" 和value="Smith" 创建一个 localStorage 键/值对
检索键值为"lastname" 的值然后将数据插入 id="result"的元素中
提示: 键/值对通常以字符串存储，你可以按自己的需要转换该格式。


## essionStorage 对象
sessionStorage 方法针对一个 session 进行数据存储。当用户关闭浏览器窗口后，数据会被删除。
```
<script type="text/javascript">
     sessionStorage.lastname="Smith";
     document.write(sessionStorage.lastname);
</script>
```


# Application Cache
HTML5 引入了应用程序缓存，这意味着 web 应用可进行缓存，并可在没有因特网连接时进行访问。

应用程序缓存为应用带来三个优势：

1. 离线浏览 - 用户可在应用离线时使用它们
2. 速度 - 已缓存资源加载得更快
3. 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源。

## Cache Manifest 基础
如需启用应用程序缓存，请在文档的 <html> 标签中包含 manifest 属性：
```
<html manifest="demo.appcache">
<body>
      ......
</body>
</html>
```
每个指定了 manifest 的页面在用户对其访问时都会被缓存。  
如果未指定 manifest 属性，则页面不会被缓存（除非在 manifest 文件中直接指定了该页面）。

Tmanifest 文件的建议的文件扩展名是：".appcache"。

请注意，manifest 文件需要配置正确的 MIME-type，即 "text/cache-manifest"。必须在 web 服务器上进行配置。

## Manifest 文件
manifest 文件是简单的文本文件，它告知浏览器被缓存的内容（以及不缓存的内容）。

manifest 文件可分为三个部分：

1. CACHE MANIFEST - 在此标题下列出的文件将在首次下载后进行缓存
2. NETWORK - 在此标题下列出的文件需要与服务器的连接，且不会被缓存
3. FALLBACK - 在此标题下列出的文件规定当页面无法访问时的回退页面（比如 404 页面）


## CACHE MANIFEST
第一行，CACHE MANIFEST，是必需的：
```
CACHE MANIFEST
/theme.css
/logo.gif
/main.js
```
上面的 manifest 文件列出了三个资源：一个 CSS 文件，一个 GIF 图像，以及一个 JavaScript 文件。  
当 manifest 文件加载后，浏览器会从网站的根目录下载这三个文件。然后，无论用户何时与因特网断开连接，这些资源依然是可用的。

## NETWORK
下面的 NETWORK 小节规定文件 "login.php" 永远不会被缓存，且离线时是不可用的：
```
NETWORK:
login.php
```
可以使用星号来指示所有其他资源/文件都需要因特网连接：
```
NETWORK:
*
```

## FALLBACK
下面的 FALLBACK 小节规定如果无法建立因特网连接，则用 "offline.html" 替代 /html5/ 目录中的所有文件：
```
FALLBACK:
/html/ /offline.html
```
注意: 第一个 URI 是资源，第二个是替补。


# 更新缓存
一旦应用被缓存，它就会保持缓存直到发生下列情况：

1. 用户清空浏览器缓存
2. manifest 文件被修改（参阅下面的提示）
3. 由程序来更新应用缓存

# 完整的 Manifest 文件
```
CACHE MANIFEST
# 2012-02-21 v1.0.0
/theme.css
/logo.gif
/main.js
 
NETWORK:
login.php
 
FALLBACK:
/html/ /offline.html
```
提示:以 "#" 开头的是注释行，但也可满足其他用途。应用的缓存会在其 manifest 文件更改时被更新。  
如果您编辑了一幅图片，或者修改了一个 JavaScript 函数，这些改变都不会被重新缓存。更新注释行中的日期和版本号是一种使浏览器重新缓存文件的办法。

## 关于应用程序缓存的说明
请留心缓存的内容。

一旦文件被缓存，则浏览器会继续展示已缓存的版本，即使您修改了服务器上的文件。为了确保浏览器更新缓存，您需要更新 manifest 文件。

注释：浏览器对缓存数据的容量限制可能不太一样（某些浏览器设置的限制是每个站点 5MB）。


# Web worker 
Web worker 是运行在后台的 JavaScript，不会影响页面的性能。  

什么是 Web Worker？  
当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。  

web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。  

浏览器支持  
所有主流浏览器均支持 web worker，除了 Internet Explorer。

## 检测 Web Worker 支持
在创建 web worker 之前，请检测用户的浏览器是否支持它：
```
if(typeof(Worker)!=="undefined")
{
  // Yes! Web worker support!
  // Some code.....
}
else
{
  // Sorry! No Web Worker support..
}
```

## 创建 web worker 文件
现在，让我们在一个外部 JavaScript 中创建我们的 web worker。  

在这里，我们创建了计数脚本。该脚本存储于 "demo_workers.js" 文件中：
```
var i=0;
  
function timedCount()
{
   i=i+1;
   postMessage(i);
   setTimeout("timedCount()",500);
}
  
timedCount();
```
以上代码中重要的部分是 postMessage() 方法 - 它用于向 HTML 页面传回一段消息。  

注释：web worker 通常不用于如此简单的脚本，而是用于更耗费 CPU 资源的任务。  

## 创建 Web Worker 对象
我们已经有了 web worker 文件，现在我们需要从 HTML 页面调用它。

下面的代码检测是否存在 worker，如果不存在，- 它会创建一个新的 web worker 对象，然后运行 "demo_workers.js" 中的代码：
```
if(typeof(w)=="undefined")
{
    w=new Worker("/example/data/demo_workers.js");
}
```
然后我们就可以从 web worker发生和接收消息了。

向 web worker 添加一个 "onmessage" 事件监听器：
```
w.onmessage=function(event){
    document.getElementById("result").innerHTML=event.data;
};
```
当 web worker 传递消息时，会执行事件监听器中的代码。event.data 中存有来自 event.data 的数据。

## 终止 Web Worker
当我们创建 web worker 对象后，它会继续监听消息（即使在外部脚本完成之后）直到其被终止为止。

如需终止 web worker，并释放浏览器/计算机资源，请使用 terminate() 方法：
```
w.terminate();
```

## Web Workers 和 DOM
由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象：  
1. window 对象
2. document 对象
3. parent 对象


# Server-Sent
HTML5 服务器发送事件（server-sent event）允许网页获得来自服务器的更新。  
Server-Sent 事件 - 单向消息传递  
Server-Sent 事件指的是网页自动获取来自服务器的更新。  

以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过服务器发送事件，更新能够自动到达。  

例子：Facebook/Twitter 更新、估价更新、新的博文、赛事结果等。  

浏览器支持  
所有主流浏览器均支持服务器发送事件，除了 Internet Explorer。  

## 接收 Server-Sent 事件通知
EventSource 对象用于接收服务器发送事件通知：
```
var source=new EventSource("/example/data/demo.php");
source.onmessage=function(event)
{
    document.getElementById("result").innerHTML+=event.data + "<br />";
};
```
1. 创建一个新的 EventSource 对象，然后规定发送更新的页面的 URL（本例中是 "demo.php"）  
2. 每接收到一次更新，就会发生 onmessage 事件  
3. 当 onmessage 事件发生时，把已接收的数据推入 id 为 "result" 的元素中  

## 检测 Server-Sent 事件支持
以下实例，我们编写了一段额外的代码来检测服务器发送事件的浏览器支持情况：
```
if(typeof(EventSource)!=="undefined")
{
  // Yes! Server-sent events support!
  // Some code.....
}
else
{
  // Sorry! No server-sent events support..
}
```

# 服务器端代码实例
为了让上面的例子可以运行，您还需要能够发送数据更新的服务器（比如 PHP 和 ASP）。  

服务器端事件流的语法是非常简单的。把 "Content-Type" 报头设置为 "text/event-stream"。现在，您可以开始发送事件流了。  

PHP 代码 (demo.php)：  
```
<?php
header('Content-Type: text/event-stream');
header('Cache-Control: no-cache');
  
$time = date('r');
echo "data: The server time is: {$time}\n\n";
flush();
?>
```
ASP 代码 (VB) (demo.asp):  
```
<%
Response.ContentType="text/event-stream"
Response.Expires=-1
Response.Write("data: " & now())
Response.Flush()
%>
```
把报头 "Content-Type" 设置为 "text/event-stream"  
规定不对页面进行缓存  
输出发送日期（始终以 "data: " 开头）  
向网页刷新输出数据  

推送的信息格式必须为”data:内容\n\n“，否则。。。

# EventSource 对象
在上面的例子中，我们使用 onmessage 事件来获取消息。不过还可以使用其他事件：

事件 描述
onopen 当通往服务器的连接被打开
onmessage 当接收到消息
onerror 当错误发生



































# 新增标签  
- 结构标签
- 表单标签
- 媒体标签
- 其他功能标签  

mark标签  
progress标签  
time标签  
ruby标签  
rt标签  
wbr标签  
canvas标签  
command标签  
details标签  
datalist标签  
keygen标签  
output标签  
source标签  
menu标签  


# 删除标签  
- 可以用css代替的标签  
- 不在使用frame  
- 只有个别浏览器支持的标签  
- 其他不常用的标签  


# 新增属性
- 表单属性
- 链接属性
- 其他属性

```
<html manifast="cache.manifest"></html>  
<link rel="icon" href="demo_icon.gif" type="image/gif" sizes="16*16">  
<base href="http://localhost/" target="_blank">  
  
<script defer src="http://code.jquery.com/jquery-1.10.1.min.js" onload="alert('a')"></script>  
<script async src="http"//code.jquery.com/jquery-migrate-1.21.min.js" onload="alert('b')"></script>  
  
<a media="handheld" href="#">手持</a>  
<a media="tv" href="#">电视</a>  
<a href="http://www.mortalliao.win/" herflang="zh" ref="external">网站</a>  
  
<menu type="toolbar" label="Menu">
    <li><input type="checkbox"/>Red</li>
    <li><input type="checkbox"/>Blut</li>
</menu>
  
<div>
    <style type="text/css" scoped>
        h1{color:red;}
        p{color:blue;}
    </style>
    <h1>This is a head</h1>
    <p>This is a paragraph</p>
</div>
```

# 废除属性
- 可以用CSS代替的属性  
- 多余属性  
- 其他属性  












