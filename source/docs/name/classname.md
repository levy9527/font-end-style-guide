title: ClassName命名
---

ClassName的命名应该尽量精短、明确，必须以**字母开头命名**，且**全部字母为小写**，单词之间**统一使用中划线** “-” 连接

### 命名原则
现在前端开发团队使用的是命名原则是 在页面代码的根元素加上 `class=${pageName}`
并且在后续的css代码中, 该页面的类选择器都放在.pageName中

```vue
// my-page.vue
<template>
  <div class="my-page">
    <div class="list"></div>
    <button class='submit-btn'></button>
  </div>
</template>
```

```css
<style>
  .my-page {
    .list {}
    .submit-btn {}
  }
</style>
```

在这样的命名规则实施一段时间后,就发现了可能存在样式全局污染的问题。

当时问题是这样的: 当个别元素的样式 没有包裹在页面样式里面。
如:
``` vue
<style>
  .my-page {
    .list {}
  }
  .submit-btn {}
</style>
```

那么 .submit-btn这个样式就会暴露到全局，当其他页面也有.submit-btn这个样式的时候,那么原页面的submit-btn的样式就会被覆盖。

于是,团队也会使用scoped来避免样式全局污染的问题。

 当 `<style>`标签有 scoped 属性时，它的 CSS 只作用于当前组件中的元素。

当我们在页面的 `<style>`标签加上了scoped属性, 这个标签下的所有样式,就变成页面私有的样式。因此也不会发生样式冲突的问题

```vue
<style scoped>
  .my-page {
    .list {}
    .submit-btn {}
  }
</style>
```

### 命名注意事项

 - 尽可能精简、明确

```css
  // 推荐
  #nav {}
  .author {}

  // 不推荐
  #navigation {}
  .atr {}
```


 - 使用小写字母 并且单词之间使用中划线 "-" 作为连接符

```css
   // 推荐
   .ads-sample {}

   // 不推荐
   .demoimage {}
 ```

 - 避免无谓的元素选择器

```css
  // 推荐
  #example {}
  .error {}

  // 不推荐
  ul#example {}
  div.error {}
```

 - 使用前缀来减少命名冲突

```css
  .adw-help {}
  #main-note {}
```


### 更多命名方案

#### BEM命名原则
[BEM](http://getbem.com) 全称为Block-Element-Modifier
包括以下部分

* Block 所属组件名称
* Element 组件内元素名称
* Modifier 元素或组件修饰符

其核心思想就是组件化。首先一个页面可以按层级依次划分未多个组件，其次就是单独标记这些元素。BEM通过简单的块、元素、修饰符的约束规则确保类名的唯一，同时将类选择器的语义化提升了一个新的高度。


使用 BEM 命名规范，理论上讲，每行 `css` 代码都只有一个选择器。

BEM代表 **“块（block）,元素（element）,修饰符（modifier）”**,我们常用这三个实体开发组件。

在选择器中，由以下三种符号来表示扩展的关系：

    -   中划线 ：仅作为连字符使用，表示某个块或者某个子元素的多单词之间的连接记号。
    __  双下划线：双下划线用来连接块和块的子元素
    _   单下划线：单下划线用来描述一个块或者块的子元素的一种状态

    type-block__element_modifier

##### 块（block）

一个块是设计或布局的一部分，它有具体且唯一地意义 ，要么是语义上的要么是视觉上的。

在大多数情况下，任何独立的页面元素（或复杂或简单）都可以被视作一个块。它的HTML容器会有一个唯一的CSS类名，也就是这个块的名字。

针对块的CSS类名会加一些前缀（ `ui-`），这些前缀在CSS中有类似命名空间的作用。

一个块的正式（实际上是半正式的）定义有下面三个基本原则：

1.  CSS中只能使用类名（不能是ID）。
2.  每一个块名应该有一个命名空间（前缀）
3.  每一条CSS规则必须属于一个块。

例如：一个自定义列表 `.list` 是一个块，通常自定义列表是算在 `mod` 类别的，在这种情况下，一个 `list` 列表的block写法应该为:
``` css
    .list
```

##### 元素（element）

块中的子元素是块的子元素，并且子元素的子元素在 `bem` 里也被认为是块的直接子元素。**一个块中元素的类名必须用父级块的名称作为前缀。**

如上面的例子，`li.item` 是列表的一个子元素，
```css
	  /* 推荐 */
    .list{}
    .list__item{}

 	  /* 不推荐 */
    .list{}
    .list .item{}
```

##### 修饰符（modifier）

一个“修饰符”可以理解为一个块的特定状态，标识着它持有一个特定的属性。

用一个例子来解释最好不过了。一个表示按钮的块默认有三个大小：小，中，大。为了避免创建三个不同的块，最好是在块上加修饰符。这个修饰符应该有个名字（比如：`size` ）和值（ `small`，`normal` 或者 `big` ）。

如上面的例子中，表示一个选中的列表，和一个激活的列表项

```css
    /* 推荐 */
    .list{}
    .list_select{}
    .list__item{}
    .list__item_active{}

     /* 不推荐 */
    .list{}
    .list.select{}
    .list .item{}
    .list .item.active{}
```


综合例子:
 ```html
 /* html */
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit" />
</form>
 ```

  ```css
  /* css */
.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }
  ```

使用BEM可以让classname命名变得简单易懂，可读性更强，利于项目管理和多人协作，
并且BEM命名规则中classname没有嵌套,便于维护、复用。
但是，BEM 强调单一职责原则和单一样式来源原则，意味着传统纯手工 CSS 可能会产生大量重复的代码。


#### OOCSS命名原则
[OOCSS](http://oocss.org/) (Object-Oriented CSS) 即面向对象CSS
主要有两个规则:
1. 分离结构和皮肤（separate structure and skin）

 皮肤即一些重复的视觉特征，如边框、背景、颜色，分离是为了更多的复用；结构是指元素大小特征，如高度，宽度，边距等等。
 ```css
   // 推荐
   .button {
     padding: 10px;
   }
   .widget {
     overflow: auto;
   }
   .skin {
     box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
   }

  // 不推荐
 .button {
   padding: 10px;
   box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
 }
 .widget {
   overflow: auto;
   box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
 }
 ```
 2. 分离容器和内容（separate container an content）

打破容器内元素对于容器的依赖，元素样式应该独立存在。

```html
  // 推荐
  <div class="container"><h2 class="category">xxx</h2></div>
  .category {...} //h2元素 有一个独立的选择器

  //不推荐
  <div class="container"><h2>xxx</h2></div>
  .container h2 {...} // h2元素依赖于父元素 container
```

使用OOCSS原则，遵循的是DRY(don't repeat yourself)的原则,能够减少大量的重复的样式代码，
提高代码复用率。同时，视觉元素可以灵活组合各个类名，展示不同的效果，丰富的类名也同时使得元素有着更好的可读性；
另一方面，由于容器和内容的分离，CSS 完成了与 HTML 结构解耦。
但同时也会带来一些缺点，抽象复用会使class越来越多，极端情况会产生可能产生很多原子类，
这对于那些偏向于“单一来源原则”的开发者来说并不受欢迎。

### 常用命名推荐

| ClassName | 含义 |
| ------------ | ------------- |
| about | 关于 |
| account | 账户 |
| arrow | 箭头图标 |
| article | 文章 |
| aside | 边栏 |
| audio | 音频 |
| avatar | 头像 |
| bg,background | 背景 |
| bar | 栏（工具类）|
| branding | 品牌化 |
| crumb,breadcrumbs | 面包屑 |
| btn,button | 按钮 |
| caption | 标题，说明 |
| category | 分类 |
| chart | 图表 |
| clearfix | 清除浮动 |
| close | 关闭 |
| col,column | 列 |
| comment | 评论 |
| community | 社区 |
| container | 容器 |
| content | 内容 |
| copyright | 版权 |
| current | 当前态，选中态 |
| default | 默认 |
| description | 描述 |
| details | 细节 |
| disabled | 不可用 |
| entry | 文章，博文 |
| error | 错误 |
| even | 偶数，常用于多行列表或表格中 |
| fail | 失败（提示） |
| feature | 专题 |
| fewer | 收起 |
| field | 用于表单的输入区域 |
| figure | 图 |
| filter | 筛选 |
| first | 第一个，常用于列表中 |
| footer | 页脚 |
| forum | 论坛 |
| gallery | 画廊 |
| group | 模块，清除浮动 |
| header | 页头 |
| help | 帮助 |
| hide | 隐藏 |
| hightlight | 高亮 |
| home | 主页 |
| icon | 图标 |
| info,information | 信息 |
| last | 最后一个，常用于列表中 |
| links | 链接 |
| login | 登录 |
| logout | 退出 |
| logo | 标志 |
| main | 主体 |
| menu | 菜单 |
| meta | 作者、更新时间等信息栏，一般位于标题之下 |
| module | 模块 |
| more | 更多（展开） |
| msg,message | 消息 |
| nav,navigation | 导航 |
| next | 下一页 |
| nub | 小块 |
| odd | 奇数，常用于多行列表或表格中 |
| off | 鼠标离开 |
| on | 鼠标移过 |
| output | 输出 |
| pagination | 分页 |
| pop,popup | 弹窗 |
| preview | 预览 |
| previous | 上一页 |
| primary | 主要 |
| progress | 进度条 |
| promotion | 促销 |
| rcommd,recommendations | 推荐 |
| reg,register | 注册 |
| save | 保存 |
| search | 搜索 |
| secondary | 次要 |
| section | 区块 |
| selected | 已选 |
| share | 分享 |
| show | 显示 |
| sidebar | 边栏，侧栏 |
| slide | 幻灯片，图片切换 |
| sort | 排序 |
| sub | 次级的，子级的 |
| submit | 提交 |
| subscribe | 订阅 |
| subtitle | 副标题 |
| success | 成功（提示） |
| summary | 摘要 |
| tab | 标签页 |
| table | 表格 |
| txt,text | 文本 |
| thumbnail | 缩略图 |
| time | 时间 |
| tips | 提示 |
| title | 标题 |
| video | 视频 |
| wrap | 容器，包，一般用于最外层 |
| wrapper | 容器，包，一般用于最外层 |


