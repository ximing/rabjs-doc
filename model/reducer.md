reducers 是唯一可以修改state的部分

#### 1，写法

##### 1.1简单写法

```js
{  
    namespace:'test',
    ...
    reducers:{
        firstReducer(state,action){
            return Object.assgin({},state,action.payload)
        }
    }
    ...
}
```

每个reducer函数会接收两个参数，第一个参数 state 是当前model的state对象，第二个参数 action是[flux-standard-action](https://github.com/acdlite/flux-standard-action) ，

正常情况的payload

```js
{
  type: 'something',
  payload: {
    text: 'Do something.'  
  }
}
```

异常情况的payload

```
{
  type: 'something',
  payload: new Error(),
  error: true
}
```

##### 1.2 正常写法（通过action调用 reducer的时候会使用）

```js
{
    namespace:'test',
    ...
    reducers:{
        firstReducer{
            start(state,action){},
            success(state,action){},
            error(state,action){},
            finish(state,action){},
        }
    }
    ...
}
```

通过action的方式\[见2.2\]调用reducer的时候 由于actions是一个异步函数，所以会有一定的生命周期，

1，start在 在异步action执行前会被调用，更改状态可以做一些诸如loading之类的事情

2，success在异步action执行成功后被调用

3，error在异步action执行失败后被调用

4，finish 无论异步action成功或失败都会被调用

\[注\]：四个生命周期方法都是可选项

#### 二，调用Reducer

2.1，直接通过dispatch 调用（不会触发生命周期，只会触发success/error方法）

```js
//调用 success
this.props.dispatch({type:'namespace.reducerName',payload:{a:1,b:2}})
//调用 error
this.props.dispatch({type:'namespace.reducerName',error:true,payload:{msg:'some thing'}})
```

2.2，通过action调用

2.2.1 存在和reducer同名的action的时候,调用action会自动调用同名的reducer，action的返回值就是 reducer第二个参数action的payload值

```js
{
    ...
    reducers:{
        first{
            start(state,action){},
            success(state,action){},
            error(state,action){},
            finish(state,action){},
        }
    }
    actions:{
        async first(){
            return {a:1,b:2}
        }
    }
    ...
}
```



