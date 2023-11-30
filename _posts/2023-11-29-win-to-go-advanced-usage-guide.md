---
layout: post
title: "Win To Go 进阶使用技巧"
date: 2023-11-29 21:00:00 +0800
categories: 工具二三
tags:
    - WTG
---



首先澄清一个甚至在 luobotou 论坛都似乎普遍认可的误区，Win To Go 完全可以正常升级，直接使用论坛 WTG 辅助工具 默认设置部署，系统顺利运行半年

接下来，Win To Go 面临的最大的两个问题无疑是稳定性不足和设备掉速，而这两个问题都有同一个解决方案——日常备份

<!-- more -->

## 备份还原

稳定性不足就不说了，这个问题导致了即便在 WTG 方面非常专业的  luobotou 论坛也盛行各种玄学，如开头提到的 WTG 不应升级系统的误区。如果没有日常备份，设备掉速也是一个大问题，掉速了就需要格式化固态优盘，及时可靠的备份还原方案就是 WTG 流畅使用的必需了。

第一次部署的 WTG 在用到三四个月的时候出现掉速问题（很可能已经开始一段时间了），表现是开关机缓慢、程序卡顿、复制文件速度崩溃，当时还没有意识到，一直以为 300g 的分区备份耗时8个小时是正常现象……直到格式化优盘后 140G 的分区备份十分钟完成……

至于备份工具，虽然 WTG辅助工具（实际使用多次出现报错文件被占用，无法解决）和 Dism++ 都支持热备份，但功能都相对简单，推荐傲梅轻松备份，支持周期自动增量备份（免费版够用，收费版支持差异备份，容错程度高一些，但非必须）

另外有一个细节，系统备份的时候会备份两个分区，所以还原的时候注意要选则系统分区还原。

## 分区方案

能够周期备份以后，WTG 分一个区还是两个区都行，基于减少硬盘读写的考虑（读写到一定程度就会掉速，需要格式化重来），我选择了分两个区的方案，C 盘用傲梅每天差异备份，D 盘用 GoodSync 每天同步备份。这样 C 盘 30 天一个周期的差异备份，完全备份 80G，每天的更新文件 15G，D 盘的变化似乎可以忽略。如果不分区，D 盘的 200G 文件至少每次完全备份的时候就要读写一遍……

同样是基于减少硬盘读写的考虑，可以把 系统 Users 文件夹中的可以调整位置的一些大文件夹（比如文档、微信一类的）设置到 D 盘，但是不建议修改 Users 本身位置

## 休眠问题

这里又是一个误区，WTG 是可以在本机正常休眠唤醒的，只不过设计上考虑休眠后如果更换设备会导致唤醒故障所以默认关闭了休眠功能。可以在本地组策略编辑器 (gpedit.msc) 中启用休眠

`\\Computer Configuration\\Administrative Templates\\Windows Components\\Portable Operating System\\**的 Windows To Go 工作区启动时，允许休眠 (S4) `

## 设备选择

固态优盘便携，没有可能存在的供电问题，没有线缆带来的可能接触不良问题，本身速度容量也已足够，比固态硬盘更适合做 WTG

## 界面设配

如果切换的设备分辨率不同，有些程序可能会出现界面问题，比如 Totalcmd 在 1080p 和 4K 的环境中切换，需要调整配置文件 wincmd.ini，也是因为需要对 ini 文件中的特定选项来设置值，所以好像只能用 Python 而不能用 AHK，代码见后文

## 程序许可

坚果云和 iCloud Drive 算是两个典型，坚果云要好一点，如果只在一台设备上打开就不需要重新登录，而  iCloud Drive 只要设备变动就会反复要求重新登录，还是二次验证的……为了 Logseq 单向同步到移动端，只有忍了，写了一个开机脚本，根据分辨率判断启动指定场景程序（也可以通过其他因素判断，未研究）

## 开机脚本

（代码盲协助 ChatGPT 完成……）

```python
import os
import time
import subprocess
import configparser
from screeninfo import get_monitors
import codecs
from io import StringIO
import logging

log_dir = 'D:\\N\\py'
log_file = 'start.log'

if not os.path.exists(log_dir):
    os.makedirs(log_dir)

log_path = os.path.join(log_dir, log_file)
logging.basicConfig(filename=log_path, level=logging.DEBUG, format='%(asctime)s - %(levelname)s - %(message)s')

def launch_apps_1080p():
    subprocess.Popen([r"C:\Program Files\Nutstore\Nutstore.exe"], shell=True)
    subprocess.Popen([r"C:\Program Files (x86)\Common Files\Apple\Internet Services\iCloudDrive.exe"], shell=True)

def launch_apps_non_1080p():

def totalcmd_re(width, height):
    ini_file = 'D:\\o\\TCCEE\\wincmd.ini'
    config = configparser.ConfigParser()
    with codecs.open(ini_file, 'r', encoding='utf-16-le') as f:
        file_content = f.read()
    if file_content.startswith('\ufeff'):
        file_content = file_content[1:]
    file_like_object = StringIO(file_content)
    config.read_file(file_like_object)

    if width == 1920 and height == 1080:
        config['AllResolutions']['Iconsize32_dpi'] = '96'
        config['AllResolutions']['Iconsize32'] = '16'
        config['Configuration']['MinLineHeight'] = '-8'
        config['Configuration']['OverrideDPI'] = '96'
        config['Configuration']['OverrideDPI96'] = '96'
    elif width == 3840 and height == 2160:
        config['AllResolutions']['Iconsize32_dpi'] = '192'
        config['AllResolutions']['Iconsize32'] = '32'
        config['Configuration']['MinLineHeight'] = '-16'
        config['Configuration']['OverrideDPI'] = '192'
        config['Configuration']['OverrideDPI96'] = '192'

    with codecs.open(ini_file, 'w', encoding='utf-16-le') as f:
        config.write(f)
    time.sleep(10)
    subprocess.Popen(['D:\\o\\TCCEE\\ctotalcmd.exe'], shell=True)


def main():
    monitor = get_monitors()[0]
    width = monitor.width
    height = monitor.height

    if width == 1920 and height == 1080:
        launch_apps_1080p()
    else:
        launch_apps_non_1080p()
    totalcmd_re(width, height)

if __name__ == "__main__":
    main()

```













