### 1. 3.0的嵌套路由实现
route和this.props.children实现
```
<Route path="/" component="app">
  <Route path="home" component={Home}></Route>
  <Route path="about"> component={About}</Route>
  <Route path="repos> component={Repos}
    <Route path="hello" component={Hello}>
      <Route path="world> component={World}</Route>
    </Route>
  </Route>
</Route>
```
```
// app中
const app = ({children})=>{
  return (
    <div>
      app
      {children}
    </div>
  );
}
```
### 2. 4.0的嵌套实现
```
// router.js
import React from 'react';
import { Router, Route, Switch, Redirect } from 'dva/router';
import App from './routes/App';

function RouterConfig({ history}) {
  return (
    <Router history={history}>
      <Switch>
        <Route path="/" component={App} />
      </Switch>
    </Router>
  );
}

export default RouterConfig;
```
```
// app.js
import { connect } from 'dva';
import { NavLink, Route,Switch } from 'dva/router';
import About from './about'
import IndexPage from './IndexPage'
import Repos from './repos'
import Hello from './hello'
import World from './world'
import styles from './IndexPage.css';

// 没有connnect时，有history，location和match
// connect后，加了个dispatch
// 放在Switch外面，有dispatch和children
// 放在Switch外面，不connect只有children
const App = ({})=>{
  return (
    <div>
      <div className={styles.link_container}>
        <NavLink to="/" activeClassName={styles.active}>app</NavLink>
        <NavLink to="/home" activeClassName={styles.active}>Home</NavLink>
        <NavLink to="/about" activeClassName={styles.active}>About</NavLink>
        <NavLink to="/repos" activeClassName={styles.active}>Repos</NavLink>
        <NavLink to="/repos/hello" activeClassName={styles.active}>hello</NavLink>
        <NavLink to="/repos/hello/world" activeClassName={styles.active}>world</NavLink>
      </div>
      <Switch>
        <Route path="/home" exact component={IndexPage} />
        <Route path="/about" exact component={About} />
        <Route path="/repos" component={Repos} />
      </Switch>
    </div>
  );
}

export default connect()(App);
```
```
// repos.js
import React from 'react';
import {Switch, Route} from 'dva/router'
import Hello from './hello';

const repos = () => {
  return (
    <div>
      repos
      <Switch>
        <Route path="/repos/hello" component={Hello}></Route>
      </Switch>
    </div>
  );
}

export default repos;
```
react-router-4.0中的路由实现了组件化，可以配置在dom中。
### 3. exact属性
exact是`准确`的意思，如果pathname配置的是'/',有exact`/home`则匹配不上，必须完全匹配'/'才行。4.0中用于实现3.0的ReactRoute。
### 4. location,match,history
![image](https://github.com/qingfengmy/blogs/raw/master/sources/20180115/0.png)

### 5. 动态路由
```
// router.js
function RouterConfig({ history, app }) {
  console.log('app', app)
  return (
    <Router history={history}>
      <Switch>
        <Route path="/" component={App} app={app} />
      </Switch>
    </Router>
  );
}
```
```
import dynamic from 'dva/dynamic'
<Route path="/home" exact component={dynamic({
  app,
  component: () => import('./IndexPage')
})} />
<Route path="/about" exact component={dynamic({
  app,
  component: () => import('./about')
})} />
```

注意：没用到的不要显性的import，如
```
import IndexPage from './indexpage'
import About from './about'
```
虽然这两个没有用到，但build时最终只会出现一个包。把这两行删除，则打包会出现三个包：`index.js,0.async.js,1.async.js`

### 6. 参考文章
[reactjs官网](https://reactjs.org/docs/hello-world.html)
[react-router官网](https://reacttraining.com/react-router/web/example/basic)
[React Router--React Router4](https://www.jianshu.com/p/9ffeb2ee4f38)

