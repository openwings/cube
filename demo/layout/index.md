---
layout: default
---

## Layout

布局是网站最核心的内容组织方式，Cube 提供了一系列灵巧的布局方案（兼容 IE6+ 等主流浏览器），如下将一一介绍，当然只需要引入 Cube 样式：

{% include cubeUsage.html %}

### inline-block 组件

让元素以 inline-block 呈现在文档流中，加上 `dib` 的 class 即可：

```html
<span class="dib span3">他出一對雞，我出一個鵝，閑快活。。</span>
<div class="dib span7">南畝耕，東山臥，世態人情經歷多。閑將往事思量過。賢的是他，愚的是我，爭什麽。</div>
```

将输出：

<span class="dib span3">他出一對雞，我出一個鵝，閑快活。。</span>
<div class="dib span7">南畝耕，東山臥，世態人情經歷多。閑將往事思量過。賢的是他，愚的是我，爭什麽。</div>

提到 inline-block 就让人想到浮动与浮动清除，当我们想以 inline-block 来替代浮动时，又会头疼空隙问题， 幸运的是，Cube 帮你
做到了这些，只需要在上面的 `dib` 的元素外套一层 `dib-box` 即可：

```html
<div class="dib-box">
  <div class="dib span3">Hey, I became inline block now.</div>
  <p class="dib span3">Hey, I became inline block now.</p>
</div>
```

将输出：<div class="dib-box">
  <div class="dib">Hey, I became inline block now.</div>
  <p class="dib">Hey, I became inline block now.</p>
</div>

注意，这里 dib-box 内部的 dib 的 font-size 会被重置为 12px，在使用过程中可以从内部继承和覆盖成为你需要的。

### 自适应两端对齐组件

该组件依赖于上面的 inline-block 方案，使用时外层加上 justify，内部需要两端对齐的元素都加上 dib, dib 与 justify 不要同时出现：

```html
<div class="justify">
    <span class="dib">用</span><span class="dib">户</span><span class="dib">名</span>
</div>
```

将输出：

<div class="justify">
    <span class="dib">用</span><span class="dib">户</span><span class="dib">名</span>
</div>

更多示例，[请移步](http://jsbin.com/OsEcOMA/1)

### CSS 三角形组件

Cube 提供了丰富的三角形效果, 如：

- 上三角: arrow-top
- 下三角: arrow-bottom
- 左三角: arrow-left
- 右三角: arrow-right
- 左上角: arrow-left-top
- 右上角: arrow-right-top
- 左下角: arrow-left-bottom
- 右下角: arrow-right-bottom

```html
<div class="justify box-num">
  <span class="dib">
    <span class="arrow arrow-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-bottom"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left-bottom"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right-bottom"></span>
  </span>
</div>
```

将输出：<div class="justify box-num">
  <span class="dib">
    <span class="arrow arrow-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-bottom"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right-top"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-left-bottom"></span>
  </span>
  <span class="dib">
    <span class="arrow arrow-right-bottom"></span>
  </span>
</div>

### 替换元素等比缩放组件

主要用于视频网站，不同的视频网站由于控制栏高度不同，需要 JS 配合添加对应的 class。

常见的视频比例有：

- 宽屏 16:9 = 56.25%
- 窄屏 4:3 = 75%

使用方案：

```html
<div class="fluid-media">
  <embed class="widescreen" src="" type="">
</div>

<div class="fluid-media">
  <embed class="narrowscreen" src="" type="">
</div>

注意，这里的 .fluid-media 元素是 relative，所以实际使用中需要对齐写高度。

```
截至目前，Cube 统计了如下网站的控制栏高度：

- 优酷
- 我乐 56.com
- 土豆
- 爱奇艺
- Youtube


```html
<div class="fluid-media">
  <embed class="youku" src="" type="">
</div>

<div class="fluid-media">
  <embed class="wole" src="" type="">
</div>

<div class="fluid-media">
  <embed class="tudou" src="" type="">
</div>

<div class="fluid-media">
  <embed class="iqiyi" src="" type="">
</div>

<div class="fluid-media">
  <embed class="youtube" src="" type="">
</div>
```
将输出：

<div class="fluid-media" style="height: 350px;">
  <embed class="youku" src="http://player.youku.com/player.php/sid/XNTg0NjI4MDMy/v.swf" allowfullscreen="true" quality="high" width="680" height="425" align="middle" allowscriptaccess="always" type="application/x-shockwave-flash">
</div>

<div class="fluid-media">
  <embed class="wole" src="" type="">
</div>

<div class="fluid-media">
  <embed class="tudou" src="" type="">
</div>

<div class="fluid-media">
  <embed class="iqiyi" src="" type="">
</div>

<div class="fluid-media">
  <embed class="youtube" src="" type="">
</div>

### 未知高度垂直居中组件

网站中，尤其图片类型网站，图片垂直居中是常见的场景，Cube 给出了一套兼容性良好的图片垂直居中方案，该方案同时支持单行、多行文字，以及图文混排：

```html
<div class="center-box">
  <b class="center-hack"></b>
  <div class="center-content">
    <div class="center-img">
      <img width="100%" src="http://cyj.me/assets/img/2013-new-york/IMG_0770.jpg" alt="自由女神像,来自 cyj.me">
    </div>
    <p>适意行，安心坐，渴时饮饥时餐醉时歌，困来时就向莎茵卧。日月长，天地阔，闲快活！。</p>
  </div>
</div>
```
将输出：

<div class="center-box" style="border:1px solid #ccc;">
  <b class="center-hack"></b>
  <div class="center-body">
    <div class="center-img">
      <img src="http://cyj.me/assets/img/2013-new-york/IMG_0770.jpg" alt="自由女神像,来自 cyj.me" width="680" height="453">
    </div>
    <p>适意行，安心坐，渴时饮饥时餐醉时歌，困来时就向莎茵卧。日月长，天地阔，闲快活！。</p>
  </div>
</div>


（栅格、常用布局解决方案、如何 Mobile First 等）
