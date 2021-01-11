从输入URL到页面展示
- 用户输入
- URL请求过程
  * 重定向
  * 响应数据类型处理
- 准备渲染进程
  * 通常，打开新页面都会使用独单的渲染进程
  * 如果从A页面打开B页面，并且A和B都属于同一站点，B页面复用A页面的渲染进程
- 提交文档
  * 浏览器进程发出提交文档，渲染进程接收到提交文档的消息后，回合网络进程建立传输数据的管道
  * 文档数据传输完成，渲染进程返回确认提交消息给浏览器进程
  * 浏览器进程收到确认提交后，更新浏览器界面状态，包括安全状态、地址栏URL、前进后退的历史状态，并更新web页面
- 渲染进程
  一旦文档被提交，渲染进程便开始页面解析和子资源加载



## 输入url=>页面展示
1.输入url
2.浏览器进程检查url,组装协议，构成完整url
3.浏览器进程通过ipc通信将url请求发送给网络进程
4.网络进程接收url请求，检查本地缓存是否缓存了该请求资源，如果有，则将资源返回给浏览器进程
5.如果没有，网络进程向web服务器发起http请求：
  * 进行dns解析，获取ip地址和端口
  * 利用ip地址和服务器建立tcp连接
  * 构建请求头信息
  * 发送请求头信息
  * 服务器相应后，接收响应头和响应信息，解析响应内容
6.网络进程解析响应内容：
  * 检查状态码，如果是301、302则需要重定向，从Location自动读取地址进行重定向；如果是200，则继续处理请求
  * 状态码为200，检查响应类型content-type,如果是字节流类型，则将该请求提交给下载管理器，该导航结束；如果是html则浏览器进程通知渲染进程准备进行渲染。
7.准备渲染进程
  * 浏览器进程检查当前url是否和之前打开的渲染进程根域名是否相同，相同则复用原来的进程；不同，则开启新的渲染进程
8.传输数据、更新状态
  * 渲染进程准备好，浏览器向渲染进程发起 提交文档 的消息，渲染进程接收到消息和网络进程建立传输数据的管道
  * 渲染进程接收完数据后，向浏览器发送 确认提交
  * 浏览器进程接收到确认消息后更新浏览器界面状态：安全、地址栏url、前进后退的历史状态、更新web页面