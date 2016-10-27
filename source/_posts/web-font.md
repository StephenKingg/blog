---
title: 网页设计中的字体设定
date: 2016-10-27 14:00:00
tags: [font-family, web font]
---
引言：不同的平台（Windows、Mac OS、Linux、Android、iOS）预装的字体各不相同，浏览器默认显示的字体效果也不尽相同。使用CSS的`font-family`属性可以指定相应的字体，以便在网页设计中达到较好的字体显示效果。
<!--more-->
## 1. font-family

首先通过一个例子来认识一下CSS的`font-family`属性：

```css
body {
  font-family: Helvetica, Arial, "Microsoft YaHei", sans-serif;
}
```

其中，`Helvetica`和`Arial`是西文字体，`Microsoft YaHei`既包括中文字体又包括西文字体，`sans-serif`是无衬线体。优先指定西文字体，否则像`Microsoft YaHei`这样既包含中文又包含西文的字体，会覆盖后面指定的西文字体。确保在`font-family list`的最后加上`generic family name`（比如`serif`，`sans-serif`，`monospace`，`cursive`，`fantasy`），以防止前面指定的所有字体在计算机中都不存在时没有字体可以显示的情况发生。关于`font-family`的详情，请参见[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family)。

关于`font-family`的书写：字体名称中如果包含空格，则必须用引号包含，上面提到的`generic family names`是关键字，不能使用引号包含。我个人习惯使用双引号，且只使用中文字体的英文名称（部分开发设计者中英文名称都写进`font-family list`里），关于字体的名称，可以在图中红方框的位置看到：![link](https://ooo.0o0.ooo/2016/10/10/57faed504dc39.png)

## 2. 平台字体简介

### 2. 1 Windows

* `宋体（SimSun）`：Windows下大部分浏览器的默认中文字体，小字号的`宋体`（如`12px`、`14px`）显示结果还可以接受，但是大字号非常差。
* `微软雅黑（Microsoft YaHei）`：从 Vista 开始，微软提供了这款新的无衬线黑体类字体，并且拥有Regular、Bold两种粗细的字重，显著提高了字体的显示效果。现在这款字体已经成为Windows浏览器中最值得使用的中文字体。从Win8开始，`微软雅黑`又加入了Light这款更细的字重，对于喜欢细字体的开发设计者又多了一个新的选择。
* `Arial`：Windows平台上默认的无衬线西文字体，有多种变体，显示效果一般。
* `Tahoma`：十分常见的无衬线字体，被Windows 2000、Windows XP、Windows Server 2003及Sega游戏主机Dreamcast等系统采用为预设字型，显示效果比Arial要好。
* 其他预装字体请参见[Microsoft](https://www.microsoft.com/typography/fonts/product.aspx?pid=161)、[Wikipedia](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_Microsoft_Windows)。

### 2. 2 Mac OS

* `华文黑体（STHeiti）`、`华文细黑（STXihei）`：属于同一字体族，OS X 10.6 之前的简体中文系统界面默认字体，有Regular和Bold两个字重，显示效果可以接受。
* `黑体-简（Heiti SC）`：从OS X 10.6开始，`Heiti SC`替代`STHeiti`作为简体中文系统界面默认字体，iPhone、iPad等设备用的也是这款字体，显示效果不错，但是喇叭口设计遭人诟病。
* `冬青黑体（Hiragino Sans GB）`：是日文字体`Hiragino KakuGothic`的简体中文版，简体中文有Regular和Bold两种，冬青黑体是一款清新的专业印刷字体，小字号时足够清晰，被很多人的追捧。
* `Source Han Sans`：即`思源黑体`，由Google和Adobe合作开发，字体族有七个字重，集设计素质、完整字数（对国内使用环境特别重要）和泛用性于一身，是竞争力十分强的一套新设计。
* `Times New Roman`：Safari浏览器的默认字体，是最常见且广为人知的西文衬线字体之一，众多网页浏览器和文字处理软件都是用它作为默认字体。
* `Helvetica`、`Helvetica Neue`：苹果生态中最常用的西文字体。`Helvetica Neue`为`Helvetica`的改善版本，增加了更多不同粗细与宽度的字形，共拥有51种字体版本，极大的满足了日常的使用。
* `苹方（PingFang SC）`：在OS X El Capitan上，苹果为中国用户打造了一款全新中文字体--苹方，去掉了为人诟病的喇叭口，整体造型看上去更加简洁。
* `San Francisco`：同样是OS X El Capitan上最新发布的西文字体，和Helvetica看上去差别不大，目前已经应用在Mac OS 10.11+、iOS 9.0+、watch OS等最新系统上。
* 其他字体请参见[Apple](https://support.apple.com/en-us/HT202408)、[Wikipedia](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_macOS)。

### 2. 3 Android

原生Android下中西文字体都选择默认的无衬线字体：

* 原生Android4.0之前：西文字体采用`Droid Sans`，中文字体采用`Droid Sans Fallback`。关于`Droid Sans`字体族，[知乎](https://www.zhihu.com/question/19946495)里有个很不错的回答。
* 原生Android4.0之后：采用`Roboto`，下面是Google官方的`Roboto`介绍：

> Google’s signature family of fonts, the default font on Android and Chrome OS, and the recommended font for Google’s visual language, Material Design.

### 2. 4 iOS

iOS系统的字体和Mac OS系统的字体相同，保证了Mac上的字体效果，iOS设备就没有太大问题。

* 西文字体：iOS 4.0之后使用`Helvetica Neue`，4.0之前使用`Helvetica`。


### 2. 5 Linux

* `文泉驿微米黑（WenQuanYi Micro Hei）`：Linux社区现有的最佳简体中文字体

## 3 注意事项

* IE font-family fallback bug：在较低版本的IE中（如IE8），只要font-family中某个字体存在，就会完全无视在它之后的字体，缺字用默认字体显示（也就是宋体），请各位注意这一点。

## 4 实际使用

我自己用的`font-family list`（针对西文和简体中文）如下：

`font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Source Han Sans SC", "Source Han Sans CN", "WenQuanYi Micro Hei", Roboto, "Heiti SC", "Microsoft YaHei", "Microsoft JhengHei", sans-serif;`
