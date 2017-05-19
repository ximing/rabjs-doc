actions是model中处理业务逻辑的地方，本质就是一个async的function

```
{
    namespace:'test',
    ...
    actions:{
        async hello(args){

        },
        //3.2.0 以上支持 异步中间件
        hi:(args)=>async ({getState,dispatch,put,call})=>{
            
        }
    }
    ...
}
```

业务中可以用以下四种方式调用

##### 1 直接dispatch action方法

```
dispatch(model.actions.hello(a,b,c,d))
//对应actions为
async hello(a,b,c,d){
}
```

##### 2 put方式，通过namespace.actionName 的方式

```
import {put} from 'rabjs';
put({type:'test.hello',payload:{a:1}});
async hello({a}){
}
```

缺点只能传一个Object \(payload\)作为参数

##### 3 call方式，通过namespace.actionName 的方式

```
import {call} from 'rabjs';
call('namespace.hello',a,b,c,d);
//对应actions 为
async hello(a,b,c,d){
}
```



