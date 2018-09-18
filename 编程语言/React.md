# 引入

	react.min.js - React 的核心库
	react-dom.min.js - 提供与 DOM 相关的功能
	babel.min.js - Babel 可以将 ES6 代码转为 ES5 代码，这样我们就能在目前不支持 ES6 浏览器上执行 React 代码。Babel 内嵌了对 JSX 的支持。

# jsx

	 {/*注释...*/}
	在 JSX 中不能使用 if else 语句，单可以使用 conditional (三元运算) 表达式来替代。
	表达式写在花括号 {} 中。

# 组件

	var HelloMessage = React.createClass({
	  render: function() {
	    return <h1>Hello World！</h1>;
	  }
	});
	
	ReactDOM.render(
	  <HelloMessage />,
	  document.getElementById('example')
	);
	React.createClass 方法用于生成一个组件类 HelloMessage。
	<HelloMessage /> 实例组件类并输出信息。


# 状态

	getInitialState 方法用于定义初始状态，也就是一个对象，这个对象可以通过 this.state 属性读取。当用户点击组件，导致状态变化，this.setState 方法就修改状态值，每次修改以后，自动调用 this.render 方法，再次渲染组件。

# props	属性


