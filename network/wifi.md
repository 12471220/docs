### iw
1. 查看无线网卡信息  
   `iw dev`
2. wifi扫描(可以使用|grep SSID输出简洁信息)  
   `iw dev <device name> scan |grep SSID`
3. 连接wifi  
   `iw dev <device name> connect <SSID>`
