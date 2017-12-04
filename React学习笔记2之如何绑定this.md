## 如何绑定this

在用class声明的组件中,事件绑定中的this是不会自动绑定的,因此需要我们手动绑定.
```javascript
class Title extends Component {
  handleClick () {
    console.log(this)
  }
  render () {
    return (
      <h1 onClick={this.handleClick}>React 小书</h1>
    )
  }
}
ReactDOM.render(
  <Title />,
  document.getElementById('example')
);
```
这是因为 React.js 调用你所传给它的方法的时候，并不是通过对象方法的方式调用（this.handleClick），而是直接通过函数调用 （handleClick），所以事件监听函数内并不能通过 this 获取到实例。
如果你想在事件函数当中使用当前的实例，你需要手动地将实例方法 bind 到当前实例上再传入给 React.js。

通常有三种方式：
### a. 在构造函数中绑定this
```javascript
class Title extends Component {
  constructor(){
      this.handClick=this.handClick.bind(this)
  }
  handleClick () {
    console.log(this)
  }
  render () {
    return (
      <h1 onClick={this.handleClick}>React 小书</h1>
    )
  }
}
```
### b. 在事件处理程序中绑定this
```javascript
class Title extends Component {
  handleClick () {
    console.log(this)
  }
  render () {
    return (
      <h1 onClick={this.handleClick.bind(this)}>React 小书</h1>
    )
  }
}
```
### c. 使用箭头函数
```javascript
class Title extends Component {
  handleClick = ()=> {
    console.log(this)
  }
  render () {
    return (
      <h1 onClick={this.handleClick}>React 小书</h1>
    )
  }
}
```