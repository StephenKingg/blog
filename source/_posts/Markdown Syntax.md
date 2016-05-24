# A Guide to Markdown Syntax

### 1. 标题
"#"之后最好加个空格

    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

### 2. 加粗，斜体

    *斜体*
    _斜体_
*斜体*
_斜体_

    **加粗**
    __加粗__
**加粗**
__加粗__

    ***粗斜体***
    ___粗斜体___
***粗斜体***
___粗斜体___

### 3. 代码

#### 3. 1 部分代码

    我是`function_name()`部分代码

我是`function_name()`部分代码

#### 3. 2 代码片段

    ```javascript
    $(document).ready(function () {
        alert("Hello, world!");
    });
    ```

```javascript
$(document).ready(function () {
    alert("Hello, world!");
});
```

支持的语言：`actionscript, apache, bash, clojure, cmake, coffeescript, cpp, cs, css, d, delphi, django, erlang, go, haskell, html, http, ini, java, javascript, json, lisp, lua, markdown, matlab, nginx, objectivec, perl, php, python, r, ruby, scala, smalltalk, sql, tex, vbscript, xml`

也可以使用4空格缩进，效果相同

        $(document).ready(function () {
            alert("Hello, world!");
        });

### 4. 列表

#### 4. 1 无序列表

    - item1
    + item2
    * item3

- item1
+ item2
* item3

#### 4. 2 有序列表

    1. item1
    2. 自动添加数字
    5. 自动纠正

1. item1
2. 自动添加数字
5. 自动纠正

#### 4. 3 列表嵌套

    1. 列出所有元素：
        - 无序列表元素 A
            1. 元素 A 的有序子列表
        - 前面加四个空格
    2. 列表里的多段换行：
        前面必须加四个空格，
        这样换行，整体的格式不会乱
    3. 列表里引用：

        > 前面空一行
        > 仍然需要在 >  前面加四个空格

    4. 列表里代码段：

        ```
        前面四个空格，之后按代码语法 ``` 书写
        ```

            或者直接空八个，引入代码块

1. 列出所有元素：
    - 无序列表元素 A
        1. 元素 A 的有序子列表
    - 前面加四个空格
2. 列表里的多段换行：
    前面必须加四个空格，
    这样换行，整体的格式不会乱
3. 列表里引用：

    > 前面空一行
    > 仍然需要在 >  前面加四个空格

4. 列表里代码段：

    ```
    前面四个空格，之后按代码语法 ``` 书写
    ```

        或者直接空八个，引入代码块

### 5. 链接

#### 5. 1 Inline-style

    文字链接： [名称](网址)
    网址链接： <网址>

我是[百度](https://www.baidu.com)
我是<https://www.baidu.com>

#### 5. 2 Reference-style

    常用的搜索引擎有[Google][123]，[百度][baidu]，[必应][aaa]等。

      [123]: https://www.google.com/
      [baidu]: https://www.baidu.com/
      [aaa]: https://www.bing.com/

常用的搜索引擎有[Google][123]，[百度][baidu]，[必应][aaa]等。

  [123]: https://www.google.com/
  [baidu]: https://www.baidu.com/
  [aaa]: https://www.bing.com/

#### 5. 3 title属性

    [Google](https://www.google.com/ "Google大发好")
    或者这样写：
    [Google][hover]

      [hover]: https://www.google.com/ "Google大发好"

[Google](https://www.google.com/ "Google大发好")
或者这样写：
[Google][hover]

  [hover]: https://www.google.com/ "Google大发好"

### 6. 图片

#### 6. 1 普通方式

    ![google](https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)

![google](https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)

#### 6. 2 使用网址变量

    ![pic][1]

      [1]: https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png

![pic][1]

  [1]: https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png

#### 6. 3 使用HTML语法，能自定义图片宽高

    <img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" width="75px" height="75px">

<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" width="150px" height="75px">

#### 6. 4 点击图片并跳转

    [![google][pic]][url]

      [pic]: https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png
      [url]: https://www.google.com/

[![google][pic]][url]

  [pic]: https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png
  [url]: https://www.google.com/

### 7. 引用

#### 7. 1 普通引用

    > 引用文本
    > 自动换行可以不加，新的一行要加上">"

> 引用文本
> 自动换行可以不加，新的一行要加上">"

#### 7. 2 引用里嵌套引用

    > 最外层引用
    > > 多一个> 嵌套一层引用
    > > > 可以嵌套很多层

> 最外层引用
> > 多一个> 嵌套一层引用
> > > 可以嵌套很多层

#### 7. 3 引用里嵌套列表

    > - 引用里嵌套一个列表

> - 引用里嵌套一个列表

    > - 引用里嵌套子列表
    >       - 子列表需要从"- "之后延后四个空格

> - 引用里嵌套子列表
>       - 子列表需要从"- "之后延后四个空格

#### 7. 4 引用里嵌套代码块

    >     多加四个空格

>     多加四个空格

    > ```
    > 使用```形成代码块
    > ```

> ```
> 使用```形成代码块
> ```

### 8. 换行

    如果另起一行，只需在当前行末尾加2个空格  
    这是新的一行

如果另起一行，只需在当前行末尾加2个空格  
这是新的一行

如果添加新的段落，只需空出一行即可。

### 9. 分隔符

    "---" "***" "___"的上下最好各空一行，three or more

    前面的段落

    ***

    ---

    ___

    后面的段落

前面的段落

***

---

___

后面的段落

### 10. 行内HTML元素

支持部分HTML行内元素，包括`<kbd>, <b>, <i>, <em>, <sup>, <sub>, <br>`等。

#### 10. 1 键位显示：

    <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

#### 10. 2 代码块：

    使用<pre></pre>元素同样可以形成代码块

使用<pre></pre>元素同样可以形成代码块

#### 10. 3 粗斜体：

    <<b>Markdown在此处同样适用，如*斜体*</b>

<b>Markdown在此处同样适用，如*斜体*</b>

### 11. 符号转义

如果你的描述中需要用到markdown的符号，比如`_` `#` `*`等，可以在这些符号前加反斜杠，如`\_` `\#` `\*`。

    \_这里的文本不想变为斜体\_
    \*\*这里的文本不想被加粗\*\*

\_这里的文本不想变为斜体\_
\*\*这里的文本不想被加粗\*\*

### 12. 添加视频

#### 12. 1 使用HTML语法

    <a href="video-url" target="_blank"><img src="image-url" alt="this is an image" width="200" height="200"></a>

<a href="video-url" target="_blank"><img src="image-url" alt="this is an image" width="200" height="200"></a>

#### 12. 2 使用markdown

    [![video here](image-url)](video-url)

[![video here](image-url)](video-url)

### 13. Tables

Tables aren't part of the core Markdown spec, but they are part of GFM and *Markdown Here* supports them. They are an easy way of adding tables to your email -- a task that would otherwise require copy-pasting from another application.

```
Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the 
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```

Colons can be used to align columns.

| Tables        | Are           | Cool |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell. The outer pipes (|) are optional, and you don't need to make the raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
