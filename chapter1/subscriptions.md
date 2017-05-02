subscriptions可以做针对当前model的history，websocket，service worker等相关的操作

#### 1，基础语法

```
{
    ...
    subscriptions:{
        init({history, dispatch}){
            history.listen((location) => {
                console.log('init------------>',location)
            })
        }
    }
    ...
}


```



