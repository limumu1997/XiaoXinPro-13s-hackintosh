# XiaoXinPro-13s-hackintosh

# 感谢前人的贡献付出
最近迷恋macOS系统，拿出闲置了几年的小新pro13s折腾一番。结合前辈们的EFI和现在最新的驱动，现在已得出一个稳定满足日常使用的版本。笔记本硬件无任何改动，仅开启了BIOS的高级模式。如果不能正常使用此EFI可访问原库Wiki参考资料。

  ![Work](./screenshot/Work.png)


## 不正常工作
- ~~睡眠~~ (小新PRO13不能真正睡眠，可以仿真睡眠。唤醒比较困难，`OC` 下唤醒方法是：`电源键`唤醒)
- 声卡MIC(`暂时解决方法`：启动台-声音-输入：手动切换到“`外接可用麦克风设备`”), 了解[更多](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/%E5%A3%B0%E5%8D%A1)


## Lenovo XiaoXin Pro 13s 2020 Hackintosh
### 适用：`2020款小新pro13s Intel版本`
## 电脑配置
|规格 | [详细信息](https://item.lenovo.com.cn/product/1007854.html) |
|:-: | :-:|
|电脑型号|联想小新pro13 笔记本电脑|
|操作系统|macOS Ventura/ Catalina |
|处理器|英特尔 酷睿 i5 - 10210U |
|内存|16GB板载无法更换|
|硬盘|PCIEX4，[混搭](https://zhuanlan.zhihu.com/p/89874980), 以下针对安装 macOS 下说明 |
|显卡|Intel HD Graphics CFL CRB|（UHD620）|
|显示器|13.3 英寸 IPS 2560x1600|
|声卡| Realtek ALC257|
|网卡|[原装网卡AX201] ( [Intel网卡](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/Intel%E7%BD%91%E5%8D%A1) / [BCM94360Z4](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/BCM94360Z4%E5%9B%9B%E5%A4%A9%E7%BA%BF) / [白果拆机网卡](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/%E7%99%BD%E6%9E%9C%E6%8B%86%E6%9C%BA%E7%BD%91%E5%8D%A1) ) |
|官方BIOS|搜【[小新pro 13 Intel](https://newsupport.lenovo.com.cn/search_result.html?q=%E5%B0%8F%E6%96%B0pro%2013%20Intel)】 选【小新 Pro-13 2019(2020)(Intel平台：IML版)】|

## 注意
- 部分i5 和 `i7-10710U` 的 CPUID 为 `0x0A0660`，需要仿冒`cpuid` ：`0x0806EC`、`0x0806EB` 或其他），详情看[这里](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/%E6%9F%A5%E7%9C%8B%E6%9C%AC%E6%9C%BACPUID)
- 需要[解锁 DVMT 、 开启CFG Lock](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/DVMT%E8%A1%A5%E4%B8%81#%E6%B5%8B%E8%AF%95%E7%89%88bios)
- 目前 `声卡(MIC不可用)`、~~`睡眠`~~ 这些比较棘手的问题需要解决，正常使用已经没有问题。
- 硬盘耗电问题看下[小新pro-13耗电情况.xlsx](https://github.com/daliansky/XiaoXinPro-13-hackintosh/tree/master/EFI/Document)
- 更多关于小新pro13  的黑苹果事宜请看 [wiki](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki)

## 安装部分

混搭硬盘: （`黑苹果下：可用、不可用`）
- `可用`：UMIS开头的是忆联（忆联AH530）
- `可用`：INTEL开头的是因特尔（INTEL 760P)
- `可用`：WD BLACK开头的是西数（SN 730)
- `不可用`：SKHynix开头的是海力士（Hynix PC601 ?：`SK HYNIX SKHynix_HFS512GD9TNI-L2A0B`)
- `不可用`：SAMSUNG开头的是三星（三星PM981a：`SAMSUNG MZVLB512HBJQ-000L2`)  

`PS`: 以上是已知道型号，倘若还有其他型号：既不代表可用，也代表不可用！


如果你的机子硬盘是三星固态硬盘(`SAMSUNG MZVLB512HBJQ-000L2`) 或 海力士(`SKHynix_HFS512GD9TNI-L2A0B`)，  
为了更好使用 `macOS` ，强烈建议替换其他型号 

详细的安装教程请移步：[联想小新PRO 13 2019兼macOS Catalina安装教程](https://blog.daliansky.net/Lenovo-Xiaoxin-PRO-13-2019-and-macOS-Catalina-Installation-Tutorial.html) 

- ### 安装教程

    - `Fn+F2`进入`BIOS`,
    - 先查看 `Information`：`Secure Boot` 是否为 `Disabled`;
    - 如果 `Secure Boot` 是 `Enabled`，选择左边到 `Security`： 设置 `Secure Boot` 为 `Disabled`;
    - `Fn+F10` 保存设置
    - 需要[解锁 DVMT 、 开启CFG Lock](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/DVMT%E8%A1%A5%E4%B8%81#%E6%B5%8B%E8%AF%95%E7%89%88bios)  


- ### ~~安装后操作~~

    - ~~安装好系统，先用 `安装的EFI` 进入系统~~
    - ~~然后找到`终端`执行一下：~~
    - ~~`sudo spctl --master-disable`~~
    - ~~再执行`重建缓存`:~~
    - ~~`sudo kextcache -i /`~~
    - ~~替换 `EFI` 或 `config.plist`~~
    - ~~重启~~

- ### OC 与 Clover之间切换：
   - 例如Clover 转 OC
   - 先设置OC启动
   - 第一次重启，选择`reset nvram`，这时之前的启动设置会清除了
   - 再次设置对应的`EFI`启动即可

     
   
## 镜像下载
  
  - [[**黑果小兵的部落阁**] :【黑果小兵】原版镜像](https://blog.daliansky.net/categories/下载/镜像/)

## 问题解答(FAQ)
  - ### [Wiki](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki)

## EFI 下载
  - ### [Releases](https://github.com/daliansky/XiaoXinPro-13-2019-hackintosh/releases)

## 更新日志  
  - ### [Changelog](Changelog.md)

## 注意

- 安装注意：小新由于安装过程中触摸板可能无法驱动，使用U盘安装macOS会占用仅仅一个USB接口,
  建议安装之前先买个usb拓展,用于插入鼠标,来进行安装步骤选项设定
- 该EFI目录中有CLOVER引导方式，也有OC的引导方式，
  目前两种方法都可以使用，但是OC引导方式，需要自己添加win系统的引导，
  具体方法：[添加引导](EFI/Document/OC-引导多系统@OC-xlivans.md)
## 正常工作
- 显卡

- 电源

- 蓝牙

- 显示器亮度调节

- 无线（[原网卡AX201](https://github.com/daliansky/XiaoXinPro-13-hackintosh/wiki/%E5%B0%8F%E6%96%B0pro13%E5%9C%A8macOS%E7%B3%BB%E7%BB%9F%E4%B8%8B%E5%8F%AF%E4%BD%BF%E7%94%A8%E7%9A%84%E7%BD%91%E5%8D%A1) 在macOS 下可以驱动了(`08-02-2020`)

- 触摸板 (`02-17-2020`) （1、`OC`关闭触摸板方法：`FN+F6`）

  ![TouchPad](./screenshot/TouchPad.png)

- USB定制（采用 `ACPI` 方式，为使用 `OC` 做准备）

- 声卡 [14.x下无法加载，14.x以上系统没此问题，声卡 ID 使用说明](Changelog.md#oc--clover-%E5%85%B3%E4%BA%8E%E5%A3%B0%E5%8D%A1id-%E4%BD%BF%E7%94%A8%E6%83%85%E5%86%B5)

- 其它 `ACPI` 补丁修复采用 `hotpatch` 方式，文件位于 `/ACPI/patched`

