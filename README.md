# Element UI React

## 开发环境

安装git hooks, 每次提交前会强制lint src下代码

```shell
npm run install:githooks
```

```shell
npm i && npm start
```

浏览器打开http://localhost:3000, Bingo🍺

## 组件接口

目前提供了3个基础组件, Component, PropTypes和View.

### Component

为了保持组件的可控性, 所有自定义组件都需要继承于此Component, 而不是React.Component.

* 属性
 * className [String], 可以将className附加到组件的根元素的class上.
 * style [Object], 可以将style附加到组件的根元素的style上.

* 方法
 * classNames(className, ..., className), 使用方法参照[1], 返回类型为String.

    ```jsx
    <div className={this.classNames('el-alert', `el-alert--${ this.props.type }`)}>
     ...
    </div>
    ```

### PropTypes

继承了React所有的PropTypes, 并提供了一些通用的自定义类型, 所有的自定义组件不再使用React.PropTypes.

* range(min, max)

### View

* 属性
 * show [any], Vue的`v-show`的实现, 参考[2].

     ```js
     // Vue
     <i class="el-alert__closebtn" :class="{ 'is-customed': closeText !== '', 'el-icon-close': closeText === '' }" v-show="closable" @click="close()">{{closeText}}</i>

     // React
     <View show={this.props.closable}>
     <i className={this.classNames('el-alert__closebtn', this.props.closeText ? 'is-customed' : 'el-icon-close')} onClick={this.close.bind(this)}>{this.props.closeText}</i>
     </View>
     ```

 * transition [String], Vue的`transition`的实现, 参考[3].

     ```js
     // Vue
     <transition name="el-alert-fade">
     ...
     </transition>

     // React
    <View transition="el-alert-fade">
    ...
    </View>
     ```

> 注意: React.Children.count(props.children) === 1

## 单元测试

项目使用**jest**来做单元测试, 执行以下命令:

```shell
npm test
```

> 因为组件使用了react-dom, 但是react-dom只允许初始化一次, 所以目前jest还无法正常测试React组件, 待react升级到15.4.0, 参考issue: https://github.com/facebook/jest/issues/1353

## UI自动化测试

> TODO

## Tasks

* es-lint

    ```shell
    npm run lint
    ```

## 贡献代码

代码规范请参考 [CONTRIBUTING.md](https://github.com/eleme/element-react/blob/master/CONTRIBUTING.md)

## References
1. https://github.com/JedWatson/classnames
2. https://vuejs.org/guide/conditional.html#v-show
3. https://vuejs.org/guide/transitions.html#Transitioning-Single-Elements-Components
