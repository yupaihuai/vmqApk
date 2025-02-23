
V免签  —— 个人开发者收款解决方案
===============

此处为fork自原作者的修改版
主要修改增加几项功能：

1. 支持开机自启(国内定制系统需手动开启自启权限)
2. 支持post失败后再重试一次(这次重试是强制亮屏的)
3. ios设备可以找一台安卓设备-》绑定店员进行收款通知了

修改版特点：可以装在自己的日用安卓机器上，不用专门找一台机器亮屏挂机了。因为修改版支持错误重试，如果装在日用机器上推送失败，软件会强制打开一个前台Service以及一个前台Activity

前台页面的打开需要手动开启两项权限：后台弹出页面、锁屏显示

在使用过程中，可以将屏幕关闭，省电，然后在收到支付信息后，软件会自动的打开前台并推送支付信息。
软件里面的心跳本来想移除用来省电的，但基于可靠性，虽然心跳会略微增加耗电，但还是没有去除

---

经过自测，软件只要开启网络，掉单概率大幅降低。主要改进点是两项。

一：优化了里面大量的 okhttp 的访问，做成了单例,防止某些情况下可能导致的内存溢出、错误崩溃等等
二：增加了一次网络重试（没有做三次、四次是防止重复提交导致订单出问题），而且是唤起到前台的网络重试，（之所以唤起到前台，是测试过小米等机型，如果app长时间在后台（6小时以上），app会被限制网络，除非启动前台Service或者Activity

安装在主力机上，每天带机上地铁、外出游玩，4个月实测（每天达到100单）掉单数据：

原版：掉单率存在百分之5到10 (主要集中在网络较差环境中)

加入一次重试后：掉单率大概在百分之2 左右

加入五次重试后：掉单率接近千分之一 (排除手机停机断网、无信号等情况)


**以下赞助链接采用此系统搭建，您可以随时赞助测试其稳定性：**

[赞助链接](http://card.netsite.cc/p/5lle3xdfw5s8lpgqvdad)

===============


V免签 是基于SpringBoot 2.1.1/ThinkPhP5.1 实现的一套免签支付程序，主要包含以下特色：

 + JAVA、PHP双服务端，总有一款适合你服务器
 + 超简单Api使用，提供统一Api实现收款回调
 + 免费、开源

> Java版服务端地址：【 https://github.com/szvone/Vmq 】

> PHP 版服务端地址：【 https://github.com/szvone/vmqphp 】

## 前言

[赞助链接](http://card.netsite.cc/p/5lle3xdfw5s8lpgqvdad)

## 安装

 + 下载服务端程序，可选PHP/Java版，按照说明安装
 + 下载编译好的Apk,安装后扫码/手动配置 即可使用


 > 升级说明：请您直接下载新版本覆盖旧版本即可！


## 说明
 + 请部署完成后访问后台，有详细的Api说明


## 注意

  + 本系统原理为监控收款后手机的通知栏推送消息，所以请保持微信/支付宝/V免签监控端后台正常运行，且添加到内存清理白名单！

  + v免签面向用户是个人开发者，如果您不懂如何开发网站，那么v免签不适合您的使用！

  + v免签的原理是监控手机收到收款后的通知栏推送信息，所以不适合于商用多用户的情况，如果您想用于商用，请二次开发！

  + v免签是免费开源产品，所有程序均开放源代码，所以不会有收费计划，因此作者不可能教会每个人部署安装，请参考文档多百度谷歌，v免签使用具有一定的技术门槛，请见谅！

  + v免签的监控端并不适配所有手机，遇到手机无法正常使用的时候，请您更换手机或使用模拟器挂机！

  + v免签拥有双语言服务端，当您使用php版本服务端遇到问题的时候，请您尝试使用java版本服务端，php版本服务端配置略复杂，需要配置伪静态规则，请知悉！

  + 正常的安装步骤简略如下
    + 下载服务端部署(GitHub中下载的为最新版)
    + 登录网站后台更改系统设置
    + 打开网站后台监控端设置
    + 下载监控端
    + 安装监控端后使用手动配置或扫码配置
    + 监控端中点击开启服务跳转到辅助功能中开启服务
    + 开启服务后返回v免签点击检测监听权限
    + 如果显示监听权限正常，至此安装完毕，如果只收到通知栏推送的测试通知，则系统不兼容无法正常监听
    + 如果显示监听权限正常，还是无法正常运行，那么请确定微信是否关注 “微信支付”这个公众号


  + v免签支持的通知有：
    + 支付宝个人收款的推送通知
    + 支付宝商家二维码的收款推送通知
    + 支付宝店员通绑定的店员账号收款的推送通知
    + 微信二维码收款推送通知
    + 微信店员收款推送通知
    + 微信收款商业版收款推送通知
    + 微信收款商业版店员到账收款通知

## 更新记录
 + v1.8.1（2019.12.20）
    + 修复上个版本无法正常回调问题

 + v1.8（2019.12.03）
    + 修复付款人昵称如果是纯数字，支付完后台订单金额会记录成昵称的数字的问题

 + v1.7（2019.05.17）
    + 删除辅助功能依赖，改为使用通知使用权进行监听，修复一大堆bug，建议更新到该版本

 + v1.6.2（2019.05.17）
    + 增加微信收款商业版到账支持

 + v1.6.1（2019.05.17）
    + 修复微信无法正常回调的问题

 + v1.6（2019.05.16）
    + 启用新方式监听到账通知，理论支持更多设备！

 + v1.5（2019.04.24）
    + 修复部分手机扫码配置失败的问题！

 + v1.4.1（2019.04.23）
    + 修复部分手机无法正确检测监听权限问题，点击监听权限按钮后，如果一切正常，状态栏会收到推送信息，并且会提示监听权限正常！

 + v1.4（2019.04.23）
    + 修复部分手机无法正确检测监听权限问题，点击监听权限按钮后，如果一切正常，状态栏会收到推送信息，并且会提示监听权限正常！

 + v1.3（2019.04.20）
    + 添加后台心跳线程熄屏运行权限，更加稳定啦（推荐更新到此版本）

 + v1.2（2019.04.19）
    + 整理代码，重新优化APP兼容性
    + 添加店员到账支持，添加后可以实现安卓备用机/模拟器 挂小号取收款通知，方便IOS用户，
       + 微信绑定店员方式=>微信->收付款->二维码收款->收款小账本->添加店员接收通知
       + 支付宝绑定店员方式=>我的->商家服务->店员通->立即添加

 + v1.1（2019.02.25）
   + 修复安卓7.0以上系统监控App闪退问题
   + 修复监控端检测服务状态无法正确检测是否正常问题
   + 添加商家码收款回调支持，商家码收款的也能正常回调啦

 + v1.0（2019.01.31）
   + 初版发布

## 版权信息

V免签遵循 MIT License 开源协议发布，并提供免费使用，请勿用于非法用途。


版权所有Copyright © 2019 by vone (http://szvone.cn)

All rights reserved。

