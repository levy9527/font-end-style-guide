title: class命名
---

class的命名应该尽量精短、明确，必须以**字母开头命名**，且**全部字母为小写**，单词之间**统一使用中划线** “-” 连接

### 命名原则
现在前端开发团队使用的是命名原则是 在页面代码的根元素加上 `class=${page-name}`
并且在后续的css代码中, 该页面的类选择器都放在.pageName中

```vue
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


除了这样的命名规则之外, 团队在使用vue作为技术栈的项目中,也会使用scoped。

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

 - 在子模块数量可预测的情况下，继承父模块的命名前缀

```html
<div class="modulename">
  <div class="modulename-cover"></div>
  <div class="modulename-info"></div>
</div>
```

 当子孙模块超过4级或以上的时候，可以考虑在祖先模块内具有识辨性的独立缩写作为新的子孙模块

```html
  /* 推荐 */
  <div class="modulename">
    <div class="modulename-cover"></div>
    <div class="modulename-info">
      <div class="modulename-info-user">
      <div class="modulename-info-user-img">
        <img src="" alt="">
        <!-- 这个时候 miui 为 modulename-info-user-img 首字母缩写-->
        <div class="miui-tit"></div>
        <div class="miui-txt"></div>
        ...
        </div>
      </div>
      <div class="modulename-info-list"></div>
    </div>
  </div>

/* 不推荐 */
<div class="modulename">
  <div class="modulename-cover"></div>
  <div class="modulename-info">
    <div class="modulename-info-user">
    	<div class="modulename-info-user-img">
    	  <img src="" alt="">
    	  <div class="modulename-info-user-img-tit"></div>
    	  <div class="modulename-info-user-img-txt"></div>
    			...
        </div>
      </div>
      <div class="modulename-info-list"></div>
     </div>
   </div>
```

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
| wrap, wrapper | 容器，包，一般用于最外层 |

### 更多命名规则
在制定命名原则的同时, 也列出更多命名原则, 方便读者可以了解更多。

1. [BEM命名原则](http://getbem.com)

BEM核心思想就是组件化。首先一个页面可以按层级依次划分为多个组件，其次就是单独标记这些元素。

使用BEM可以让classname命名变得简单易懂，可读性更强，利于项目管理和多人协作，
并且BEM命名规则中classname没有嵌套,便于维护、复用。
但是，BEM 强调单一职责原则和单一样式来源原则，意味着传统纯手工 CSS 可能会产生大量重复的代码。


2. [OOCSS命名原则](http://oocss.org)

OOCSS (Object-Oriented CSS) 即面向对象CSS, 主要有两个规则，分别是分离结构和皮肤和分离容器和内容。

 使用OOCSS原则，遵循的是DRY的原则,能够减少大量的重复的样式代码，提高代码复用率。

 另一方面，由于容器和内容的分离，CSS 完成了与 HTML 结构解耦。

 但同时也会带来一些缺点，抽象复用会使class越来越多，极端情况会产生可能产生很多原子类，
 这对于那些偏向于“单一来源原则”的开发者来说并不受欢迎。

