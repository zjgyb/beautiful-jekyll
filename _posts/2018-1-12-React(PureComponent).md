---
layout: post
title: react(PureComponent)
tags: Front-end react
---

# 总结今日之所学——react篇

## 接昨天未讲完的题目，<a href="https://mp.weixin.qq.com/s/05SWQW7XeHHsk4QvACiMeA" target="_blank">来源地址</a>

### <a href="https://codepen.io/zjgyb/pen/wpjZRX" target="_blank">接下来的题目Codepen</a>
``` react
class Row extends React.Component {
  render () {
    const {item, style} = this.props;
    // style是经常更新的因此不要使用React.PureComponent
    // console.log(1)
    return (
      <tr style={style}>
        <td>{item.id}</td>
      </tr>
    )
  }
}
  
class Table extends React.Component {
// class Table extends React.Component {
  render() {
    const {list} = this.props;
    const itemStyle = {
      color: 'red'
    }
    return (
      <table>
          {list.map(item => <Row key={item.id} item={item} style={itemStyle} />)}
      </table>
    )
  }
}
  
class App extends React.Component {
  constructor() {
    super();
    this.state = {
      list: Array(10).fill(0).map((val, index) => ({id: index}))
    }
  }
  // state = {
  //   list: Array(10).fill(0).map((val, index) => ({id: index}))
  // }  
  handleClick() {
    this.setState({
      // otherState: 1
      list: [... this.state.list, 101]
    })
  }
  render() {
    const {list} = this.state;
    console.log(2)
    return (
      <div>
        <button onClick={this.handleClick.bind(this)}>change state!</button>
        <Table list={list} />
      </div>
    );
  }
}


ReactDOM.render(
  <App />,
  document.getElementById('root')
)
 ```
 
作者讨论了PureComponent在何种情况下会优化性能，下面是我的理解：<br />

&nbsp;&nbsp;在第二题中改变的是App组件中otherState状态，因此在Table组件中没有东西发生改变，因此render不会重新渲染，所以用PureComponent有利于性能优化，你可以用<code>console.log('sone render')</code> 来观察组件是否被重新渲染<br />

&nbsp;&nbsp;在第三题中改变的是App组件中的index状态，这将直接导致Table组件list的改变，从而使render中的itemStyle发生重构，因此在Row组件里的style每次会发生改变，把Component变成PureComponent无效，还会影响性能，因此该注意此类问题<br />
  
## 文章相关 <br />

<a href="https://zjgyb.github.io/2018-01-11-React(render)/" target="_blank">React(render)</a>
