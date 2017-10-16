## simple-mode

simple-mode是无路由的小应用时使用的模式

```

const app = rab({
    //指定简单模式
    simple: true
});

//添加 model
//app.addModel(count);

//注入 根组件
app.registerRoot(({}) => <App/>);

//启动应用
app.start('#demo_container');

```



