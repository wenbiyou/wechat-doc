## XMLHttpRequest 是怎么实现的


- 回调函数
  * 将一个函数作为参数传递给另一个函数
  * 同步回调和异步回调
  * 异步回调
    * 把异步回调作为一个任务，添加到消息队列尾部
    * 把异步回调添加到为任务队列中，在当前任务的末尾出执行微任务
- 系统调用栈
  * 循环系统在执行一个任务时，都要为这个任务维护一个系统调用栈


### XMLHttpRequest运行机制
- 创建XMLHtttpRequest对象

- 为xhr对象注册回调函数

- 配置基础的请求信息

- 发送请求


### XMLHttpRequest 使用过程中的坑
- 跨域问题

- https混合内容的问题
