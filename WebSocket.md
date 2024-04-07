## WebSocket

### 1.与http的区别

1. http是无状态的协议，每次请求都需要重新建立连接，websocket建立一次连接后一直保持长连接
2. websockt是全双工的，而http为单工，只能客户端发起请求，服务器响应数据
3. 标识头不同

### 2.连接过程

1. tcp三次握手连接

2. 客户端发送一个get请求，请求头包含upgrade和connection字段，指定协议升级和建立连接，以及一个随机的sec-websocket-key字段

3. 服务器收到请求后，验证请求头，并返回握手响应，响应头包括upgrade和connection字段，对sec-websocket-key加密后产生的sec-websocket-accept字段
4. 客户端验证sec-websocket-accept字段，连接建立

### 3.事件

1. open：建立连接
2. close：关闭连接
3. error：连接建立时发生
4. message：收到消息时发生

### 4.如何保持长连接

采用心跳机制，双发收发ping，以确保连接依然存在

### 5.连接断开怎么处理

主要和前端相关，监听onclose事件，重连，采用二进制指数退避算法规避拥塞