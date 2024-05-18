# Opencore-EFI-Z370M
`Opencore-0.9.9` EFI for Hackintosh `13-Ventura` install/boot.

# 硬件 Hardware Specification

The total worth of this hackintosh is ￥2876 ($398 USD)

| Part | Model | Details |
| ----- | ----- | ----- | 
| 主板 Motherboard | 华硕 Asus Z370M Plus II | USED |
| CPU | Intel 8600K | OEM USED |
| iGPU | Intel UHD 630 | Integrated |
| GPU | AMD RX 5700XT Sapphire Nitro+ | 超白金OC USED |
| RAM | 丁凌存储 3200MHz DDR4 32G | 海力士Hynix颗粒 |
| SSD | WD SN550 HBM 1T | Old controller |
| SSD | GUDGA 128G | for Win11 USED |
| 电源 Power | 玄武550 | Rated 600W |
| 网卡 NetAdapter | BCM94360CD | USED |

Chinese and English introductions are provided below:

# 中文文档 Readme
### 如果有5700xt独显：
- 安装U盘中，可以使用`EFI-installer`，其中已经匹配好了华硕Z370M-Plus-II主板的USB端口。
    - USB3 gen1 使用了主板上的`U31G1_34`，另一个空置未使用。 
    - 机箱USB口接的`USB1314`
- 安装过程屏幕可直接插5700XT。
- 安装好后，可以使用`EFI-hless-r24-ag5500xt-ss5700-RTC-acpi-wake` 替代系统EFI，实测48小时工作无故障。
- 请删除EFI文件夹的后缀名，只保留`EFI`，本仓库的后缀只为方便标注辨别。

### 如果没有GPU，仅有CPU核显UHD630
- 安装好后，可以使用`EFI-UHD-working`代替系统EFI，注意文件夹应重命名为`EFI`再使用。
- 实测24小时工作无故障。
- UHD630可以带动4k屏，如果想要4K60FPS，需要主板的HDMI/DP接口支持。主要瓶颈是主板接口规格。

### 目前的体验
- [x] Apple ID 登录正常
- [x] iCloud 全部服务正常，AppStore正常。
- [x] AriDrop 正常
- [x] 西部数据SSD完全正常
- [x] 锁屏解锁体验正常
- [x] 开关机流程顺畅，工作正常。无`safe-mode`警告。
- [x] 网页正常，看视频正常
- [x] 蓝牙连音响、连键盘正常
- [x] 蓝牙/有线，连妙控板2正常
- [x] 锁屏熄屏正常。主机不睡眠，锁屏后自动休停屏幕，体验正常。
- [x] 速度完爆一切macbook pro，同时开20个sketch大文件画图，完全流畅毫无卡顿。
- [x] 自购SSD太划算了，Nvme 1TB才三百来块，速度快的飞起，反观Apple，无语。
- [ ] Chrome浏览器一切正常，必须关闭其硬件加速。
- [ ] Safari浏览器不正常，反正我用Chrome，无所谓。
- [ ] 深度睡眠hibernate不正常，已禁止任何睡眠，之后一切正常。
- [ ] 浅睡唤醒Darkwake不正常，已禁止任何睡眠，之后一切正常。

### 详细说明
- 关于BIOS
    - 关闭vt-d
    - 关闭usb s5唤醒
    - 关闭快速启动
    - 关闭安全启动
    - 关闭串口
    - 关闭网络唤醒等各类唤醒
    - 启动类型=其他操作系统
    - 关闭 Resizable Bar
    - 开启大于4G寻址
    - 北桥-开启核显
    - 北桥-核显分配内存=1024MB
    - 北桥-首选显卡=自动
    - 开启内存XMP
    - 其他更细致的设定，请遵循[Opencore](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#starting-point)针对Coffeelake-CPU的建议
- 关于USB安装盘
    - 使用了USB3盘，镜像加载速度明显提升。
    - 从mac上下载了Ventura的安装dmg，大小12GB，在mac下使用命令制作了完整系统的安装U盘
    - 尝试过Opencore推荐的macrecovery小镜像，只有673MB，但是完整系统需要联网下载，网速越来越慢，要至少48小时，中国区果友可以直接放弃这种在线安装思路。
- 关于主板USB口
    - 使用`USBToolBox.kext`,`UTBMap.kext`映射端口
    - 如果你插的主板口不是我提到的`U31G1_34`和`USB1314`，则应该自行下载 `USBToolBox` 的程序工具，重新映射端口，并生成你自己的 `UTBMap.kext`，替换本仓库EFI中的 `UTBMap.kext`。

### config.plist 详细说明
TODO

### 重要提示与故障问题解答
- 强烈推荐，强烈推荐买一个单独的SSD，装一个windows，128G足够了，二手价格在36元左右，一个硬独立双系统windows几乎能帮你解决所有遇到的问题。可以说如果没有这份单独的128G+win11，我是无法在华硕z370m-plusII上安装配置成功的。
- 新手安装黑苹果时，一定会需要依赖黑苹果主机硬件信息，比如映射USB，调整CPU供电，调整显卡型号参数，调试核显，根据主板内的SSDT来解决bug等等，所以在黑苹果机上装一个windows，上述操作将变得非常非常轻松。
- 5700XT连屏幕，遭遇了显示器绿屏，全屏绿，崩溃死机
    - 我遇到了，解决了，全部方法分享如下：
    - 先验证显卡是否良好
        - 在windows下，显卡驱动全部默认设置，不要降频也不要超频。下载图吧工具箱，跑个甜甜圈。
        - 如果崩溃，请下载 DDU （[Display Driver Uninstaller](https://www.wagnardsoft.com/content/Download-Display-Driver-Uninstaller-DDU-18076)）彻底卸载AMD驱动。进安全模式请见[微软官方指导](https://support.microsoft.com/zh-cn/windows/%E5%9C%A8-windows-%E4%B8%AD%E4%BB%A5%E5%AE%89%E5%85%A8%E6%A8%A1%E5%BC%8F%E5%90%AF%E5%8A%A8%E7%94%B5%E8%84%91-92c27cff-db89-8644-1ce4-b3e5e56fe234) 重装驱动，不要动设置。再进正常系统，开甜甜圈压力测试看看。
    - 如果显卡在windows下也绿屏或花屏崩溃
        1. AMD驱动问题，可以下载老版本驱动，或者进AMD官网-网吧专区，下载网吧驱动，有网友报告问题解决。
        1. HDMI线材与协议问题，AMD显卡对HDMI兼容缺陷是一个已知问题，AMD官方今年与HDMI协商共建开源驱动，疑似是为了解决HDMI兼容问题，但遭到HDMI方面拒绝。
        1. 显卡显存虚焊，或显卡核心虚焊，寄修费用预估200~300。

# How to use: Readme!
### TODO