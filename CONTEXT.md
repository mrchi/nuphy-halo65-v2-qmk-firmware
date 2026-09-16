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
