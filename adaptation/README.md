## UI 适配部分

### 基本概念

#### px、dpi、ppi、dip、dp、ppi、pt、sp、分辨率、像素密度等概念

px：pixel，像素。一个像素通常认为视频中的完整取样，是一个抽象的取样。

dpi：dot per inch，每英寸点数。多用于印刷。

ppi：pixel per inch，每英寸像素。多用于屏幕显示。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/DPI_and_PPI.png/250px-DPI_and_PPI.png)

以上左图为 PPI，右图为 DPI。

参考：https://zh.wikipedia.org/wiki/%E6%AF%8F%E8%8B%B1%E5%AF%B8%E7%82%B9%E6%95%B0

dip：device-independent pixel，设备独立像素，也可以缩写成dp。

设备独立像素（dip/dp）是一个计算机基于坐标系的一个物理测量单位，同时表示一个应用使用的抽象像素，下浮系统转换成物理像素。

一个典型应用的例子，就是允许移动设备软件可以调整信息在不同的屏幕尺寸中的 UI 显示。这种抽象允许应用将像素作为一个测量单位，下浮图像系统将应用的抽象的像素转换成特定设备恰当的像素测量。例如，在 Android 操作系统中，1 dip/dp 相当于在 160 dpi 屏幕上的一个物理像素，同时 WPF （Windows Presentation Foundation）指定 1dip/dp 相当于 1/96 英寸。

dip/dp 作为一个物理单位，是一个传统的可以被测量的有绝对值的。例如：对于 Android 设备来说，1dip/dp 等于 1/160 英寸，或者 0.15875 mm。

然而，传统的像素仅仅作为显示信息的一个参考，dip/dp 也可以用来测量用户输入，比如在触摸屏设备中的输入。

参考：https://en.wikipedia.org/wiki/Device-independent_pixel  
https://blogs.msdn.microsoft.com/text/2009/12/11/wpf-text-measurement-units/  
http://stackoverflow.com/questions/2025282/what-is-the-difference-between-px-dp-dip-and-sp-on-android  
https://material.google.com/layout/units-measurements.html#

dp：dp = dip = device-inpendent pixel。

ppi：pixel per inch，每英寸像素。又被称为像素密度，是一个表示打印图像或者显示器单位面积上像素数量的指数。一般用来计量电脑显示器，电视机和手持电子设备屏幕的精细程度。通常情况下，每英寸像素值越高，屏幕能显示的图像也越精细。

有研究表明，人类肉眼能够分辨的最高像素点密度是 300 ppi，超过 300 ppi 的屏幕被常常成为 Retina 显示屏，这个概念最早是由苹果公司于 2010 年推出 iPhone 4 手机的时候提出来的。但是人眼能否分辨两个像素与观察图像的炬力和人的视力也有很大的关系。另外，根据现实亮度的不同，或是图像由不同的介质显示（纸张或显示器），人眼的分辨能力也会改变。因此，“人眼像素分辨率为 300 ppi”有一定的广告宣传成分。

参考：https://zh.wikipedia.org/wiki/%E6%AF%8F%E8%8B%B1%E5%AF%B8%E5%83%8F%E7%B4%A0
     

电脑与手机屏幕的每英寸像素值取决于尺寸和分辨率，通常指的就是每英寸上的像素点数。  
例如一台 4:3 的 15" 显示器，分辨率为 1024 × 768 (XGA)，其横向和纵向的像素密度均为 85 ppi。  
备注：计算方法：15"为斜对角的长度，根据直角三角形计算，4:3 对应的边长度分别为 12:9 inch，1024 × 768 就是 1024 pixel × 768 pixel，那么横向和纵向的像素密度分别为：768/12 ≈ 85.333333， 1024/12 ≈ 85.333333，都是约等于 85 ppi。  
同样的一台显示器，如果分辨率设置的不同，像素点设置也不同，分辨率越高，每英寸像素值也会越高。备注：实际的长度物理尺寸是不会变化的。对应长度上的分辨率越高，这样每英寸像素值也会越高。

一台显示器的像素密度是由显示单元之间的点距决定的。一台显像管或者液晶显示器的像素密度大约是 67 - 130 ppi，而现在笔记本电脑的屏幕能够达到 200 ppi，个别产品甚至可以高达 300 ppi。

2008 年 1 月，美国高平公司发布了一款 0.44 英寸的 SVGA 显示器，其像素密度高达 2272 ppi，每个像素点之间的点距只有11.25微米。这款显示器未来将在眼部成像技术上使用。  
全息摄影对像素密度要求更高，因为高密度带来的是更大的画面尺寸和更多的成像角度。最新的空间光调制器每个像素点之间的点距只有 2.5微米，像素密度则是高达 10160 ppi。

PPI 的计算。

电脑和移动设备（手机和平板）  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/d30ee099bd8351610c8746eeb1128aba5e786b86)  

以屏幕尺寸为4 inch 的 iPhone 5为例，分辨率为 1136 × 640，像素密度为 326 ppi，就是通过先计算斜边对应的像素，然后除以斜边的长度 4 inch，得到的像素密度为 326 ppi。

参考:

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/%27Map%27_on_Retina_Display.jpg/220px-%27Map%27_on_Retina_Display.jpg)

由于屏幕的尺寸并不代表其实际的物理尺寸，因此可能会有一定的误差，比如 21.5 inch 的 iMac 实际尺寸为 21.465 inch，这样计算会有一定的误差，但是影响并不是很大。

参考：  
http://theground.jimdo.com/android/android-screen-size-ldpi-mdpi-hdpi/

<!-- language: none -->

    +----------------+----------------+---------------+-------------------------------+
    | Density Bucket | Screen Density | Physical Size | Pixel Size                    | 
    +----------------+----------------+---------------+-------------------------------+
    | ldpi           | 120 dpi        | 0.5 x 0.5 in  | 0.5 in * 120 dpi = 60x60 px   | 
    +----------------+----------------+---------------+-------------------------------+
    | mdpi           | 160 dpi        | 0.5 x 0.5 in  | 0.5 in * 160 dpi = 80x80 px   | 
    +----------------+----------------+---------------+-------------------------------+
    | hdpi           | 240 dpi        | 0.5 x 0.5 in  | 0.5 in * 240 dpi = 120x120 px | 
    +----------------+----------------+---------------+-------------------------------+
    | xhdpi          | 320 dpi        | 0.5 x 0.5 in  | 0.5 in * 320 dpi = 160x160 px | 
    +----------------+----------------+---------------+-------------------------------+
    | xxhdpi         | 480 dpi        | 0.5 x 0.5 in  | 0.5 in * 480 dpi = 240x240 px | 
    +----------------+----------------+---------------+-------------------------------+
    | xxxhdpi        | 640 dpi        | 0.5 x 0.5 in  | 0.5 in * 640 dpi = 320x320 px | 
    +----------------+----------------+---------------+-------------------------------+
        
<!-- language: none -->

    +---------+-------------+---------------+-------------+--------------------+
    | Unit    | Description | Units Per     | Density     | Same Physical Size | 
    |         |             | Physical Inch | Independent | On Every Screen    | 
    +---------+-------------+---------------+-------------+--------------------+
    | px      | Pixels      | Varies        | No          | No                 | 
    +---------+-------------+---------------+-------------+--------------------+
    | in      | Inches      | 1             | Yes         | Yes                | 
    +---------+-------------+---------------+-------------+--------------------+
    | mm      | Millimeters | 25.4          | Yes         | Yes                | 
    +---------+-------------+---------------+-------------+--------------------+
    | pt      | Points      | 72            | Yes         | Yes                | 
    +---------+-------------+---------------+-------------+--------------------+
    | dp      | Density     | ~160          | Yes         | No                 | 
    |         | Independent |               |             |                    | 
    |         | Pixels      |               |             |                    | 
    +---------+-------------+---------------+-------------+--------------------+
    | sp      | Scale       | ~160          | Yes         | No                 | 
    |         | Independent |               |             |                    | 
    |         | Pixels      |               |             |                    | 
    +---------+-------------+---------------+-------------+--------------------+
        
More info can be also be found in the [Google Design Documentation](https://www.google.com/design/spec/layout/units-measurements.html#).

XHDPI往往指的是具有类似于苹果Retina显示屏显示效果的屏幕。[12]。不同等级的屏幕显示效果相差颇多，下图为iPhone 3GS和iPhone 4显示效果的对比：

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Non-Retina_Display.jpg/400px-Non-Retina_Display.jpg)  
![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/63/Retina_Display.jpg/400px-Retina_Display.jpg)

以下为 *GA 的区别。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Vector_Video_Standards2.svg/749px-Vector_Video_Standards2.svg.png)

其他参考：  
http://theground.jimdo.com/android/android-screen-size-ldpi-mdpi-hdpi/  
https://en.wikipedia.org/wiki/Retina_Display  
https://zh.wikipedia.org/wiki/Retina%E6%98%BE%E7%A4%BA%E5%B1%8F  
https://blogs.msdn.microsoft.com/text/2009/12/11/wpf-text-measurement-units/

http://www.jianshu.com/p/ea0c362ed4b6
*******

UI 适配部分。

1.iOS 状态栏适配的问题。

从Xcode6版本开始，模拟器新增了 iPhone 6 和 iPhone 6 Plus 两种，如果旧的⼯程直接跑到这两个模式时，默认是”兼容模式”，即系统会简单的把内容等⽐例放⼤，
这⼀点表现在我们之前的⼯程⾥表现显著就是，放⼤的状态栏。

启用高分辨率模式的两种方法：  
1°：添加大屏 LaunchImage   
在 Images.xcassets 里，删除旧的 LaunchImage 组，然后新建 LaunchImage 组，对应高分辨率的图片。  
2°：添加 Launch Screen File  
这个是在 Xcode 6，iOS 8 中新增的功能，可以使用 xib storyboard 来生成启动动画，在旧版本的时候，会被自动忽略。

2.对于设计师来说，是否只需要一个 @3x 图片即可。  
1°：png 方案。设计师可以使用 iPhone 6s Plus 来出设计稿，开发拿到切图之后，通过 3x 然后缩小。
2°：矢量图方案。  
3°：插件自动生成 @2x 图。


*********

总结之前对各种iOS屏幕做的适配，现对iOS适配总结如下：
iOS App适配总结：
新项目适配
1、导航：高度固定，导航左右按钮大小保持不变，中间的标题自动按屏幕宽度等比拉伸。

2、Tabbar : 高度固定，上边的按钮宽度随屏幕宽度自动拉伸，图片、字体大小对按钮的相对位置保持不变，大小亦不变。

3、其他控件 :设定一个比率因子（最好定义为一个通用的内联函数或宏）（以当前设备屏幕宽与设计图标准屏幕宽的比值）在不同屏幕上等比率缩放。

4、字体：以设计图屏幕为准，在其他屏幕上等比率放大字体大小。

5、网络图片的显示问题： 图片尺寸选择为当前能适应所有机型中最大的图片即可。

6、4S尺寸的适配：若内容太多，放不下，可添加滑动进行解决。

7、当xib + autolayout 做适配时，最好加上添加sizeclass 做竖屏适配，防止TableViewCell或ViewController'view 无法铺满屏幕的情况。

8、若使用autoresize 进行适配（不使用autolayout），需注意勾选好每个子视图随父视图变化时的变化情况。

9、添加上所有机型的闪屏图。

旧App适配维护更新
对未添加6、6p闪屏的情况的适配

1、当添加上6、6p闪屏之后的情况后出现了个ViewController视图铺不满屏幕的情形。如果视图是用xib进行初始化，且使用了autolayout,需重新设置约束，最好加上sizeclass进行适配各种屏幕；如果视图未使用autolayout,则重设autoresize的各个参数。

2、字体、控件大小调节，同上，分两种情形进行设置即可（xib + autolayout + sizeclass）或autoresise 此举针对使用xib 的情形。若未使用xib，按比率因子设置宽高和字体大小即可。

2.对于设计师来说，是否只需要一个 @3x 图片即可。  
1°：png 方案。设计师可以使用 iPhone 6s Plus 来出设计稿，开发拿到切图之后，通过 3x 然后缩小。
2°：矢量图方案。  
3°：插件自动生成 @2x 图。

3.对于国际化翻译中会出现的文本有长短的情况。可以尝试通过第三方的文本排版引擎来解决，待确认。YYText。

4.对于开发人员来说，是否只需要加载 @3x 图片。这个有待确认。

5.对于尺寸标注标注转换问题。

***********

系统版本功能适配点。

iOS 9 与之前的版本。

iOS 10 与之前的版本。


