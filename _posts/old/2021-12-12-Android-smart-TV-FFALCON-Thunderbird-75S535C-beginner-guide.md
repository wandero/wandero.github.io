---
id: 1081
title: '安卓智能电视（FFALCON 雷鸟 75S535C）简易使用指南'
date: '2021-12-12T21:21:15+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1081'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/21/211212%20%E5%AE%89%E5%8D%93%E6%99%BA%E8%83%BD%E7%94%B5%E8%A7%86%EF%BC%88%E9%9B%B7%E9%B8%9F%2075S535C%EF%BC%89%E7%AE%80%E6%98%93%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '7'
categories:
    - 工具二三
---

年中因为疫情准备换款大电视，基于预算选择了雷鸟 FFALCON 75S535C，（买完一周就因为疫情远程工作了大半个月，电影、刷剧、Switch、Xbox 使用充分……），使用几个月下来还算满意，折腾经验如下：

<!-- more -->

## 安装 ADB 环境

（大多智能电视都对安装应用进行了限制，需要安装 ADB 环境设置）

### PC 端安装 ADB 环境

#### 下载 ADB 程序包

推荐 [Google 官方工具包](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)

#### 配置环境变量

解压文件夹，例如至 `C:\cloudlet.info\platform-tools`

CMD 运行 `SETX PATH "%PATH%;C:\[cloudlet.info](http://cloudlet.info)\platform-tools" /M`

可在 CMD 中运行 adb （输入 adb 回车） 验证是否配置成功

#### TV 端开启 ADB 调试开关

进入 设置 &gt; 系统 &gt; 系统信息 页面，

遥控器依次按下"上"、"下"、"左"、"右"

（页面中弹出 ADB 开关）设置 ADB 为开启状态

## 开启安装第三方应用权限

（确保 PC 和 TV 在同一局域网，为之后方便，可在路由器中将 TV 绑定固定 ip）

（PC 端 ） CMD 运行 `adb connect 192.168.5.35` （电视 IP 地址）

（TV 端）弹出允许 USB 调试开关 – 勾选一律允许使用这台计算机调试-确定（如果这里没有弹出提示，重启电视，多试几次）

（PC 端）显示 `already connected to 192.168.5.35:5555` （表示连接成功）

某些时候会提示 devices offline 的提示，需要依次运行 `adb kill-server` 、`adb start-server` 重启 adb 服务，如果仍然不行可以考虑重启 PC 和 TV

（PC 端 ） CMD 依次运行

`adb shell setprop persist.tcl.debug.installapk 1`

`adb shell setprop persist.tcl.installapk.enable 1`

开启安装第三方应用权限

## 安装应用

### adb 远程安装

（在 PC 成功连接 TV 后）adb install可在 PC 端为 TV 安装应用，如

`adb install C:\cloudlet.infodemo.apk` (完整文件名可通过将文件拖拽至 CMD 窗口生成）

### 电视端 apk 安装

（需要注意雷鸟电视禁止安装第三方桌面，也无法设置第三方应用自启动）

可以安装当贝市场，里面有些电视上的主流应用，但不少应用安装后无法运行。这里要提的是当贝助手的屏幕检测功能，可以在收货验机时比较方便全面的检查屏幕。

## 卸载和恢复预装应用

（卸载内置乐博投屏）

`adb shell pm uninstall --user 0 com.tcl.MultiScreenInteraction_TV`

恢复预装应用（未验证）

`adb shell cmd package install-existing com.tcl.MultiScreenInteraction_TV`

## ADB 往 TV 端传送文件

### 上传文件

`adb push d:\cloudlet.info\advancedsettings.xml /sdcard/Android/data/org.xbmc.kodi/files/.kodi/userdata`

### 下载文件

adb pull `/sdcard/Android/data/org.xbmc.kodi/files/.kodi/userdata/advancedsettings.xml d:cloudlet.info`

### 手动浏览文件结构

不清楚文件具体路径可以在PC 端 CMD 运行 `adb shell` 进入 shell 模式（会显示 tcl\_m7642:/ $ 类字样），之后通过 ls （显示当前路径所有文件夹）`cd cloudlet.info`（进入 cloudlet.info 文件夹）手动浏览文件结构，当然也可以为电视端安装 ES 文件浏览器等资源管理器，建立专门的 web 文件传送页面

## 其他

### 投屏

网上流传的替换无广告版乐播经验证已失效，这样默认的乐播虽然有广告但支持开机自启动，就没有替换必要了，可以在不打开「多屏互动」（乐播）的情况下使用 iPhone 或者安卓机投屏。

如果需要电脑投屏到电视，可以考虑幕享等其他免费投屏方案（乐播 PC 端收费），WIN 10 的无线投屏也可以尝试，但不能解决声音问题。

### 听歌

电视端的音乐应用都比较糟糕，而且似乎都不能防烧屏，但是系统自带的蓝牙单独听很不错，手机蓝牙连上电视，手机播放随意 APP 的音乐就可以了。电视音箱好歹也有 34W ，比手机的效果那还是要强很多的，动态画面能防烧屏，还可以进入智能音箱模式关闭画面。

### 开启 HDMI 信号源的 4K 模式

信号源下 设置 – 系统 – 通用设置 – （开启）HDMI 高级标准

### 主页显示近期使用应用列表

长按 HOME 键弹出，这个功能非常方便，避开了默认系统打开应用的繁琐操作（但好像没有什么地方提，还是偶然发现的）

### 电视卫士

家长设置 系统自带的可以设置时间和应用限制（但密码限制居然可以用忘记密码然后做算术题来绕开……明码密码不大方便，跟官方建议使用遥控器的方向键做隐藏输入也被无视了……）

应用管理 – 应用权限 – 后台运行权限 – Kodi（这个功能固件更新后好像取消了）

### 禁止开机播放视频

在主页时按菜单键-桌面设置-关闭个性化推荐

### 追评

就硬件来说，这个价位的雷鸟还是不错的，屏幕还行（见的不多识的不广），2160p（4K） x265 10bit HDR（这里有点没搞清楚） 硬解流畅，一般应用的话不用考虑电视盒子。

就固件（软件）来说，那是一言难尽……官方根本没搞清楚自己的市场定位，老是搞些增加不了什么收益又破坏用户体验的幺蛾子，又想当又想立还没魄力……技术实力也不行，搞封闭系统又解决不了问题，更新个固件不是这里出点问题就是那里出点问题，甚至老的问题没解决新的问题又来了（问题都不大，但这套操作实在是一塌糊涂），当然，电视也就这个价位，实在受不了接个盒子也能绕开绝大多数问题，也就发发牢骚吧……