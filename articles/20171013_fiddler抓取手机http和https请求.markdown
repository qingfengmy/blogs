### 1. fiddler抓取手机http请求
fiddler默认只抓取电脑的http请求，如果要支持抓取手机的http，需要设置。
```
// fiddler客户端设置
Tools->Options->Connections->Allow remote computers to connect
```
```
// 查看本机ip地址
ipconfig
```
```
// 手机wifi
高级设置->手动代理->ip地址(填上面查到的地址)->端口号(8888)->IP(DHCP)
```
这样应该就可以抓取手机的http请求了。
> 注意：有时需要重启fiddler才能生效。

### 2. fiddler抓取手机https请求
#### 2.1 下载并安装Fiddler证书生成器。（注：Fiddler 证书生成器只能在 Vista 以上系统运行）
下载地址：http://www.telerik.com/docs/default-source/fiddler/addons/fiddlercertmaker.exe?sfvrsn=2
> 注意：fiddler的版本必须是4.6.3 or 4.6.20176以上，版本低的话fiddler证书生成器或直接退出
#### 2.2 生成证书
运行fiddler，运行证书生成器，然后在fidder端设置。
```
Tools->Options->Https->Capture Https Connects->Decrypt Https traffic
```
此时会弹出证书生成的提示，点击next，一直到完成。
#### 2.3 保存证书
重启fiddler
```
Tools->Options->Action->Export Root Certificate to DeskTop
```
这样就把证书导到了桌面。
#### 2.4 手机安装证书
```
// 方式1
拷到手机上，点击安装。
```
```
// 方式2
手机设置代理后，浏览器访问http://ip地址:8888，然后点击下载证书
```
#### 2.5 访问https
https页面有个select，其四种值的意义如下：
```
from all processes : 抓取所有的 https 程序, 包括 本机 和 手机 
from browsers only : 只抓取浏览器中的 https 请求 
from non-browsers only : 只抓取除了浏览器之外的所有 https 请求 
from remote clients only ： 抓取远程的客户端的 https ,可以代表手机
```
> 手机->设置->安全->受信任的凭据(这里可查看手机信任的证书)
### 3. 参考文章
[如何用Fiddler对Android应用进行抓包](http://jingyan.baidu.com/article/03b2f78c7b6bb05ea237aed2.html)

[使用Fiddler工具抓取手机HTTP和HTTPS包](http://blog.csdn.net/bingyu880101/article/details/52223783)

[Fiddler抓包使用教程-Https](http://blog.csdn.net/zhaoyanjun6/article/details/72956016)
