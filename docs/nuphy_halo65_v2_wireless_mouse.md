# Halo65 V2 无线滚轮报告

## 问题

Halo65 V2 在蓝牙模式下，鼠标滚轮键一次触发会被放大。蓝牙与 2.4G 共用 UART 发送路径；本次实测仅覆盖蓝牙和 USB。修复涉及两处问题：

1. `UART_Send_Bytes()` 会把报告发送 3 次；鼠标报告是相对量，重复发送会放大滚动量。
2. `tmk_core/protocol/host.c` 的 `host_mouse_send()` 还额外调用了一次无参的 `uart_send_mouse_report()`。正常发送路径已经由 `rf_driver.c` 调用带 `report` 参数的版本，因此会造成重复发送。

## 修复

- `keyboards/nuphy/halo65_v2/ansi/rf.c`：仅对非鼠标报告设置 `uart_repeat_flag`，鼠标报告只发送一次。
- `tmk_core/protocol/host.c`：删除多余的 `uart_send_mouse_report()` 声明和调用，保留 `rf_driver.c` 的唯一鼠标报告发送路径。

## 验证

使用原始 HID 抓取工具比较无线和 USB 报告：

```bash
cd .scratch/halo65v2-wheel-scroll
clang -O2 -o hid_capture hid_capture.c -framework IOKit -framework CoreFoundation
./hid_capture bt 10
./hid_capture usb 10
```

刷入 VIA 固件后，蓝牙单次滚轮操作的报告间隔约为 `16 ms`、`90 ms`，不再出现 `0.2–2 ms` 内的三连发；剩余的 `3` 个 `v=1` 报告是 QMK `mousekey` 的正常重复行为，与 USB 基线一致。
