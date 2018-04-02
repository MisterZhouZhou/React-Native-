
<center><font size=6>**React Native 编码规范**</font></center>

## 基本规范

 >  1.每个文件只包含一个React组件，命名要顾名知义
 
 >  2.尽可能的使用ES6语法
 
 >  3.console，alert在调试时写，调试完立即删除
 
 > 4.代码缩进格式统一，工具类方法注意添加注释
 

## 命名规范
  > 1.命名中不要出现中文

  > 2.文件名: 文件夹和文件名要使用大驼峰命名法,比如 HomeIndex.js
  
  > 3.图片命名规则： 模块_xx.png 或者 模块/xx.png
  
 ```
  setting_bg.png
  setting/bg.png

 ```

  > 4 组件命名: 与文件名（除中缀外）完全一致。如果组件单独放置在目录中，则目录名也一致。
  
```
  import FootView from './FootView'

```


## 变量与常量声明
### 变量

>	1.尽量使用let来代替var

>	2.对于全局变量声明，采用`global.xxx = xxx`，但应避免声明过多全局变量污染环境

### 常量
  > 1.对于常量应使用const进行声明，命名采用驼峰写法
  
  > 2.对于使用 immutable(不可改变的) 数据应用const进行声明

### 字符串
> 1.以反引号( ` )标示
> 2.可读性更强，代码更易编写

```
   `How are you, ${name}?`
```

## 属性
### 属性名
 
> 1.组件的属性使用小驼峰命名法

 ```
  fontSize={12}, textColor='#FFFFFF' 
 ```
> 2.使用外联样式时,属性名最好带有Style关键字
  
  ```
  flexStyle.js
  ```


### 属性设置

>  1.在封装的组件内最好设置属性(以便`propTypes`校验),以免类型不对导致的错误。

>  2.属性较多使用`{...this.props}`语法(最好在属性开头加上`{...this.props}`,为了防止少写属性,产生报错)


## 注释

 > 1.组件之间的注释需要用 `{/* 注释内容 */}` 包裹 
 
   ```
    {/* 这是组件间注释 */}
   ```
     
 > 2.组件之外的注释使用 `{/* 注释内容 */}` 或者 `// 注释内容`
 
 ```
 {/* 这是组件间注释 */}
 // 这是组件外注释 
 ```


## 条件输入
>1.条件输出值 

```
  {this.state.on ? 'On' : 'Off'}
```
>  2.条件输出组件内容 

```
  {this.state.on ? <Text>On</Text> : <Text>Off</Text>}

```


## 组件
> 使用class与extends关键字。不使用React.createClass方法。需要导出的组件直接在class关键字前使用export default。

```
// bad
export default React.createClass({
});

// good
export default class HomeView extends Component {
}

class HomeView extends Component {
}
export default

```

### 自闭合标签
>  1.JSX 中所有标签必须闭合, 没有子元素的组件使用自闭合语法，自闭合标签 / 前留一个空格；

example:

```
// bad
<Logo></Logo>
<Logo    />
<Logo
 />
// good
<Logo />

```

### state/props
> 对于多个单词组成的pros，使用驼峰命名法。不使用下划线或连接线。

```
// bad
var userName = this.props.userName;
let checked = this.state.checked;

// good
const { userName, age, sex } = this.props;
const { checked } = this.state;

```


### 括号
> 当JSX标签超过一行时，使用括号包裹。单行时，不必有括号。
 
```
/// bad
render() {
  return <View>
           <Image />
         </View>;
}

// good
render() {
  return (
    <View>
      <Image />
    </View>
  );
}

// good, when single line
render() {
  return <Text>{body}</Text>;

```

### 方法声明的顺序
> 原则上按如下顺序排列React组件的各个方法（生命周期）：

```
1. constructor
2. 静态方法（static methods)
3. getChildContext
4. componentWillMount
5. componentDidMount
6. componentWillReceiveProps
7. shouldComponentUpdate
8. componentWillUpdate
9. componentDidUpdate
10. componentWillUnmount
11. 点击处理或事件处理函数，比如onClickSubmit()、 onChangeDescription()
12. 用在render中的getter方法，比如getSelectReason()、 getFooterContent()
13. 可选的render方法，比如renderNavigation()、renderProfilePicture()
14. render


```
或者

```
1. constructor
2. 静态方法（static methods)
3. getChildContext
4. componentWillMount
5. componentDidMount
6. componentWillReceiveProps
7. shouldComponentUpdate
8. componentWillUpdate
9. componentDidUpdate
10. componentWillUnmount
11. 点击处理或事件处理函数，比如onClickSubmit()、 onChangeDescription()
12. 用在render中的getter方法，比如getSelectReason()、 getFooterContent()
13. render
14. 抽离的组件代码块，例如renderItemView，renderHeaderView


```

## 模块

>  1.使用import / export来做模块加载导出，不使用非标准模块写法

```
// 不好
const colors  = require('./colors');
module.exports = color.lightRed;

// 好
import { lightRed } from './colors';
export default lightRed;

```

>  2.import / export 后面采用花括号{ }引入模块的写法时，须在花括号内左右各保留一个空格

```
// 不好
import {lightRed} from './colors';
import { lightRed} from './colors';
// 好
import { lightRed } from './colors';

```

# 箭头函数书写约定
>1.函数体只有单行语句时，允许写在同一行并去除花括号

>2.当函数只有一个参数时，允许去除参数外层的括号

```
// 好
const foo = x => x + x; // 注意此处会隐性return x + x
const foo = (x) => {
  return x + x; // 若函数体有花括号语句块时须进行显性的return
}; 
[1, 2, 3].map( x => x * x);

// 不好
(function(){
	console.log('哈');
})();

// 好
(()=>{
	console.log('哈');
})();

```


