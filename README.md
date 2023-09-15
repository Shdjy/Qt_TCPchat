# Qt_TCPchat

基于Qt的多线程TCP通讯软件

使用Qt实现的一个支持多客户端链接的多线程TCP服务器及其客户端。
通讯设计：用户通过客户端发送自己的昵称，服务器进行认证注册；用户输入发送的目标，点击发送，服务器转发消息到相应的用户。
客户端：客户端的网络实现，使用QTcpSocket。实现其readyRead()，connected()，disconnected()信号的处理
服务器：服务器设计为控制台应用，MyTcpServer作为服务器主要的调度，接受新的链接、注册名称、转发消息
        重写TCPServer的incomingConnection(qintptr handle)方法，创建ChatBusiness业务对象，并移入子线程启动
        ChatBusiness创建对应的MyTcpSocket套接字与客户端连接
        实现自己的MyTcpSocket使其之间内部就可以处理消息的发送，转发系统请求到ChatBusiness

