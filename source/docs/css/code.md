title: 代码规范
---

## 编码规范

CSS样式表是一个序列通用字符集，传输和存储过程中，这些字符必须由支持 US-ASCII（例如 UTF-8, ISO 8859-x, SHIFT JIS 等）字符编码方式编译

### 文档内嵌样式表编码

> When a style sheet is embedded in another document, such as in the STYLE element or "style" attribute of HTML, the style sheet shares the character encoding of the whole document.

当样式出现在其它文档，如 HTML 的 STYLE 标签或标签属性 "style"，样式的编码由文档的决定。

### 文档外链样式表编码

> When a style sheet resides in a separate file, user agents must observe the following priorities when determining a style sheet's character encoding (from highest priority to lowest):

> 1. An HTTP "charset" parameter in a "Content-Type" field (or similar parameters in other protocols)
> 2. BOM and/or @charset
> 3. <link charset=""> or other metadata from the linking mechanism (if any)
> 4. charset of referring style sheet or document (if any)
> 5. Assume UTF-8

文档外链样式表的编码可以由以下各项按照由高到低的优先级顺序决定：

1. HTTP “Content-Type” 字段参数 “charset”（或其它协议相似的参数）
2. BOM（byte-order mark）和（或）@charset
3. Link 中的元数据设置（如果有的话）
4. 引用样式表字符集或文档编码（如果有的话）
5. 假定为 UTF-8 编码

### 样式表编码

> Authors using an @charset rule must place the rule at the very beginning of the style sheet, preceded by no characters. (If a byte order mark is appropriate for the encoding used, it may precede the @charset rule.)

> @charset must be written literally, i.e., the 10 characters '@charset "' (lowercase, no backslash escapes), followed by the encoding name, followed by '";'.


* @charset规则一定要在样式文件的第一行首个字符位置开始，否则的话就会有机会让 BOM 设置生效（如果有设置 BOM 的话）而优于 @charset 作为样式表的编码
* `@charset "";` 一定要写上，并且用小写字母，不能出现转义符

### 团队约定

* 样式文件必须写上 @charset 规则，并且一定要在样式文件的第一行首个字符位置开始写，编码名用 “UTF-8”
* 字符 @charset ""; 都用小写字母，不能出现转义符，编码名允许大小混写
* 考虑到在使用“UTF-8”编码情况下 BOM 对代码的污染和编码显示的问题，在可控范围下，坚决不使用 BOM。（更多关于 BOM 可参考 [BOM的介绍](https://zh.wikipedia.org/wiki/%E4%BD%8D%E5%85%83%E7%B5%84%E9%A0%86%E5%BA%8F%E8%A8%98%E8%99%9F) 和 [「带 BOM 的 UTF-8」和「无 BOM 的 UTF-8」有什么区别？](http://www.zhihu.com/question/20167122) ）


```css
/* 推荐 */

@charset "UTF-8";

.demo{}

/* 不推荐 */
/**
 * @desc File Info
 * @author Author Name
 * @date 2015-10-10
 */

/* @charset规则不在文件首行首个字符开始 */
@charset "UTF-8";

.demo{}
```

```css
@CHARSET "UTF-8";
/* @charset规则没有用小写 */

.demo{}
```

```css
/* 无@charset规则 */
.demo{}
```

更多关于样式编码：[CSS style sheet representation](http://www.w3.org/TR/2011/REC-CSS2-20110607/syndata.html#charset)

## 代码风格

### 代码格式化

样式书写一般有两种：一种是紧凑格式 (Compact)

```css
.list{ display: block;width: 50px;}
```

一种是展开格式（Expanded）

```css
.list{
  display: block;
  width: 50px;
}
```

**团队约定**

统一使用展开格式书写样式



### 代码大小写

样式选择器，属性名，属性值关键字全部使用小写字母书写，属性字符串允许使用大小写。

```css
/* 推荐 */
.demo{
  display:block;
}

/* 不推荐 */
.demo{
  DISPLAY:BLOCK;
}
```

### 选择器

* 尽量少用通用选择器 `*`
* 不使用 ID 选择器
* 不使用无具体语义定义的标签选择器

```css
/* 推荐 */
.user-info {}
.user-info li {}
.user-info li p{}

/* 不推荐 */
*{}
#user-info {}
.user-info div{}
```

* 组选择器分行处理

```css
/* 推荐 */
a:focus,
a:active {
  position: relative;
  top: 1px;
}

/* 不推荐 */
a:focus, a:active {
  position: relative;
  top: 1px;
}
```

* `>`、`+`、`~` 选择器的两边各保留一个空格。

```css
/* 推荐 */
main > nav {
    padding: 10px;
}
/* 不推荐 */
main>nav {
    padding: 10px;
}
```

 *  属性选择器中的值必须用双引号包围。

```css
/* 推荐 */
article[character="juliet"] {
  voice-family: "Vivien Leigh", victoria, female
}
/* 不推荐 */
 article[character='juliet'] {
   voice-family: "Vivien Leigh", victoria, female
 }
 ```

* 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。

由于CSS选择器是**从右到左**进行规则匹配的, 如果选择器的嵌套层级过多, 则浏览器会从右到左,逐级遍历页面元素,从而导致浏览器匹配选择器和文档元素时所消耗的时间过长。

```css
/* 推荐 */
#username input {}
.comment .avatar {}

/* 不推荐 */

/* 浏览器会寻找所有的div盒子,然后分别向上寻找li元素 以此类推, 直到找到完全符合的元素 */
.nav ul.list li div{}
/* 浏览器匹配页面中所有的元素后分别向上逐级匹配class为comment的元素，继而向上寻找div盒子,直到页面的根节点， */
div .comment * {}
```

### 代码缩进

统一使用两个空格进行代码缩进，使得各编辑器表现一致（各编辑器有相关配置）

```css
.user-info {
  width: 100%;
  height: 100%;
}
```

### 分号

每个属性声明末尾都要加分号；

```css
.user-info {
  width: 100%;
  height: 100%;
}
```

### 空格

* 选择器与`{` 之间 必须有空格
```css
.selector {}
```

* 属性名 与之后的 : 之间不允许包含空格， : 与 属性值 之间必须包含空格。
```css
margin: 0;
```

* 列表型属性值 书写在单行时, `,` 后必须跟一个空格。
```css
font-family: Arial, sans-serif;
```


### 代码易读性

* 左括号与类名之间一个空格，冒号与属性值之间一个空格


```css
/* 推荐 */
.demo {
  width: 100%;
}

/* 不推荐 */
.demo{
  width:100%;
}
```


* 逗号分隔的取值，逗号之后一个空格


```css
/* 推荐 */
.box {
  box-shadow: 1px 1px 1px #333, 2px 2px 2px #ccc;
}

/* 不推荐 */
.box {
  box-shadow: 1px 1px 1px #333,2px 2px 2px #ccc;
}
```

* 为单个css选择器或新声明开启新行



```css
/* 推荐 */
.user,
.user-logo,
.user-info {
  color: #ff0;
}
.nav{
  color: #fff;
}

/* 不推荐 */
.user, .user-logo, .user-info {
  color: #ff0;
}.nav{
  color: #fff;
}
```

* 颜色值 `rgb()` `rgba()` `hsl()` `hsla()` `rect()` 中不需有空格，且取值不要带有不必要的 0


```css
/* 推荐 */
.user-info {
  color: rgba(255,255,255,.5);
}

/* 不推荐 */
.user-info {
  color: rgba( 255, 255, 255, 0.5 );
}
```

* 属性值十六进制数值能用简写的尽量用简写

```css
/* 推荐 */
.user-info {
  color: #fff;
}

/* 不推荐 */
.user-info {
  color: #ffffff;
}
```

*  可以缩写的属性 要尽量的利用起来

```css
/* 推荐 */
.box {
  padding: 0 1em 2em;
}

/* 不推荐 */
.box {
  padding-bottom: 2em;
  padding-left: 1em;
  padding-right: 1em;
  padding-top: 0;
}
```

* 不要为 `0` 指明单位

```css
/* 推荐 */
.box {
  margin: 0 10px;
}

/* 不推荐 */
.box {
  margin: 0px 10px;
}
```

### !important

尽量不使用`!important`声明
仅在设计上 确实不允许任何其它场景覆盖样式时，才使用内联的 !important 样式。

### 属性值引号

css属性值需要用到引号时，统一使用单引号

```css
/* 推荐 */
.user-info {
  font-family: 'Hiragino Sans GB';
}

/* 不推荐 */
.user-info {
  font-family: "Hiragino Sans GB";
}
```

### 属性书写顺序

建议遵循以下顺序：

1. 布局定位属性：display / position / float / clear  / visibility / overflow
2. 自身属性：width / height / margin / padding / border / background
3. 文本属性：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. 其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient ...

```css
.user {
  display: block;
  position: relative;
  float: left;
  width: 100px;
  height: 100px;
  margin: 0 10px;
  padding: 20px 0;
  font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
  color: #333;
  background: rgba(0,0,0,.5);
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -o-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```


[mozilla官方属性顺序推荐](https://www.mozilla.org/css/base/content.css)

### CSS3浏览器私有前缀写法

CSS3 浏览器私有前缀在前，标准前缀在后

```css
.user {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -o-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```
更多关于浏览器私有前辍写法：[#Vendor-specific extensions](http://www.w3.org/TR/2011/REC-CSS2-20110607/syndata.html#vendor-keywords)
