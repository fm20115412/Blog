## jsx笔记
1、HTML 语言直接写在 JavaScript 语言之中，不加任何引号，这就是 JSX 的语法，它允许 HTML 与 JavaScript 的混写。
```javascript
const element = <h1>Hello, world!</h1>;
```
2、在JSX中使用{}嵌入任何js表达式
```javascript
const element = (
  <h1>
    Hello, {2+2}!
  </h1>
);
```
3、在为属性命名时，采用驼峰的方式
```javascript
const element = <div tabIndex="0"></div>;
```
4、jsx可以防止xss攻击，这是因为react会将用户的输入转义为字符串
```javascript
const element = (
  <div>
    <h2>{ `first &gt; second `}</h2>
    <h3>{`<em>hello</em>`}</h3>
  </div>
  
);
```
会显示为：

![enter image description here](https://github.com/fm20115412/Blog/blob/master/image/1.png)

5、react会调用React.createElement()函数将jsx语法转换为JavaScript 对象。
```javascript
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world'
  }
};
```

有了这个表示 HTML 结构和信息的对象以后，就可以拿去构造真正的 DOM 元素，然后把这个 DOM 元素塞到页面上。

![enter image description here](https://huzidaha.github.io/static/assets/img/posts/44B5EC06-EAEB-4BA2-B3DC-325703E4BA45.png)

6、true/false/undefined/null 等在react里渲染不出来
