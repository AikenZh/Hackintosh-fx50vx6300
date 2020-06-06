# Hackintosh-fx50vx6300

适用于10.14

Clover版本：5098

| Clover   |                                                              |
| -------- | ------------------------------------------------------------ |
| 主板     | 华硕 X550VX ( 英特尔 PCI 标准主机 CPU 桥 - 100 Series/C230 Series 芯片组) |
| 处理器   | 英特尔 Core i5-6300HQ                                        |
| 显卡     | HD530（hdmi改了一下，没测试，因为我没有...）                 |
| 声卡     | ALC255	利用Hackintool注入Layout ID为99                    |
| 亮度     | 通过`Clover Configurator` -> ACPI设置 -> 添加PNLF            |
| 蓝牙     | 没用过，未驱动                                               |
| 无线网卡 | 某宝买                                                       |

`ACPI/patched/`：

​	`DSDT.aml`：Clover F4 提取 -> 通过`maciASL`编译改错 -> 打上[RehabMan](https://github.com/RehabMan)收录的[电量补丁](https://github.com/RehabMan/Laptop-DSDT-Patch/blob/master/battery/battery_ASUS-N55SL.txt)

​	`SSDT-Pr.aml`：CPU变频 使用`ssdtPRGen.sh`生成

​    ` SSDT-Disable-DGPU.aml`：禁用独显

`kexts/Others/`:

​	`USBPorts.kext`：根据黑果小兵的[USB定制](https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html#%E5%AE%9A%E5%88%B6usb)教程定制的，左边两个口使用USB3时接口设置为USB3、USB2时设置为USB2，其他都设置为内建了

​	`CPUFriend.kext` 和 `CPUFriendDataProvider.kext`：通过[one-key-cpufriend](https://github.com/stevezhengshiqi/one-key-cpufriend)选择平衡性能模式生成

​	`VoodooPS2Controller_v2.1.5.kext`：编辑的时候触控板容易误触，于是只保留了`VoodooPS2Keyboard.kext`，需要触控板的替换为backup里的`ApplePS2SmartTouchPad.kext`或者`VoodooPS2Controller_v2.1.5.kext`





> 麦克风没用，尝试自己仿冒声卡驱动，没弄好，先备份一下提取的一些信息以后有空再试试。