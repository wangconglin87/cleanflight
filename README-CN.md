# Cleanflight

![Cleanflight](docs/assets/cleanflight/cleanflight-logo-light-wide-1-240px.jpg)

IMPORTANT NOTICE: Support for STM32F1 based flight controllers will be removed in late 2017, this includes NAZE, CC3D (original) and CJMCU like flight controllers.

重要通知：2017年底将删除对基于STM32F1的飞行控制器的支持，包括NAZE，CC3D（原始）和CJMCU等飞行控制器。

Cleanflight is flight controller software for multi-rotor and fixed wings.  The Cleanflight project, and related projects such as Betaflight and iNav are
used on the majority of flight controllers used around the world.  There is no other software used on as many flight-controllers!

Cleanflight是用于多轴旋翼机和固定翼的飞行控制器软件。Cleanflight项目以及Betaflight和iNav等相关项目被用于世界各地的大多数飞行控制器上。没有哪个软件被用于如此多的飞行控制器上！

* If you're looking for experimental new features and don't mind doing your homework, checkout the [betaflight fork](https://github.com/betaflight/betaflight).
* 如果你在寻找实验性的新功能，并愿意花费时间研究，请查看分支[betaflight fork](https://github.com/betaflight/betaflight)。
* If you're looking for advanced navigation features then check out the [iNav fork](https://github.com/iNavFlight/inav).
* 如果你在寻找高级导航功能，请查看分支[iNav fork](https://github.com/iNavFlight/inav)。
* All other users should use Cleanflight.
* 其他用户应该使用Clearflight。

## Features 特性

Features:

* Awesome flight performance as trusted by the majority of Acrobatic and Racing Drone pilots.
* 具有高性能被大多数特技和竞速无人机驾驶者所信赖。
* Support for modern STM32 based processors F1/F3/F4/F7.
* 支持F1/F3/F4/F7。
* Support for modern accelerometer/gyro/barometer/compass sensors.
* 支持加速度计、陀螺仪、气压计、罗盘。
* Support for modern ESC technologies DSHOT/ONESHOT and legacy PWM.
* 支持DSHOT、ONESHOT和PWM电调协议。
* Support for Multi-color RGB LED strip support.
* 支持彩色LED灯带。
* Advanced on-board telemetry logging (Blackbox).
* 先进的板载遥测日志记录（黑匣子）。
* Wide support of receivers (SBus/iBus/SumD/SumH/PPM/PWM/CRSF/JetiExBus)
* 广泛支持各种接收机SBus、iBus、SumD、SumH、PPM、PWM、CRSF、JetiExBus。
* Wide support of telemetry protocols (FrSky/SmartPort/S.Port/HoTT/iBus/LTM/MavLink/CRSF/SRXL).
* 广泛支持各种遥测协议FrSky、SmartPort、S.Port、HoTT、iBus、LTM、MavLink、CRSF、SRXL。
* Built-in OSD support & configuration without needing third-party OSD software/firmware/comm devices.
* 内置OSD，无需第三方支持即可使用。
* Support for external OSD slave systems.
* 支持外部OSD副系统。
* VTX support (RTC6705/Unify Pro(SmartAudio)/IRC Tramp/etc).
* VTX支持RTC6705、Unify Pro(SmartAudio)、IRC Tramp等。
* and MUCH, MUCH more.
* 等等。

## Installation & Documentation 安装及文档

* Cleanflight documentation - https://github.com/cleanflight/cleanflight/tree/master/docs
* Cleanflight文档 - https://github.com/cleanflight/cleanflight/tree/master/docs
* Betaflight Wiki -  https://github.com/betaflight/betaflight/wiki
* Betaflight百科 -  https://github.com/betaflight/betaflight/wiki

## Support

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
国内没有，不会翻墙，谁可以搞到B站上

Please subscribe and '+1' the videos if you find them useful.

## Configuration Tool 配置工具

To configure Cleanflight you should use the [Cleanflight-configurator GUI tool](https://chrome.google.com/webstore/detail/cleanflight-configurator/enacoimjcgeinfnnnpajinjgmkahmfgb) (Windows/OSX/Linux).

The source for it is here:
源码在此：

https://github.com/cleanflight/cleanflight-configurator

Note: the configurator auto-updates itself if installed using Chrome, if you need an old version to use old firmware then you can get them here:
注: 在Chrome上的配置工具会自动更新，如正用旧固件，点击链接可找到相应配置工具。

https://github.com/cleanflight/cleanflight-configurator/releases


## Contributing 添砖加瓦

Contributions are welcome and encouraged.  You can contribute in many ways:

* Documentation updates and corrections.
* 更新更正文档
* How-To guides - received help? Help others!
* 编写使用教程 - 人人为我，我为人人。
* Bug reporting & fixes.
* 报告已及修复Bug。
* New feature ideas & suggestions.
* 提交新功能及建议。

See [CONTRIBUTING.md](CONTRIBUTING.md)

## Developers

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

## Contributors 参与者

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
