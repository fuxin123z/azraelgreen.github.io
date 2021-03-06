---
layout: post
title: 电脑自动开机的五种方法
date: 2017-05-08
categories: blog
tags: [operations]
description: 电脑自动开机的五种方法
---

### 方法一：设置定时开机

主板上有实时时钟(Real Time Clock，RTC)负责系统的计时，我们可以通过RTC指定开机的时间，就像闹钟一样。

不过，由于这项功能很少被人使用，部分虽然提供了此功能的主板 (如INTEL原装主板)其实并不能在指定时间开机，所以用户在正式使用前最好先进行测试。

#### 具体操作方式为：

1. 电脑开机之后根据屏幕上的提示信息按“`Del`”键进入主板BIOS设置画面，与定时开机有关的设置功能一般放在“`Power Management Setup`”选项下。

2. 在BIOS中有一项“`RTC Alarm Poweron`”的选项，应设成“`Enabled`”(启用)。之后用户可以具体设好定时开机的日期、小时、分钟、秒钟。

3. 为了保证电脑准确无误地实现定时自动开机的功能，用户还要先检查一下主板BIOS中的系统时间是否与现实时间相同。

4. 最后一步要记得将主板BIOS中的设置修改结果进行保存，即可在预设的时间定时开机。某些主板上还能够设成每日同一时间从BIOS自动开机，方法是将“`RTC Alarm Date`”一项改为“`Every Day`”。

不过要提示大家一点，如果利用BIOS自动开机的话，用户的Windows操作系统中只能使用一个帐户，否则不可能实现自动开机再自动登录Windows。

### 方法二：利用键盘/鼠标开机

如果电脑机箱放置在难以触及的地方，使用键盘/鼠标开机是一个不错的方案。但要注意的是此功能只支持以PS/2接口连接的键盘和鼠标，使用 USB接口连接则不行。

启用主板BIOS中“`Power On By PS/2 Keyboard`”的选项，就可以选择不同的开机热键，如Ctrl+E是最常见的开机热键。

或者选“`Power Key`”一项后，可用键盘上单独设计的一个电源键开机，但前提是只有部分符合Keyboard 98技术规格的键盘才支持此功能。当然，机箱上的电源按钮仍然能够使用。

至于用鼠标开机也很简单，在BIOS中的设置选项与键盘开机设置类似，然后只须轻点鼠标按钮就能启动电脑。

### 方法三：利用网络唤醒开机

要使用Wake On LAN (WOL)网络唤醒功能，需要网卡支持，而具备WOL功能的网卡都有一条特殊的信号线连接主板上的WOL接口，负责将开机信号传送至主板。不过，目前具备WOL接口的主板已经不多，厂商改为在主板内置的网络芯片上提供WOL功能。

WOL的原理是电脑在开机时或S5休眠模式(Suspend to Disk，休眠到硬盘)下，网卡仍以极低电压维持基本运作，这时在网络上的其他电脑便可通过软件传送一个称为“`Magic Packet`”的神奇封包至要唤醒的电脑。网卡接收信号后就会发出开机信号至主板，使主板启动。

由于电脑在唤醒前仍处于开机状态，因此我们要知道网卡的 MAC 地址(每张网卡均有自己独特的 MAC 地址，软件以此进行识别)。

#### 网络唤醒功能的具体使用方法如下：

首先在主板BIOS中打开WOL选项。注意部份主板只支持从S5模式中唤醒(Wake On LAN from S5)。

其次，从网上下载WOL软件。这个名为“Magic packet”的网络唤醒软件，其设置和使用方法都很简单。运行后在其操作界面中只有5个选项。

其中：

网卡的“(MAC Address)(MAC地址)”一栏，用户可在Windows操作系统的命令行模式下输入“`ipconfig/all`”的指令来获得。

另外， “Internet Address”(互联网地址)一栏是要进行广播的栏目，在此栏及“Subnet Mask”一栏中输入“255、255、255、255”则可进行本地广播(Local Broadcast)。

第四栏为“Send Options”，应选择“Local Subnet”。

第五栏“Remote Port Number”则随意输入。注意，上述设置只针对本地网络(Local LAN)而言。如要经互联网进行唤醒则涉及更多的问题，在此不作讨论。

最后单击界面下方的“Wake Me UP”按钮即可实现从网络唤醒电脑。

### 方法四：用电视卡开机

具备自动开机功能的电视卡已经大量面市，将其连接好后，利用电视卡提供的软件设置开机时间即可。

电视卡的自动开机方式大致可以分为二种方式：

第一种是真正具备自动开机功能的产品，需先将机箱电源线与电视卡连接再转接出;

另一种是利用休眠方式开机的电视卡。

其中，第二种方法由于电脑并未真正关机，即仍在消耗电力，所以并不是所有用户都乐意采用。

#### 下面主要介绍第一种自动开机方法的具体操作。

1. 首先，用户在安装时要将机箱上电脑开关按钮的引线接脚与电视卡的“Power Switch”接脚相连接(笔者以康博X800电视卡为例)。

2. 之后再将电视卡的另一组“Power Switch”接脚与主板上的电源接脚连接，最后把电视卡装进主板的PCI扩展槽中，这样内部连接就完成了。

3. 安装好硬件后，电视卡的配套软件(如康博PVR2)也需要进行设置。主要是在“预约录像设置”功能方面，用户应勾选“启用自动开机功能”一项。

4. 如果你电脑中的Windows操作系统超过一个用户使用的话，还要设为“启用自动登录”模式，并输入用户名称和密码，即可完成整个设置步骤。

### 方法五：意外断电后重新来电时自动开机

在主板BIOS中有一个“`Power Management Setup（电源管理设置）`”中，有个“`POWER ON AFTER PWFAIL`”或“`pwron after pw-fail`”设置项。其选项有三，分别为“On（开机）”、“Off（关机）”和“Former-Sts（恢复到到断电前状态）”。

将此选项设置为 “On”，当你的电脑意外断电后重新接通电源时电脑就会自动开机。

根据BIOS版本和主板的不同，此项设置也会有所不同，具体请参见主板说明书。

但建议大家最好还是将此选项设置为“Off”，不要用此功能自动开机。

因为这种功能极其不稳定，所以它很可能导致在正常断电情况下，一接通电源电脑就自动开机；或是打开插线板开关时，也有可能会使电脑自动开机。因此对主板会有所损害。