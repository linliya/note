---
title: Polymer轻松入门
createDate: 2017.9.25
desp: 用了polymer几个月了，在此总结一下一些点，希望刚开始学的同学可以轻松学会，愉快开发
author: linli
classify: 前端开发
---

## Polymer轻松入门

本文着重总结一下新手入门Polymer会比较困惑的点，具体教程请查看文档[polymer官网](https://www.polymer-project.org/1.0/docs/devguide/feature-overview)

`Polymer` 是Google 前端团队开发的一套前端库，目前已经出到了Polymer 2, Polymer 3也在研发当中了，由于现阶段还是用`polymer 1`比较多，所以本篇文章还是主要关注`polymer 1`的使用。

`polymer`的核心思想是组件化，一切皆为组件，同时支持单向和双向绑定，（不过为了让数据流动不那么混乱还是比较支持用单向绑定），我们可以将`html`,`css`,`js`都写在一个`html`文件里面，然后通过`link`标签的`rel` 属性`import`进来即可使用。

### 直接进入正题


#### 单向绑定与双向绑定

> 单向绑定： 顾名思义，即数据只能通过单向传递，在polymer中，常见的单向绑定是父子组件之间数据的的传递，兄弟之间之间如果要传递数据，则需要通过事件冒泡到父组件中，然后由父组件进行事件分发，

- 父子组件之间

```
app-parent为父组件，将userData传递给子组件app-child

<app-child user-data="[[userData]]"></app-child>

```
  > polymer中的属性名userData需要转化为user-data的形式，在app-child中通过this.userData即可拿到父组件传递过来的userData值

- 兄弟组件之间

> 双向绑定：双向绑定的数据会实现同步，一个数据的修改会影响到与它绑定的上下层数据，一般的应用场景是通过iron-ajax获取的数据对象，需要将其传递给该组件所在的作用域，请看以下例子：
