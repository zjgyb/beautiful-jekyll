---
layout: post
title: React(render)
tags: Front-end React
---

# 总结每日所学知识——react篇

## 今天看到了《前端大全》里的一篇文章[链接](https://mp.weixin.qq.com/s/05SWQW7XeHHsk4QvACiMeA)，结合最近所学进行了理解

### [第一题](https://codepen.io/zjgyb/pen/QarNYN?editors=0010)(target:'_blank')
```react
class Content extends React.Component {
  render() {
    console.log('render content');
    return <div>Content</div>
  }
}
class App extends React.Component{
  handleClick() {
    this.setState({
      a: 1
    })
  }
  render() {
    console.log('render App');
    return(
      <div>
        {/* 点击之后是会被重新渲染的，因为state属性发生了变化，因为有新的状态，因此会被重新渲染，先App里的render渲染，再Content里的*/}
        <button onClick={this.handleClick.bind(this)}>setState</button>
        <Content />
      </div>
    );
  }
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
)
```
