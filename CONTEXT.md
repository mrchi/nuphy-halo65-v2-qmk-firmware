# NuPhy Halo65 V2 固件

本仓库维护 NuPhy Halo65 V2 键盘的 QMK 固件。以下术语用于描述目标键盘、键位配置和可刷写固件。

## Language

**Halo65 V2**：
本项目的 NuPhy Halo65 V2 ANSI 布局键盘，不包含其他 Halo 型号或代际。
_Avoid_：Halo65（省略代际）、Halo V2（省略型号）

**VIA keymap**：
为 Halo65 V2 启用 VIA 动态改键能力的 QMK 键位配置，不是 VIA 客户端应用，也不是 VIA 键盘定义 JSON。
_Avoid_：VIA 软件、VIA JSON

**VIA 固件**：
以 VIA keymap 编译得到、供 Halo65 V2 刷写的完整 QMK 固件，不是独立的 VIA 插件或键位配置文件。
_Avoid_：VIA 插件、键位配置文件

**BIN 固件**：
Halo65 V2 的最终二进制刷写文件，扩展名为 `.bin`；与构建中间产物 `.hex` 区分。
_Avoid_：HEX 固件（指本项目发布产物时）

## 灯光

**环灯**：
Halo65 V2 机身四周的装饰性灯带，与主键区灯相互独立，可单独开关、配色和调速。
_Avoid_：侧边灯、氛围灯、Side RGB

**键盘灯**：
主键区的照明与灯效区域，是环灯之外的唯一另一个灯光区域。
_Avoid_：背光、主灯、Matrix RGB

**定位灯**：
默认灯效，只点亮 F、J 与 ↑ 三颗键，用于盲打定位；其余键保持熄灭。
_Avoid_：position mode、FJ 灯

**出厂默认**：
设备首次上电或恢复出厂后生效的灯光初始状态，只写入一次，此后由用户设置覆盖。
_Avoid_：默认值、初始配置

**设备重置**：
由 Fn 组合键长按触发的恢复出厂操作，把设备恢复到与首次上电一致的出厂默认。
_Avoid_：复位、Factory Reset

## 键位层

**Fn 层**：
由 Fn 键按住的层，承载媒体控制、音量、屏幕亮度、Mac 快捷键与导航键。
_Avoid_：Fn1 层、第一功能层

**F 键层**：
由 Fn 加 Shift 进入的层，把主键区映射为 F1-F12。
_Avoid_：Fn2 层、第二功能层

**控制层**：
集中承载设备连接、设备控制与灯效控制的层，用 Fn 组合键进入。
_Avoid_：灯效层、副灯层
