# CSS世界 学习笔记 例子

## 第1章 概述

### 1.1 CSS世界的“世界观”

### 1.2 世界都是创造出来的

CSS世界的诞生就是为图文信息展示服务的

### 1.3 CSS完胜SVG的武器——流

#### 1.3.1 何为“流”

“流”实际上是CSS世界中一种基本的定位和布局机制

#### 1.3.2 流是如何影响整个CSS世界的

#### 1.3.3 什么是流体布局

### 1.4 CSS世界的开启从IE8开始

### 1.5 table自己的世界

### 1.6 CSS新世界——CSS3

## 第2章 需提前了解的术语和概念

### 2.1 务必了解的CSS世界的专业术语

1. 属性
2. 值
3. 关键字
4. 变量
5. 长度单位
6. 功能符
7. 属性值
8. 声明
9. 声明块
10. 规则或规则集
11. 选择器
    - 类选择器
    - ID选择器
    - 属性选择器
    - 伪类选择器
    - 伪元素选择器
12. 关系选择器
    - 后代选择器
    - 相邻后代选择器
    - 兄弟选择器
    - 相邻兄弟选择器
13. @规则

### 2.2 了解CSS世界中的未定义行为

## 第3章 流、元素与基本尺寸

### 3.1 块级元素

#### 3.1.1 为什么list-item元素会出现项目符号

每个元素都有两个盒子：外在盒子和容器盒子。外在盒子觉得元素时候换行显示；容器盒子觉得宽高、内容呈现。

#### 3.1.2 display:inline-block 的盒子是怎样组成的

#### 3.1.3 width/height 作用在哪个盒子上

### 3.2 width/height 作用的具体细节

#### 3.2.1 深藏不露的 width:auto

1. 充分利用可用空间
2. 收缩与包裹
3. 收缩到最小
4. 超出容器限制

子元素既保持了inline-block元素的收缩特性，又同时让内容宽度最大，直接无视父级容器的宽度限制。

##### 1. 外部尺寸与流体特性

1. 正常流宽度
2. 格式化宽度

格式化宽度仅出现在决定定位模型中，也就是出现在position属性值为absolute或fixed的元素中。
默认情况下，绝对定位元素的宽度表现是“包裹性”的，即宽度是由内部尺寸决定的。
对于非替换性元素，当left/right或top/bottom对立方位的属性值同时存在的时候，元素的宽度表现为“格式化宽度”，即其宽度大小相对于最近的具有定位特性的祖先元素计算。

##### 2.内部尺寸与流体特性

1. 包裹性
2. 首选最小宽度

    - 东亚文字最小宽度为每个汉字的宽度。
    - 西方文字最小宽度由特定的连续的英文字符单元决定，以空格、短横线、问号以及其他非英文字符分割。
    - 图片的最小宽度就是该元素内容本身的宽度。

3. 最大宽度

最大宽度实际等同于“包裹性”元素设置wihte-space：norwap 声明后的宽度。
如果内部没有块级元素或者块级元素没有设定宽度值，则最大宽度实际上是最大的连续内联盒子的宽度。

#### 3.2.2 width值作用的细节

内在盒子又分为4个盒子，分别是content box、padding box、border box、margin box。

margin的背景永远是透明的。

margin一旦设定具体宽度和高度值，其本身的尺寸是不会因margin值变化而变化的。

设置padding、border后会：
    - 流动性丢失
    - 与现实世界表现不一致的困扰
    width会直接作用于content box上

#### 3.2.3 CSS流体布局下的宽度分离原则

“宽度分离原则”是指CSS中的width属性不与影响宽度的padding/border（有时候包括margin）属性共存。

#### 3.2.4 改变width/height作用细节的box-sizing

#### 3.2.5 相对简单而单纯的height:auto

#### 3.2.6 关于height：100%

对于width属性，父元素的width为auto，百分比值是支持的；但是，对于height属性，如果父元素的height为auto，只要子元素在文档流中，其百分比值就被忽略了。

原因：如果包含块的高度没有显示指定（即高度由内容决定），并且该元素不是绝对定位，则计算值为auto。auto和100%无法一起计算，所以百分比就被忽略了。

##### 如何让元素支持height：100%效果

1. 设定显式的高度值
2. 使用绝对定位

### 3.3 CSS min-width/max-width和min-height/max-height二三事

#### 3.3.1 为流体而生的min-width/max-width

#### 3.3.2 与众不同的初始值

- width/height的默认值为auto。
- min-width/min-height的初始值也是auto。
- max-width/max-height的初始值为none。

#### 3.3.3 超越！important，超越最大

1. 超越！important是指max-width会覆盖添加!important的width属性
2. 超越最大是指在min-width和max-width冲突的时候min-width会覆盖max-width

#### 3.3.4 任意高度元素的展开收起动画技术

- 从0px到auto是无法计算的，因此无法形成过渡或动画效果。
- max-height的值比height计算值大的时候，元素的高度就是height属性的计算值

### 3.4 内联元素

#### 3.4.1 哪些元素是内联元素

#### 3.4.2 内联世界深入的基础——内联盒模型

#### 3.4.3 幽灵空白节点

文档声明为HTML5时，内联元素的所有解析和渲染表现就如同每个行框盒子的前面有一个“空白节点”一样。

## 第4章 盒尺寸四大家族

### 4.1 深入理解content

#### 4.1.1 content与替换元素

1. 什么是替换元素——通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”

    1. 内容的外观不收页面上CSS的影响
    2. 有自己的尺寸
    3. 在很多CSS属性上有自己的一套表现规则

2. 替换元素的默认display值
3. 替换元素的尺寸计算规则
    1. 固有尺寸指的是替换内容原本的尺寸
    2. HTML尺寸
    3. CSS尺寸特指可以通过CSS的width和height或者max-width/min-width和max-height/min-height设置的尺寸
    4. 计算规则如下：
        - 如果没有CSS尺寸和HTML尺寸，则使用固有尺寸作为最终的宽高
        - 如果没CSS尺寸，就使用HTML尺寸作为最终的宽高
        - 如果有CSS尺寸，则最终尺寸由CSS属性决定
        - 如果“固有尺寸”含有固有的宽高比例，同时仅设置了宽度或仅设置了高度，则元素依然按照固有的宽高比例显示
        - 如果上面的条件都不符合，则最终宽度表现为300px，高度为150px，宽高比2：1（img标签除外）
        - 内联替换原宿和块级替换元素使用上面同一套尺寸计算规则

    - 当图片的src属性缺省的时候，图片不会有任何请求，是最高效的占位实现方式
    - CSS世界中的替换元素的固有尺寸有一个很重要的特性，就是“我们是无法改变这个替换元素内容的固有尺寸的”

4. 替换元素和非替换元素的距离有多远
    1. 替换元素和非替换元素之间只隔了一个src属性
    2. 替换元素和非替换元素之间只隔了一个CSS content属性
5. content与替换元素关系剖析
    1. 使用content生成的文本无法选中、无法复制
    2. 不能左右:emtey伪类
    3. content动态生成值无法获取

#### 4.1.2 content内容生成技术——::before/::after伪元素技术

1. content辅助元素生成
2. content字符内容生成
3. content图片生成
4. 了解content开启闭合符号生成
5. content attr属性值内容生成
6. 深入理解content计数器
    1. 属性counter-rest，作用是给计数器起个名字
    2. 属性counter-increment，就是计数器递增
        - 普照源唯一，每普照一次，普照源就增加一次计数值
        - 计数器的数值变化遵循HTML渲染顺序，遇到一个increment计数器就变化，什么时候counter输出就输出此时的计数值
        - counter-rest可以一次命名两个计数器，increment也可以，用空格隔开
        - 变化的值不一定是1，可以灵活设置
        - 值还可以为none或inherit
    3. 方法counter()/counters()
7. content内容生成的混合特性

### 4.2 温和的 padding 属性

#### 4.2.1 padding 与元素的尺寸

在设置box-sizing:border-box时，如果padding足够大，那么width也无能为力

内联元素的padding在垂直方向同样会影响布局，影响视觉表现。只是因为内联元素没有可视宽度和可视高度的说法，垂直方向的行为表现完全受line-height和vertical-align的影响，视觉上病没有改变和上一行下一行内容的间距，所以我们就感觉垂直padding没有起作用。

这样我们就可以在不影响当前布局的情况下，优雅地增加链接或按钮的点击区域的大小。

对于非替换元素的内联元素，不仅padding不会加入行盒高度的计算，margin和border也都是如此，都是不计算高度，但实际上在内联盒周围发生了渲染。

#### 4.2.2 padding 的百分比值

1. 和margin属性不同，padding属性不支持负值
2. padding支持百分比值，但是无论是水平方向还是垂直方向都是相对于宽度计算的
    - 对于内联元素
        1. 同样是基于宽度计算
        2. 默认的高度和宽度细节有差异
        3. padding会断行

#### 4.2.3 标签元素内置的 padding

1. ol/ul 列表内置 padding-left，但是单位是px不是em
2. 很多表单元素都内置padding
    - 所有浏览器input标签和textarea标签输入框内置 padding
    - 所有浏览器button标签按钮内置 padding
    - 部门浏览器select下拉内置 padding，如Firefox、IE8
    - 所有浏览器radio标签/checkbox标签按钮内置 padding
    - button按钮元素的 padding最难控制
        - 推荐一个既语义良好行为保留，同时UI效果棒兼容性好的实现小技巧，就是用label元素，label元素的for属性和button元素的id值对应即可

#### 4.2.4 padding 与图形绘制

### 4.3 激进的 margin 属性

#### 4.3.1 margin与元素尺寸以及相关布局

1. 元素尺寸的相关概念
    - 元素尺寸包括padding和border，也就是元素的border box尺寸，原生DOM API中是offsetWidth和offsetHeight
    - 元素内部尺寸包括padding，但不包括border，也就是元素的padding box尺寸，原生DOM API中是clientWidth和clientHeight
    - 元素外部尺寸包括padding、border和margin，也就是元素的margin box尺寸，没有对应的原生API
2. margin与元素的内部尺寸
    - 只有元素是“充分利用可用空间”的状态时，margin才可以改变元素的可视尺寸
    - 只要宽度设定，margin就无法改变元素尺寸
    - 只要元素的尺寸表现符合“充分利用可用空间”，无论是垂直方向还是水平方向，都可以通过margin改变尺寸
    - 对于普通流体元素，margin智能改变元素水平方向尺寸
    - 对于具有拉伸特性的绝对定位元素，则水平或垂直方向都可以
3. margin与元素的外部尺寸
    - 垂直方向margin无法改变元素的内部尺寸，但可以改变外部尺寸
    - margin对尺寸的影响都是针对具有块状特性的元素而言，对于纯内联元素不适用
    - 内联元素垂直方向的margin是没有任何影响的，既不会影响外部尺寸，也不会影响内部尺寸

#### 4.3.2 margin 的百分比值

margin的百分比值无论是水平方向还是垂直方向都是相对于宽度计算的

#### 4.3.3 正确看待CSS世界里的margin合并

1. 什么是margin合并
    - 块级元素的margin-top和margin-bottom有时会合并为单个外边距
    - 不包括浮动和定位元素
    - 只发生在垂直方向
2. margin合并的3种场景
    1. 相邻兄弟元素margin合并
    2. 父级和第一个/最后一个元素
        - 阻止margin-top合并
            1. 父元素设置为块状格式化上下文元素
            2. 父元素设置border-top值
            3. 父元素设置padding-top值
            4. 父元素和第一个子元素之间添加内联元素进行分隔
        - 阻止margin-bottom合并
            1. 父元素设置为块状格式化上下文元素
            2. 父元素设置border-bottom值
            3. 父元素设置padding-bottom值
            4. 父元素和最后一个子元素之间添加内联元素进行分隔
            5. 父元素设置height、min-height或max-height
    3. 空块级元素的margin合并
        - 阻止空元素的margin合并
            1. 设置垂直方向的border
            2. 设置垂直方向的padding
            3. 里面添加内联元素，直接键入空格是无用的
            4. 设置height或min-height
3. margin合并的计算规则
    1. 正正取大值
    2. 正负值相加
    3. 负负取负值
4. margin合并的意义
    1. 兄弟元素的margin合并是为了让图文信息的排版更加舒服自然
    2. 父子margin合并是为了在页面中任何地方嵌套或直接放入任何裸div元素，都不会影响原来的块状布局
    3. 自身margin合并是为了可以避免不小心遗落或者生成的空标签影响排版和布局

#### 4.3.4 深入理解CSS中的margin:auto

- margin:auto的填充规则如下：
    1. 如果一侧定值，一侧auto，则auto是剩余空间大小
    2. 如果两侧都为auto，则平分剩余空间
- 出发margin:auto有一个前提条件，就是width或height为auto时。元素是具有对应方向的自动填充特性的
- 由于绝对定位元素的格式化高度即使父元素height:auto也是支持的，因此，可以在绝对定位下使用margin:auto使块级元素垂直居中对齐
- 如果里面的元素尺寸比外面的大，auto该如何计算？
    1. 默认的水平流中，如果里面的元素大，水平方向auto计算后的负值会被当做0来处理，所以不会水平居中
    2. 垂直方向计算后的负值会保留，所以会垂直居中

#### 4.3.5 margin无效情形解析

1. display计算值inline的非替换元素的垂直margin是无效的
2. 表格中tr和td元素或者设置display计算值是table-cell或table-row的元素的margin都是无效的
    - 计算值是table-caption、table或inline-table则没有问题
    - ::first-letter伪元素也可以解析margin
3. margin合并的时候，更改margin值可能是没有效果的
4. 绝对定位元素非定位方位的margin值“无效”
    - 绝对定位元素的渲染是独立的，所以margin无法影响兄弟元素，所以看起来就像是无效的
5. 定高容器的子元素的margin-bottom或者宽度定死的子元素的margin-right的定位“失效”
6. 鞭长莫及导致的margin无效
7. 内联特性导致的margin无效

### 4.4 功勋卓著的 border 属性

#### 4.4.1 为什么border-width不支持百分比

border-width支持若干关键字：

- thin：等同于1px
- medium：默认，等同于3px
- thick：等同于4px

#### 4.4.2 了解各种border-style类型

1. border-style:none
    - 默认值
    - 重置边框样式时，可以一起写border: 0 none;这样写渲染性能最高
2. border-style:solid
3. border-style:dashed
4. border-style:double
    - double类型的最小边框宽度为3px，这时double才有效果
5. 其他border-style类型
    - inset、outset、groove、ridge风格老土过时，兼容性惨不忍睹

#### 4.4.3 border-color 和 color

1. border-color的默认颜色就是color
2. 其他类似特性的CSS属性还有outline、box-shadow和text-shadow等

#### 4.4.4 border 与透明边框效果

1. 右下方background定位的技巧
    - 默认background背景图片是相对于padding box定位的，所以，计算background-position:100%的位置时不会吧border-width计算在内
2. 优雅增加点击区域大小
3. 三角等图形绘制

#### 4.4.5 border 与图形构建

#### 4.4.6 border 等高布局技术

## 第5章 内联元素和流

### 5.1 字母 x —— CSS 世界中隐匿的举足轻重的角色

#### 5.1.1 字母 x 与 CSS 世界的基线

字母x的下边缘就是我们的基线

#### 5.1.2 字母 x 与 CSS 中的 x-height

x-height指的是小写字母x的高度，就是基线和等分线之间的距离。

middle指的是基线往上1/2 x-height的高度，可以近似理解为字母x交叉点的位置

#### 5.1.3 字母 x 与 CSS 中的 ex

ex 是 CSS 中的一个相对单位，指的是小写字母 x 的高度，就是x-height

ex的价值就是不受字体和字号影响的内联元素的垂直居中对齐效果

### 5.2 内联元素的基石 —— line-height

#### 5.2.1 内联元素的高度之本 —— line-height

div的高度是由行高决定的，而非文字。

对于非替换元素的纯内联元素，其可视高度完全由line-height决定。

行距 = line-height - font-size

理解了行间距后，就能设置line-height的大小根据设计稿获取准确的文字标注值。

半行距，文字上边距，向下取证，下边距，向上取证，例如line-height是1.5，font-size的大小为14px，半行距就是（14px * 2 -14px） / 2 = 3.5px。如果标注值为20px，那么margin-top就该设为17px，margin-bottom为16px

- line-height为2时，半行距是一半的文字大小，两行文字中的间隙为一个文字尺寸大小
- line-height为1时，半行距为0，两行文字紧密贴合在一起
- line-height为0.5时，半行距为负数，两行文字就重叠在一起

line-height 不会影响替换元素

对于块级元素，line-height对其本身是没有任何作用的

#### 5.2.2 为什么 line-height 可以让内联元素居中

1. 要让单行文字垂直居中，只设置line-height一个属性就可以了
2. line-height可以让多行或单行元素近似垂直居中
3. 多行文本或者替换元素的垂直居中实现原理和单行文本不一样，需要vertical-align属性才可以

#### 5.2.3 深入 line-height 的各类属性值

line-height 的默认值是 normal，还支持数值、百分比值和长度值

- 数值：最终的计算值是和当前font-size相乘后的值
- 百分比值：最终的计算值是和当前font-size相乘后的值
- 长度值：带单位的值，如果是em，还是和当前font-size相乘后的值
- 如果属性值为数值，则所有子元素继承的都是数值
- 如果是百分比值或长度值，那么子元素继承的是最终计算后的值

1. 如果是重图文内容显示的网站，一定要用数值作为单位，line-height值可以设为1.6~1.8
2. 如果是片中布局结构的网站，用长度或数值均可，长度值建议可设为20px

#### 5.2.4 内联元素 line-height 的“大值特性”

无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的那个 line-height 决定的

### 5.3 line-height 的好朋友 vertical-align

#### 5.3.1 vertical-align 家族基本认识

vertical-align 属性值分为以下4类：

1. 线类：如baseline（默认值）、top、middle、bottom
2. 文本类，如text-top、text-bottom
3. 上标下标类：如sub、super
4. 数值百分比类：如20px、2em、20%等
    - 应该分为数值类和百分比类

根据计算值的不同，相对于基线往上还是往下偏移，取决于vertical-align的计算值是正值还是负值，如果是负值，往下偏移，如果是正值，往上偏移

vertical-align的数值属性值在实际开发时实用性很强

- 兼容性很好
- 可以精确控制内联元素的垂直对齐位置

vertical-align 属性的百分比值是相对于line-height 的计算值计算的

#### 5.3.2 vertical-align 作用的前提

vertical-align 属性智能作用在display计算值为 inline、inline-block、inline-table或inline-cell的元素上。

浮动和绝对定位会让元素块状化，从而使vertical-align属性无效

table-cell元素设置vertical-align垂直对齐的是子元素，但是作用的并不是子元素，而是table-cell元素自身。

#### 5.3.3 vertical-align 和 line-height 之间的关系

font-size 越大字符的基线位置越靠下，因为文字默认全部都是基线对齐，所以当字号大小不一致的两个文字在一起的时候，彼此就会发生上下位移，如果位移距离足够大，就会超过行高的限制，而导致出现意料之外的高度

如何解决常见的图片底部留有间隙的问题

- 图片块状化
- 容器line-height足够小
- 容器font-size足够小，此方法要生效，需要容器的line-heigt和font-size相关
- 图片设置其他vertical-align属性

#### 5.3.4 深入理解vertical-align 线性类属性值

1. inline-block 与 baseline
    - 一个inline-block元素，如果里面没有内联元素，或者overflow不是visible，则该元素的基线就是其margin底边缘，否则其基线就是元素里面最后一行内联元素的基线
    - 改变“幽灵空白节点”的基线位置可以使用font-size，当字体足够小时，基线和中线会重合在一起
    - 20px图标对齐的处理办法
        1. 图标高度和当前行高都是20px
        2. 图标标签里面永远有字符
        3. 图标CSS不适用overflow:hidden 保证基线为链字符的基线，但是要让里面潜在的字符不可见
        4. 如果项目字号都是16px，那么图标规格和默认行号设为24px可能会更适合一些
2. 了解vertical-align:top/bottom
    1. vertical-align:top就是垂直上边缘对齐，具体定义如下
        - 内联元素：元素顶部和当前行框盒子的顶部对齐
        - table-cell元素：元素顶padding边缘和表格行的顶部对齐
    2. vertical-align:bottom的规则与top类似，就是把顶部换成底部，上边缘换成下边缘
3. vertical-align:middle 与近似垂直居中
    - 内联元素：元素的垂直中心点和行框盒子基线往上1/2 x-height 处对齐
    - table-cell元素：单元格填充盒子相对于外面的表格行居中对齐
    - 通常做法是设置font-size为0，整个字符X缩小为看不见的点，根据line-height的半行间距上下等分原则，这个点正好是整个容器的垂直中心位置，这样就可以实现真正意义上的垂直居中对齐了

#### 5.3.5 深入理解vertical-align文本类属性值

文本类属性值得就是text-top和text-bottom

- vertical-align:text-top —— 盒子的顶部和父级内容区域的顶部对齐
- vertical-align:text-bottom —— 盒子的地步和父级内容区域的底部对齐

#### 5.3.6 简单了解vertical-align上标下标类属性值

上标下标类属性值得就是sub和super

- vertical-align:super —— 提高盒子的基线到父级核实的上标基线位置
- vertical-align:sub —— 降低盒子的基线到父级核实的下标基线位置

#### 5.3.7 无处不在的 vertical-align 

top/bottom和baseline/middle，切着对齐看边缘看行框盒子，后者和字符x打交道。

#### 5.3.8 基于 vertical-align 属性的水平垂直居中弹框

1. 节省了很多JavaScript定位代码，也不需要浏览器resize事件处理，当弹框内容动态变化的时候，也无需重新定位
2. 性能更改、渲染更快
3. 可以很灵活的控制垂直居中的比例
4. 容易设置overflow:auto可以实现弹框高度超过一屏时依然能看见屏幕外的内容

## 第6章 流的破坏与保护

### 6.1 魔鬼属性 float

#### 6.1.1 float 的本质与特性

float的特性：

1. 包裹性
    - 包裹
    - 自适应
2. 块状化并格式化上下文
3. 破坏文档流
4. 没有任何margin合并

#### 6.1.2 float 的作用机制

float 属性让父元素高度坍塌的原因就是为了实现文字的环绕效果

行框盒子如何和浮动元素的垂直高度有重叠，则行框盒子在正常定位状态下只会跟随浮动元素，而不会发生重叠

#### 6.1.3 float 更深入的作用机制

- 浮动锚点是 float 元素所在的”流“中的一个点，这个点本身并不浮动，而是更像一个没有margin、padding、border的空的内联元素
- 浮动参考值得是浮动元素对齐参考的实体

#### 6.1.4 float 与流体布局

### 6.2 float 的天然克星 clear

#### 6.2.1 什么是 clear 属性

clear属性：元素盒子的边不能和前面的浮动元素相邻

- none：默认值，左右浮动来就来
- left：左侧抗浮动
- right：右侧抗浮动
- both：两侧抗浮动

#### 6.2.2 成事不足败事有余的 clear

clear 属性只有块级元素才有效果，而 ::after 等伪元素默认都是内联水哦宁，这就是借助伪元素清除浮动影响时需要设置 display 属性的原因

由于clear:both 的作用本质是让自己不和 float 元素在一行显示，并不是真正意义上的清除浮动，因此float元素的一些不好的特性依然存在，所以会有以下现象

1. 如果clear:both 元素前面的元素就是 float 元素，则 margin-top 负值即使设为-9999px，也没有任何效果
2. clear:both 后面的元素依旧会发生文字环绕的现象

### 6.3 CSS 世界的结界——BFC

#### 6.3.1 BFC 的定义

BFC是块级格式化上下文

如果一个元素具有BFC，则内部子元素无论如何都不会影响到外部元素。所以，BFC元素不可能发生margin重叠；BFC元素也可以用来清除浮动的影响。

什么时候会出发BFC？

1. html根元素
2. float的值不为none
3. overflow的值为auto、scroll、hidden
4. display的值为table-cell、table-caption、inline-block
5. position的值部位relative或static

#### 6.3.2 BFC 与浮动布局

普通流体元素设置overflow:hidden 后，会自动填满容器中除浮动元素以外的剩余空间，形成自适应布局的效果

基于BFC的浮动布局有以下优点：

1. 自适应内容由于封闭而更健壮，容错性更强
2. 自适应内容自动填满浮动以外区域，无须关心浮动元素宽度，可以整站大规模应用

### 6.4 最佳结界 overflow

想彻底清除浮动的影响，最适合的属性不是clear 而是 overflow，一般使用 overflow:hidden，利用BFC的“结界”特性彻底解决浮动对外部或兄弟元素的影响。

#### 6.4.1 overflow 剪裁界线 border box

当子元素内容超出容器宽度限制的时候，剪裁的边界是 border box 的内边缘，而非 padding box 的内边缘。

如果想实现元素剪裁同时四周留有间隙的效果，可以试试透明边框，此时内间距padding 属性是无能为力的

Chrome 浏览器下，如果容易可滚动，则padding-bottom 也算在滚动尺寸之内，IE和Firefox浏览器忽略padding-bottom

#### 6.4.2 了解 overflow-x 和overflow-y

支持的属性值和overflow一样

- visible：默认值
- hidden：剪裁
- scroll：滚动条区域一直存在
- auto：不足以滚动时没有滚动条，可以滚动时滚动条出现

除非overflow-x 和overflow-y 的属性值都是visible，否则visible会当成auto来解析

#### 6.4.3 overflow 与滚动条

1. 在PC端，无论什么浏览器，默认滚动条均来自于html，而不是body标签
    - PC端获取窗体滚动高度 document.documentElement.scrollTop
    - 移动端 document.body.scrollTop
2. 滚动条会占用容器的可用宽度或高度
    - IE7以上版本，Chrome、Firefox浏览器滚动栏所占据的宽度均是17px

#### 6.4.4 依赖 overflow 的样式表现

#### 6.4.5 overflow 与锚点定位

1. 锚点定位行为的触发条件
    1. URL地址中的锚链与锚点元素对应并有交互行为
    2. 可focus的锚点元素处于focus状态
2. 锚点定位作用的本质
    - 是通过改变容器滚动高度或宽度来实现的
    - 普通元素和窗体可同时滚动时，会由内而外触发所有可滚动窗体的锚点行为定位
    - 元素设置了overflow:hidden声明，里面内容高度溢出的时候，滚动依然存在，仅仅滚动条不存在
    - 基于父元素scrollTop 值来实现自定义滚动条效果
        1. 实现简单，边界无须判断
        2. 可与原生的scroll事件天然集成、无缝对接
        3. 无须改变子元素的结构
        4. 缺点：
            1. 无法添加类似Bounce回弹动效
            2. 渲染要比一般的渲染慢

### 6.5 float 的兄弟 position:absolute

当 absolute 和 float 同时存在的时候，float 属性是无任何效果的

元素一旦position属性为 absolute 或 fixed，其 display 计算值就是bloack或table

#### 6.5.1 absolute 的包含块

普通元素的百分比宽度是相对于父元素的 content box 宽度计算的，而绝对定位元素的宽度宽度是相对于第一个 position 不为 static 的祖先元素计算的

1. 根元素被称为初始包含块（很多情况是html根元素），其尺寸等于浏览器可视窗口的大小
2. 对于其他元素， 如果该元素的 position 是 relative 或者 statci，则包含块由其最近的块容器祖先盒的 content box 边界形成
3. 如果元素 position:fixed，则包含块是初始包含块
4. 如果元素 position:absolute，则包含块由最近的 position 不为static的祖先元素建立
    - 如果该祖先元素是纯inline元素，则规则略复杂
        - 假设给内联元素的前后各生成一个宽度为0的内联盒子，则这两个内联盒子的padding box 外面的包围盒就是内联元素的包含块
        - 如果该内联元素被跨行分割了，那么包含块是未定义的，也就是CSS2.1规范并没有明确定义，由浏览器自行发挥
    - 否则，包含块由该祖先的padding box边界形成

如果没有符合条件的祖先元素，则包含块是初始包含块

和常规元素相比，absolute 绝对定位元素的包含块有以下3个明显差异

1. 内联元素也可以作为包含块所在的元素
    1. absolute一般都是用来布局，而内联元素主要用来图文展示
    2. 理解和学习的成本比较高
        - 内联元素的包含块可以受::first-line伪元素影响，但不受::first-letter影响
        - 内联元素的包含块范围比较稳固，不会受line-height等属性影响
    3. 兼容性问题
        - Firefox浏览器的包含块仅覆盖第一行，而IE和Chrome浏览器包含块由第一行开头和最后一行结束的内联盒子共同决定
2. 包含块所在的元素不是父块级元素，而是最近position不为static的祖先元素或根元素
    - height:100%和height:inherit的区别
        - 对于普通元素，两者没什么区别
        - 对于绝对定位元素，height:100%是第一个具有定位属性值得祖先元素的高度，而height:inherit则是单纯的父元素的高度继承
3. 边界是padding box而不是content box

#### 6.5.2 具有相对特性的无依赖 absolute 绝对定位

absolute 是非常独立的CSS属性值，其样式和行为表现不依赖其他任何CSS属性就可以完成

1. 各类图标定位
2. 超越常规布局的排版
3. 下拉列表的定位
4. 占位符效果模拟
5. 进一步深入“无依赖绝对定位”
    - 虽然说元素position:absolute 后的display计算值都是块状的，但是其定位的位置和没有设置position:absolute 时候的位置相关

#### 6.5.3 absolute 与 text-align

text-align可以改变absolute元素的位置

具体的渲染原理如下：

1. 由于img是内联水平，p标签中存在一个宽度为0，看不见摸不着的幽灵空白节点，也是内联水平，于是受text-align:center影响而水平居中显示
2. img设置了position:absolute，表现为无依赖绝对定位，因此在幽灵空白节点后面定位显示，同时由于图片不占据空间，这里的幽灵空白节点正好在p元素水平中心位置显示，于是我们就看到图片从p元素水平中间位置显示的效果
