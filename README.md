# mqttv3-card
日志：增加网卡绑定功能

作者： www.yandishuzi.com

YD-Digital 2022.01

软件架构
参考官方mqttv3。

安装教程
直接将源码集成入IDEA即可。
使用说明
MqttAsyncClient(String serverURI, String clientId, String bindAddress) 增加 String bindAddress参数，用于指定绑定的网络IP。当IP为全0时（0.0.0.0），内部将不绑定IP，由MQTT自动选择网络（WIFI或4G）通信。

TCPNetworkModule.java 中的public void start()函数内部实现绑定IP功能。

if("0.0.0.0" != this.bindAddress) { socket.bind(new InetSocketAddress(this.bindAddress, bindPort++)); }

并增加了端口复用功能，避免TCP连接失败。
socket.setReuseAddress(true);

参与贡献
liup
yangyd
zhangjw
http://www.yandishuzi.com
