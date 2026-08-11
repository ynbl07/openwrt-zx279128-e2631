# ZTE E2631 / ZX279128 OpenWrt Bring-up

This repository holds the first-stage OpenWrt bring-up scaffold for the ZTE E2631.
It is intended for RAM-only initramfs testing first, not flash writes.

Current focus:
- basic target scaffold
- DTS registration for the board
- GitHub Actions kernel build


目前进度（放弃）
已成功构建过一份 E2631 RAM 启动镜像：OpenWrt 6.12.100 initramfs uImage，约 4.77 MB，U-Boot 校验、CRC、load/entry 0x40008000 都正确。
该镜像 bootm 后停在 Starting kernel ...，但原厂固件也在该处不输出串口，因此不能据此判断内核一定没启动。
根因定位到 UART：E2631 虽是 ZX279128S，但 UART IP 的 compatible 是 zte,ZX279127-uart，寄存器布局不是标准 PL011。此前的 earlycon=pl011 会访问错误寄存器。
ZX279133 项目确实有同类处理：ZTE 专用寄存器映射、vendor_zte、AMBA ID 0x001feffe、以及 earlycon=zteuart。
正在准备的修复
E2631 DTS 改为 ZTE UART compatible，并加入：arm,primecell-periphid = <0x001feffe>;

启动参数改为：earlycon=zteuart,0x94404000

为 OpenWrt 的 Linux 6.12 添加最小 PL011 补丁：启用 ZTE 偏移表、AMBA 匹配与专用 earlycon。
Workflow 已增加静态检查，防止后续构建遗漏这些项。
