---
layout: post
title: 校园网如何使用路由器   
date: 2018-06-06 18:32:24.000000000 +09:00
---



> * 这是一篇教你如何在校园网使用路由器给自己开热点的方法
> * 此文章主要针对于学校使用netkeeper（创翼）软件拨号上网的学校，重庆地区亲测可用，其他地区自己测试！
> * 自己测试可以用，可以做到配置好之后，只需要电脑开创翼拨号，路由器就可以捕捉账号，并联网。
> * 如果拨号失败，会自动关闭pppoe拨号。
#### 源代码以及方法在[github这里](https://github.com/miao1007/Openwrt-NetKeeper/tree/master/netkeeper4-use-pppoer-server)
#### 如何刷openwrt固件在此便不再过多讲述
## 首先点击[这里](https://pan.baidu.com/s/1JO3vDMLgd8ifv3hF7p8quQ)(密码：q5iz)下载所需要的文件
```
链接：https://pan.baidu.com/s/1JO3vDMLgd8ifv3hF7p8quQ 密码：q5iz
```

## 一、使用方法
### （一）路由器端
#### 1.使用winscp将netkeeper文件夹下所有文件拷入openwrt的/root/目录。
#### 2.安装pppoe服务端
安装自己路由器对应版本的ipk(这里以我的路由器为例)。
方法一(路由器可以上网)：
```sh
opkg update
opkg install rp-pppoe-server
```

方法二(路由器无法上网，自行下载对应ipk)：

ipk下载
可以在路由器里运行
```
opkg update
```
一般会返回类似网址，去网址里找对应的ipk包
```
Downloading http://downloads.openwrt.org.cn/PandoraBox/ralink/packages/routing/Packages.gz.
```
下载好对应的ipk包之后，在winscp运行以下代码（这里以phicomm-k2对应的包为例）
```sh
opkg install rp-pppoe-common_3.11-1_mipsel_24kec_dsp.ipk
opkg install rp-pppoe-server_3.11-1_mipsel_24kec_dsp.ipk
```
#### 3.运行nk4conf.sh。
```sh
sh nk4conf.sh
```

---------------------------
### （二）电脑端

1.网线接路由器lan口

2.netkeeper输入账号密码拨号，会提示691错误，如果错误代码不是691，就肯定失败了，首先检查网线连接是否正确，然后重启路由器，再次拨号，如果提示错误代码691，关闭netkeeper。

3.这个时候路由器会截取真实账号，并进行拨号

4.然后你就会发现，可以上网了。

5.自己进入路由器后台设置wifi以及其他需要的服务。

----------------------------------------------------------

### 最后再给大家分享一个已经打包好的[固件](https://pan.baidu.com/s/1S1MrkGNKhJaAcDITGnEe1g)（密码：ycn8），刷好之后直接使用路由器，然后路由器就会截取真实账号进行拨号，而且里面有超多的插件可以使用。不过首先你的路由器是斐讯k2才能用哈。
```
连接：https://pan.baidu.com/s/1S1MrkGNKhJaAcDITGnEe1g  密码：ycn8
```
### 或者可以下载这个，这使我们学校另外一个大佬分享出来的斐讯K2官改固件。
```
连接：https://pan.baidu.com/s/1SlVTyyoy5PhYMyYFS_g8hw
```

----

## 注意事项
> * (一)、用路由器拨号以后出现的错误代码必须为691，其他的都连不上网。
> * (二)、运行最后一步代码可能会报错，不用管。
> * (三)、由于netkeeper心跳算法更新，所以断网之后第二天需要重新拨号。
> * (四)、电脑连接路由器的wifi，再拨号，路由器同样的可以拦截账号上网，不必非要连网线。


