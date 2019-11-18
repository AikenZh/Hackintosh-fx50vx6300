# Hackintosh-fx50vx6300

config.plist修改自[黑果小兵的部落阁](https://blog.daliansky.net/)10.15镜像中的config_Desktop.plist

目前用于10.14，个人测试过也能用于10.15

Clover版本：5098

| Clover   |                                                              |
| -------- | ------------------------------------------------------------ |
| 主板     | 华硕 X550VX ( 英特尔 PCI 标准主机 CPU 桥 - 100 Series/C230 Series 芯片组) |
| 处理器   | 英特尔 Core i5-6300HQ @ 2.30GHz 四核                         |
| 显卡     | HD530	已驱动，显存通过Hackintosh修改为2048MB              |
| 声卡     | ALC255	已驱动，利用Hackintosh注入Layout ID为99            |
| 亮度     | 通过`Clover Configurator` -> ACPI设置 -> 添加PNLF            |
| 蓝牙     | 没用过，未驱动                                               |
| 无线网卡 | 某宝买                                                       |

`ACPI/patched/`：

​	`DSDT.aml`：Clover F4 提取 -> 通过`maciASL`编译改错 -> 打上[RehabMan](https://github.com/RehabMan)收录的[电量补丁](https://github.com/RehabMan/Laptop-DSDT-Patch/blob/master/battery/battery_ASUS-N55SL.txt)

> 电量显示电池开机没问题，充着电开机拔插一下就能正常显示（触摸板同，不过不显示也能正常用手势）

​	`SSDT-Pr.aml`：CPU变频 使用`ssdtPRGen.sh`生成

`kexts/Others/`:

​	`USBPorts.kext`：根据黑果小兵的[USB定制](https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html#%E5%AE%9A%E5%88%B6usb)教程定制的，左边两个口使用USB3时接口设置为USB3、USB2时设置为USB2，其他都设置为内建了

​	`CPUFriend.kext` 和 `CPUFriendDataProvider.kext`:通过[one-key-cpufriend](https://github.com/stevezhengshiqi/one-key-cpufriend)选择平衡性能模式生成

> 安装系统的时候用ApplePS2SmartTouchPad.kext键盘不能用，改为VoodooPS2Controller.kext解决但是这个不能使用触摸板手势，安装完改回来就行。