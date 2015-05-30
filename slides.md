
### ⚛

# ⚛

## 简聊前端中的 React.js 使用

----

### 关于我

* 题叶, jiyinyiyong, ChenYong
* React.js 中文社区, 微博, 维护者
* 迷信函数式编程
* http://programming.webcity.io/

----

### 简聊 & React.js

简聊一款面向企业用户的即时沟通工具

* http://talk.ai/
* 单页面应用, 实时性
* <hr@teambition.com>

React.js

> A JavaScript library for building user interfaces.

----

### 技术栈

* React.js
* Node.js, WebSocket, Ajax
* LESS, Font Icons

难点:

* 密度很高的组件, 组件复用, 开发速度
* 大量存储在前端的数据需要同步(还好, 数据结构简单)

----

### 迁移的过程时间

逐步迁移

* 2014.02 Backbone, doT.js, require.js
* 2014.05 开始研究 React
* 2014.10 在侧边栏用 React 写过渡动画
* 2014.11 优化消息流性能
* 2015.01 去掉 Backbone 依赖, 引入 Flux
* 2015.02 切换到 Webpack

后面是更多的组件化的工作, 以及功能增改...

----

### 迁移的方向

* 去掉 jQuery 的操作, 更多使用 `props` 和 `state` 控制界面
* 更多全局的 Store, Single Source of Truth
* 路由, 层次, 结构更加清晰, 组件重用
* ... 怎么样让开发更快, 同时具备可靠性

----

### CoffeeScript 写 JSX

* 模仿 Jade 的缩进
* 一切皆是表达式

```coffee
div = React.createFactory 'div'
span = React.createFactory 'span'

React.createClass
  getInitialState: -> isSunny: false, color: 'green'
  render: ->
    div className: 'weather',
      span null, 'Today is: '
      if @state.isSunny then 'Nice' else 'OK'
      switch @state.color
        when 'blue' then 'Blue'
        when 'green' then 'Green'
        else 'Purple'
```

----

### 组件化

非常利于组件化

```coffee
Searching 234 files for "createClass"
...
161 matches across 158 files
```

现有的组件

* 大部分组件跟项目结合紧密
* 若干个组件计划独立出来在 GitHub 维护

----

### 组件编写习惯

* `props` 使用 `PropTypes`
* Component Spec 分成 "生命周期", "方法", "事件绑定", "渲染函数"
* 渲染部分的代码尽量把用变量把逻辑抽出来, 使 DOM 清晰
* 组件的事件命名的写法, 比如 `onHeaderClick`
* ... 让 DOM 看起来更清晰, 逻辑更明确

----

### Flux

* Store: 参考官方实现
* View, Components(App, Module),
* Actions: 我们的 Ajax, WebSocket 和 Action 紧密结合的

一些思考:

* `listenTo` 用法延续 Backbone 的习惯, 是否最佳?
* 组件拆分粒度控制, Mixin 使用, 怎样权衡?
* 目前没有 `waitFor` 的写法?

----

### Webpack

优势:

* 代码热替换(Hot Module Replacement)
* 分包, Hashing 方案明确(比从前 Gulp 写清晰很多)
* 内网访问开发环境, 方便其他人查看进展
* 同时兼容 AMD, CommonJS 写法, 多种代码格式, 迁移

Demo:

* [react-lite-dropdown](https://github.com/teambition/react-lite-dropdown)

----

### Webpack 的不足

劣势:

* 编译优化速度慢(相比 Gulp, 清除无用代码)
* 功能多, 配置高级功能门槛不少
* 代码热替换并不总是成功的, 还是需要刷新

----

### 目前了解的难度

React 的难度, 也关系到招聘:

* Flux 的理解, State 存储数据的场景怎样区分
* 一些特殊问题仍然需要 DOM 操作, 但和 React 怎样结合
* 怎样和社区已有的组件衔接, 目前自己写居多
* 实现动画的效果, 比如 Modal 动画实现会 tricky

----

### 仍然在努力的问题

依然在尝试跟了解:

* 更稳定和清晰的 Store(需要更清晰梳理, Immutable.js 存在门槛)
* 提升组件质量(样式的组件化, 布局问题)
* 单页面应用以外的场景怎样借助 React 的优势

----

### QA?

Thanks.

QA: 10:30 am - 11:00 am
