- ###### v-once

用于一次性数据绑定，当页面加载完毕之后，将数据的初始值渲染到元素内中，当数据发生变化时，不再进行重新渲染。当页面存在大量的数据绑定时，会消耗很高的性能，导致页面卡顿，如果数据首次渲染之后不再发生变化，那么可以使用v-once指令进行数据绑定

- v-html

用于将一段html字符串作为html内容解析显示到某个标签中

- 指令修饰符

1. `v-model.number`:作用是将输入框中的内容转为数字之后再绑定
2. `v-model.trim:`将输入框中的内容进行trim(去除两端的空格)再绑定
3. v-`model.lazy`默认情况下v-model指令会在input事件中进行重新渲染，使用.lazy修饰符后则会在按下回车或者失去焦点时进行重新渲染
4. `.prevent`用于v-on指令，效果是组织所监听的事件的默认行为
5. .`stop`用于v-on指令,相当于`e.stopPropergation`
6. `@keydown.13`：`.{keyCode}`修饰符，用于修饰键盘按键事件，只有按下`keyCode`为这个值的按键才会触发事件 

- 过滤器使用：多个过滤器可以连续使用

```javascript
<body>
    <div id="app">
        <input type="text" v-model="txt">
        <p>{{txt}}</p>
    </div>
</body>
<script>
    let root = new Vue({
        el:"#app",
        data:{
            txt:"abc"
        },

        // 组件的监听器
        watch:{
            // 监听器中可以为组件中的数据添加监听函数，每当这个数据发生变化时，监听函数就会被调用。
            // 监听函数被调用时会传递两个参数分别是改变之后的值和改变之前的值。
            txt(after,before){
                console.log(arguments);
            },

            // 监听器除了可以监听组件的数据，还可以监听组件的计算结果。

            // 组件中凡是通过set/get定义的属性都可以监听。
        }
    });

    console.log(root);

</script>

```

在`vue`中父组件向子组件传值，子组件接受的props可以是一个数组`props:["n1"]`也可以是：

```javascript
props:{
            p1:{
                // required设置次传值为必须项
                required:true,
                // type限制传值类型，可以同时设置多个类型
                type:[Number,String]
            },
            p2:{
                // 设置传值的默认值
                default:"默认值"
            },
            age:{
                // 添加自定义校验规则
                validator(v){
                    return v>0;
                }
            }
        }
```

# react

- react框架的特点：组件化开发，虚拟`dom`，高阶组件

- `jsx`是`js`与`html`混用的一种语法
- react中，一个组件是由两个文件构成的`jsx`和`css`

##### 可枚举性：用来控制所描述的属性，是否将被包括在for...in循环之中

```javascript
object.assign(target,source)
//将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。
```

React-Redux 提供`connect`方法，用于从 UI 组件生成容器组件

```javascript
import { connect } from 'react-redux'

const VisibleTodoList = connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoList)
```

