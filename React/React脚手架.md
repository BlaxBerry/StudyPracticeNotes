# React脚手架 create-react-app 

create-react-app可以快速创建一个急于React脚手架的模版项目

<img src="https://staging-qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F484272%2F52cfad2d-ef8c-b70d-3aa5-ec79b0576737.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1bb6e4bac443e2d9d368f6b114b249a2" style="zoom:50%;" />

## 简介

- 整体技术框架：

  react + **webpack** + ES6 + eslint

- 特点：

  模块化、组件化、工程化





## 创建和启动项目

1. **全局**安装

```bash
npm install -g create-react-app
```

2. 切换到指定目录下，创建脚手架项目

```bash
create-react-app demo
```

3. 进入项目目录文件夹

```bash
cd demo
```

4. **启动项目**

```bash
yarn start
```

```bash
 yarn start
    Starts the development server.

  yarn build
    Bundles the app into static files for production.

  yarn test
    Starts the test runner.

  yarn eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd demo-react
  yarn start
```

5. 浏览器打开**http://localhost:3000**

<img src="https://staging-qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F484272%2F52cfad2d-ef8c-b70d-3aa5-ec79b0576737.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1bb6e4bac443e2d9d368f6b114b249a2" style="zoom: 20%;" />

6. 编辑项目的src目录下的App.js文件







## 基本项目目录结构

```js
Demo
|-node_modules
|-public
|-src
|-package.json
|-yarn.lock
```

<img src="https://pbs.twimg.com/media/E2N6q1tVEAAFAIG?format=jpg&name=medium" style="zoom:33%;" />

---

### public

#### index.html

SPA单页面应用

整个项目只有一个HTML文件

%PUBLIC_URL% 代表public文件夹路径

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <!-- favicon图标 -->
    <!--%PUBLIC_URL%：代表public文件夹路径-->
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    
    <!-- 开启理想视口，移动端适配配置 -->
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    
    <!-- 安卓手机的浏览器页签+地址栏的颜色 -->
    <meta name="theme-color" content="#000000" />
    
    <!-- 描述网站信息 -->
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    
    <!-- 苹果手机 网页添加到主屏后的图标 -->
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    
    <!-- 应用加壳时的配置文件 -->
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
  
    <title>React App</title>
  </head>
  
  <body>
    <!-- 若浏览器不支持JS脚本的运行，则显示内容 -->
    <noscript>
      You need to enable JavaScript to run this app.
    </noscript>
    
    <!-- 组件渲染的容器 -->
    <div id="root"></div>
   
  </body>
</html>
```

### src

#### App.js

因为ReactDOM.render不是追加操作，会顶替之前写到容器root中的内容

所以ReactDOM.render方法只执行一次，

root容器中只放一个组件，即 App.js

其余的自定义组件都放入APP.js组件中，作为其子组件

---

#### index.css

通用样式

也可以放入public目录中（需要修改index.js中的引入路径）

---

#### index.js

入口文件

相当于Vue的**main.js**

```react
// 引入核心库
import React from 'react';
import ReactDOM from 'react-dom';
// 引入通用样式
import './index.css';
// 引入主组件
import App from './App';
// 记录页面性能
import reportWebVitals from './reportWebVitals';

// 渲染主组件到页面
ReactDOM.render(
  // 包裹<React.StrictMode>可以检测代码不合理的错误
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

reportWebVitals();
```







## 脚手架常用命令

#### yarn start

启动项目

#### yarn buid

打包项目

#### yarn eject

暴露webpack相关的所有配置文件

**webpack.config.js**	

react脚手架为了防止失误修改webpack的配置文件

默认将所有webpack相关的配置文件全部隐藏







## 组件模块化

```js
src
|-components
	|-Hello
			|-Hello.js
			|-Hello.css
|-App.js
|-index.js
```

index.js

```react
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'


ReactDOM.render(
    <App></App>,
    document.getElementById('root')
)
```

App.js

```react
import React, { Component } from 'react'

import Hello from './components/Hello/Hello'
import About from './components/About/About'

export default class App extends Component {

    render() {
        return (
            <div>
               <Hello/>
            	 <About/>
          	</div>
        )
    }
}
```

Hello.js

```react
import React, { Component } from 'react'

import './Hello.css'

export default class Hello extends Component {

    render() {
        return (
            <div>
                hello
            </div>
        )
    }
}
```



### 组件文件 和 普通JS文件

#### 1. 文件首字母

有的公司通过文件名的大小写区分

```js
src
|-components
	|-Hello
			|-fun.js
			|-Hello.js
			|-Hello.css
	|-About
			|-fun.js
			|-About.js
			|-About.css
|-App.js
|-index.js
```

---

#### 2. 文件后缀名

有的公司会将自定义组件文件的后缀名改为 **.jsx**

```js
src
|-components
	|-Hello
			|-Hello.jxs
			|-Hello.css
	|-About
			|-About.jxs
			|-About.css
|-App.js
|-index.js
```

自定义组件在主组件App.js文件中的引入时的路径和写法不变

```react
import React, { Component } from 'react'

import Hello from './components/Hello/Hello'
import About from './components/About/About'

export default class App extends Component {

    render() {
        return (
            <div>
               <Hello/>
            	 <About/>
            </div>
        )
    }
}
```

---

#### 3. 文件名 index.js

有的公司会将所有自定义组件名改为 **index.js**

```js
src
|-components
	|-Hello
			|-index.js
			|-index.css
	|-About
			|-index.js
			|-index.css
|-App.js
|-index.js
```

在主组件App.js中引入时可以简写

```react
import React, { Component } from 'react'

import Hello from './components/Hello'
import About from './components/About'

export default class App extends Component {

    render() {
        return (
            <div>
               <Hello/>
            	 <About/>
            </div>
        )
    }
}
```





## CSS样式模块化

因为各个自定义组件最终都被引入到了主组件App.js中

所以会导致在某一个组件中定义的CSS样式className会影响到其余组件中的相同className，后引入的会覆盖前面的样式

若是只写CSS样式，

需要通过模块化，将样式文件改名为 **module.css**

```js
src
|-components
	|-Hello
			|-index.js
			|-index.module.css
	|-About
			|-index.js
			|-index.module.css
|-App.js
|-index.js
```

将样式文件作为模块，在组件文件中引入

再使用样式的节点上通过“该模块的类名”设置类名样式

```react
import React, { Component } from 'react'

import hello from './Hello.module.css'

export default class Hello extends Component {

    render() {
        return (
            <div>
               <div className={hello.title}>
                 Hello
            	 </div>
            </div>
        )
    }
}
```

---

如果是**Less**文件的话，

不需要模块化处理，可通过嵌套解决

```less
#a {
  .xxx {}
}

#b {
  .xxx {}
}
```







## VSCode插件

![](https://miro.medium.com/max/1838/1*XgMBj0lGzZs7O6okKg5sFA.png)

**rfc + 回车**  （react function component）

快速生成React的函数组件

**rcc + 回车** （react classn component）

快速生成React的类组件

```jsx
import React, { Component } from 'react'

export default class 组件文件名 extends Component {
    render() {
        return (
            <div>
                
            </div>
        )
    }
}
```





## 组件化编码流程

1. 分析功能，拆分组件

2. 实现静态组件：使用组件实现静态页面效果

3. 实现动态组件：

   - 动态显示初始化数据
     - 数据类型
     - 数据名称
     - 数据保存在那个组件中

   - 交互效果（绑定事件）



数据存放在状态中

- 仅某个组件自己使用，数据放在自身的state状态中
- 被很多组件使用，数据放在共同的父组件的statr状态中



状态在哪，操作状态的方法就放在哪



父子组件之间的通信

- 父—>子：通过自定义属性传递，通过this.props属性接收
- 子—>父：父传给子一个函数，子调用函数将数据作为函数参数









## 暴露脚手架配置

```bash
yarn eject
```

会暴露出react脚手架的所有配置文件

```js
XXX
|-config
|-scripts
```





## 打包项目

```bash
yarn build
```

会生成一个bulid文件夹



