OpenWrt LuCI for CDNS
===
forked from https://github.com/ghostry/openwrt-gmod/tree/master/luci/luci-app-cdns 为方便OpenWrt SDK编译而设立的repo

简介
---

本软件包是 [OpenWrt-CDNS][1] 的 LuCI 控制界面,已在[该固件][O]中应用。

支持自定义上游DNS请求端口

支持自动修改dnsmasq全局设置

依赖
---

软件包显式依赖`cdns`

配置
---

软件包的配置文件路径: `/etc/config/cdns` 默认使用8.8.4.4和8.8.8.8 端口53为上游DNS服务器，经测试可达到无污染的效果。


编译
---

从 OpenWrt 的 [SDK][openwrt-sdk] 编译  
```bash
# 解压下载好的 SDK
tar xjf OpenWrt-SDK-ar71xx-for-linux-x86_64-gcc-4.8-linaro_uClibc-0.9.33.2.tar.bz2
cd OpenWrt-SDK-ar71xx-*
# Clone 项目
git clone https://github.com/AlexZhuo/luci-app-cdns.git package/luci-app-cdns
# 编译 po2lmo (如果有po2lmo可跳过)
pushd package/luci-app-cdns/tools/po2lmo
make && sudo make install
popd
# 选择要编译的包Gmod -> LuCI -> luci-app-cdns
make menuconfig
# 开始编译
make package/luci-app-cdns/compile V=99
```
[O]: http://www.right.com.cn/forum/thread-198649-1-1.html
[1]: https://github.com/AlexZhuo/openwrt-cdns
[2]: https://github.com/AlexZhuo/openwrt-cdns
[openwrt-sdk]: https://wiki.openwrt.org/doc/howto/obtain.firmware.sdk
