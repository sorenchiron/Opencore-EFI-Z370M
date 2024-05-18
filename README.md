# Opencore-EFI-Z370M
OC EFI for Hackintosh `13-Ventura` install/boot.

# Hardware Specification

The total worth of this hackintosh is ￥2876 ($398 USD)

| Part | Model | Details |
| ----- | ----- | ----- | 
| 主板 Motherboard | 华硕 Asus Z370M Plus II | USED |
| CPU | Intel 8600K | OEM USED |
| iGPU | Intel UHD 630 | Integrated |
| GPU | AMD RX 5700XT Sapphire Nitro+ | 超白金OC USED |
| SSD | WD SN550 HBM 1T | for MacOS |
| SSD | GUDGA 128G | for Win11 USED |
| 电源 Power | 玄武550 | Rated 600W |
| 网卡 NetAdapter | BCM94360CD | USED |

Chinese and English introductions provided below:

# 中文文档 Readme
### 如果有5700xt独显：
- 安装U盘中，可以使用`EFI-installer`，其中已经匹配好了USB端口。
- 安装过程屏幕可直接插5700XT。
- 安装好后，可以使用`EFI-hless-r24-ag5500xt-ss5700-RTC-acpi-wake` 替代系统EFI，实测48小时工作无故障。
- 请删除EFI文件夹的后缀名，只保留`EFI`，本仓库的后缀只为方便标注辨别。

### 如果没有GPU，仅有CPU核显UHD630
- 安装好后，可以使用`EFI-UHD-working`代替系统EFI，注意文件夹应重命名为`EFI`再使用。
- 实测24小时工作无故障。
- UHD630可以带动4k屏，如果想要4K60FPS，需要主板的HDMI/DP接口支持。主要瓶颈是主板接口规格。


# How to use: Readme!
### TODO