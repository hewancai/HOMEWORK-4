## nslookup  www.whu.edu.cn
![](pic/1-1.png)
## P23
![](pic/2-1.png)</br>
<p>
a.向每个对等方以u<sub>s</sub>/N的速率传输，同样的传输速率下每个对等方同时收到完整文件，时间为NF/u<sub>s</sub></br>
b.向d<sub>min</sub>的对等方以d<sub>min</sub>的速率传输，其他对等方的传输速率大于d<sub>min</sub>，d<sub>min</sub>的对等方时间为F/d<sub>min</sub>,其他对等方时间小于F/d<sub>min</sub></br>
c.结合a和b，如果u<sub>s</sub>/N≤d<sub>min</sub>时NF/u<sub>s</sub>≥F/d<sub>min</sub>,此时选择a的方案；如果u<sub>s</sub>/N>d<sub>min</sub>时NF/u<sub>s</sub><<F/d<sub>min</sub>,此时选择b的方案。</br>
</p>

## P25
![](pic/2-2.png)
<p>
共N个节点，N(N-1)/2条边
</p>

## P28
![](pic/2-3.png)
<p>
a.先运行TCPClient时，客户端无法与服务器端的程序建立连接，无法进行TCP连接，运行出错。</br>
b.UDPClient无需握手，程序正常运行。</br>
c.若干使用不同的端口，则客户端将尝试建立TCP连接，可能连接错误或不存在的进程，出现错误。</br>
</p>

 <p align="right">刘涛<br/>2017302580292<br/>2020.03.23</p>