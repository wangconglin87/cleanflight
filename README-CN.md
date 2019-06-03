# Cleanflight

![Cleanflight](docs/assets/cleanflight/cleanflight-logo-light-wide-1-240px.jpg)

重要通知：2017年底将删除基于STM32F1的飞行控制器的支持，包括NAZE，CC3D（原始）和CJMCU等飞行控制器。

Cleanflight是用于多轴旋翼机和固定翼的飞行控制器软件。

在世界各地，Cleanflight、Betaflight和iNav项目广泛用于各种飞行控制器上。

* 如果你在寻找实验性的新功能，并愿意花费时间研究，请查看分支[betaflight fork](https://github.com/betaflight/betaflight)。
* 如果你在寻找高级导航功能，请查看分支[iNav fork](https://github.com/iNavFlight/inav)。
* 其他用户应该使用Clearflight。

## Features 特性

* 支持F1/F3/F4/F7。
* 支持加速度计、陀螺仪、气压计、罗盘。
* 支持DSHOT、ONESHOT和PWM电调协议。
* 支持彩色LED灯带。
* 板载黑匣子。
* 接收机SBus、iBus、SumD、SumH、PPM、PWM、CRSF、JetiExBus。
* 日志协议FrSky、SmartPort、S.Port、HoTT、iBus、LTM、MavLink、CRSF、SRXL。
* 内置OSD。
* 支持外部OSD。
* VTX支持RTC6705、Unify Pro(SmartAudio)、IRC Tramp。

## 安装及文档

* Cleanflight文档 - https://github.com/cleanflight/cleanflight/tree/master/docs
* Betaflight百科 -  https://github.com/betaflight/betaflight/wiki

## 支持

Your first place for support are the [Cleanflight forums on RCGroups](https://www.rcgroups.com/forums/showthread.php?2249574-Cleanflight-firmware-for-STM32F3-based-FCBs-Check-First-Post-Please!!)

The Github issue tracker is NOT for end-user support.

## IRC Support and Developers Channel

There's a dedicated Cleanflight IRC channel on the Freenode IRC network. Many users and some of the developers frequent there, and it is a helpful and friendly community - but there are two important things to keep in mind: First and most importantly, please go ahead and ask if you have questions, but **make sure you wait around long enough for a reply**. Next, sometimes people are out flying, asleep or at work and can't answer immediately, even though they are present in the channel. This is how IRC works: Many people stay logged in, even though they are not actively participating in the discussion all the time. Have a seat, grab a drink and hang around if it's a quiet time of day.

irc://irc.freenode.net/#cleanflight

If you are using Windows and don't have an IRC client installed, take a look at [HydraIRC](http://hydrairc.com/).

There's a dedicated Slack chat channel for betaflight here:

https://slack.betaflight.com/

Etiquette: Don't ask to ask and please wait around long enough for a reply - sometimes people are out flying, asleep or at work and can't answer immediately.

## Videos

There is a dedicated Cleanflight YouTube channel which has progress update videos, flight demonstrations, instructions and other related videos.

https://www.youtube.com/playlist?list=PL6H1fAj_XUNVBEcp8vbMH2DrllZAGWkt8

国内没有，不会翻墙，谁可以搞到B站上？

Please subscribe and '+1' the videos if you find them useful.

## 配置工具

To configure Cleanflight you should use the [Cleanflight-configurator GUI tool](https://chrome.google.com/webstore/detail/cleanflight-configurator/enacoimjcgeinfnnnpajinjgmkahmfgb) (Windows/OSX/Linux).

源码在此：

https://github.com/cleanflight/cleanflight-configurator

注: 在Chrome上的配置工具会自动更新，如正用旧固件，点击链接可找到相应配置工具。

https://github.com/cleanflight/cleanflight-configurator/releases


## 添砖加瓦

* 更新更正文档
* 编写使用教程 - 人人为我，我为人人。
* 报告已及修复Bug。
* 提交新功能及建议。

查看 [CONTRIBUTING.md](CONTRIBUTING.md)

## 开发用相关文档

Please refer to the development section in the [docs/development](https://github.com/cleanflight/cleanflight/tree/master/docs/development) folder.

TravisCI is used to run automatic builds: https://travis-ci.org/cleanflight/cleanflight

https://travis-ci.org/cleanflight/cleanflight

[![Build Status](https://travis-ci.org/cleanflight/cleanflight.svg?branch=master)](https://travis-ci.org/cleanflight/cleanflight)

## Cleanflight Releases
https://github.com/cleanflight/cleanflight/releases

## Open Source

Cleanflight is software that is **open source** and is available free of charge without warranty to all users.

The license is GPL3.

## Project/Fork History

Cleanflight is forked from Baseflight, which is now dead, all primary development happens in Cleanflight, betaflight and iNav forks.

Cleanflight v2.x -> betaflight -> cleanflight v1.x -> baseflight -> multiwii

## 参与者

Thanks goes to all those whom have contributed to Cleanflight and its origins.

Primary developers:
* Dominic Clifton (hydra) - *cleanflight founder*
* Boris B (borisbstyle) - *betaflight founder*
* digitalentity - *inav founder*
* Martin Budden (martinbudden)
* Jason Blackman (blckmn)

Big thanks to current and past contributors:
* **Alexinparis** (for MultiWii),
* **timecop** (for Baseflight),
* **Sambas** (for the original STM32F4 port).
* Bardwell, Joshua (joshuabardwell)
* ctzsnooze
* Höglund, Anders (andershoglund)
* Ledvina, Petr (ledvinap) - **IO code awesomeness!**
* kc10kevin
* Keeble, Gary (MadmanK)
* Keller, Michael (mikeller) - **Configurator brilliance**
* Kravcov, Albert (skaman82) - **Configurator brilliance**
* MJ666
* Nathan (nathantsoi)
* ravnav
* sambas - **bringing us the F4**
* savaga
* Stålheim, Anton (KiteAnton)
* prodrone - **failsafe work**
* **ctn** - **for the original Configurator**

And many many others who haven't been mentioned....
