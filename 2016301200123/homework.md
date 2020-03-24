# 第二章

## 课件作业 nslookup

参考Mircrosoft提供的文档可知，nslookup显示可用于诊断域名系统（DNS）基础结构的信息。 使用此工具之前，应熟悉 DNS 的工作原理。 只有安装了 TCP/IP 协议，才能使用 nslookup 命令行工具。

```powershell
nslookup www.whu.edu.cn
```

执行上述指令得：

<img src="static\nslookup.png" alt="nslookup_result"/>

## 课本练习题

### P12

编写TCPServer.py如下：

```python
from socket import socket, AF_INET, SOCK_STREAM


HOST = ""
PORT = 18080
BUFSIZ = 2048
MAX_CLIENTS = 1

server_socket = socket(AF_INET, SOCK_STREAM)
server_socket.bind((HOST, PORT))

print("Service is starting...")

server_socket.listen(MAX_CLIENTS)

while True:

    client_socket, client_addr = server_socket.accept()
    print("Connected with {}".format(client_addr))

    while True:

        message = str(client_socket.recv(BUFSIZ), "utf-8")

        if message != None and message != "":
            print(message)
        else:
            client_socket.close()
            print("Disconnected with {}".format(client_addr))
            break

server_socket.close()
```

运行该程序于PC，同时配置局域网下的另一台设备（树莓派）的浏览器代理服务器：

<img src="static\proxy_setting.png" alt="proxy_setting"/>

在树莓派端访问http://whu.edu.cn?method=GET：

<img src="static\sending_GET.png" alt="sending_GET"/>

在PC端的TCPServer.py打印结果如下：

<img src="static\result_received.png" alt="result_received"/>

### P13

经过实验发现：“MAIL FROM”向服务器指明了邮件的发送者，需要有意义的邮箱地址，而“From：”只决定邮件显示时接收方的信息，对邮件发送过程无影响，理论上可以为任意字符串。

### P22

A. 客户-服务器分发：

分发 *F* 到 *N* 客户时客户-服务器大约需要的时间：

<img src='http://latex.codecogs.com/gif.latex?D_{c-s} \geq max\{NF/u_s, F/d_{min}\}' alt="D_{c-s} \geq max\{NF/u_s, F/d_{min}\}">

其中<img src='http://latex.codecogs.com/gif.latex?d_{min}' alt="d_{min}">=<img src='http://latex.codecogs.com/gif.latex?d_{i}' alt="d_{i}">=2Mbps。

值得注意的是，15Gb = 15 * 1024 Mb。

基于此，对于N和u的每种组合的最小分发时间的图表如下（second）：

| N\u  | 300kbps | 700kbps | 2Mbps  |
| ---- | ------- | ------- | ------ |
| 10   | 7680    | 7680    | 7680   |
| 100  | 51200   | 51200   | 51200  |
| 1000 | 512000  | 512000  | 512000 |

B. P2P分布：

分发 *F* 到 *N* 客户时P2P 大约需要的时间：

<img src='http://latex.codecogs.com/gif.latex?D_{P2P} \geq max\{F/u_s, F/d_{min},NF/(u_s + \sum{u_i})\}' alt="D_{P2P} \geq max\{F/u_s, F/d_{min},NF/(u_s + \sum{u_i})\}">

其中<img src='http://latex.codecogs.com/gif.latex?d_{min}' alt="d_{min}">=<img src='http://latex.codecogs.com/gif.latex?d_{i}' alt="d_{i}">=2Mbps。

值得注意的是，1Mbps = 1 * 1024 kbps。

基于此，对于N和u的每种组合的最小分发时间的图表如下（second）：

| N\u  | 300kbps  | 700kbps  | 2Mbps  |
| ---- | -------- | -------- | ------ |
| 10   | 7680.0   | 7680.0   | 7680.0 |
| 100  | 25903.56 | 15616.20 | 7680.0 |
| 1000 | 47558.78 | 21524.85 | 7680.0 |

