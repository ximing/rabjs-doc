model是rabjs的核心模块，负责处理所有的领域模型，封装了state，actions，reducers，subscriptions四个概念。

#### 1，创建model

```js
import {createModel} from 'rabjs';
export default createModel({
    namespace:'test',
    state:{
        todos:[]
    },
    reduers:{
    }，
    actions:{
    },
    reduers:{

    },
    subscriptions:{
        init({history, dispatch}){
            history.listen((location) => {
                console.log('init------------>',location)
            })
        },
        test({history, dispatch}){
            websocket.on('create',function(){})
        }
    }
})
```



