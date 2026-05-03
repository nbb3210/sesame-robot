# Sesame Robot 物料清单（BOM）

本文件根据 [`hardware/bom/README.md`](README.md) 与 [`hardware/printing/README.md`](../printing/README.md) 整理而成，按用途分类汇总，便于一次性梳理整机所需物料。

> 整机预算约 50–60 美元（不含 3D 打印耗材与工具）。
> 接线方案有三种（A / B / C），请按下文挑选其一执行；其余「核心电子件、电源、紧固件、3D 打印件、耗材工具」为通用项。

---

## 1. 核心电子件（三种方案通用）

| 物料 | 数量 | 说明 |
| --- | --- | --- |
| MG90S 全金属齿微型舵机 | 8（建议买 10 含备件） | 髋关节 / 腿部主驱动；自带舵机摇臂 |
| 0.96" SSD1306 I²C OLED | 1 | 128×64 屏，作为机器人「表情面板」嵌入顶盖 |
| USB-C 数据 / 电源线 | 1 | 须支持 5 V/3 A，用于烧录与有线供电 |
| KCD1 面板式船形开关 | 1 | 卡入顶盖开关孔位 |
| 22 AWG 硅胶线套装 | 1 | 电源 / 地线主干 |
| 30 AWG 硅胶线套装 | 1 | 信号线及狭窄空间走线 |
| 热缩管套件 | 1 | OLED、开关、电池接点绝缘 |
| 小号扎带 | 1 包 | 机内理线 |

---

## 2. 接线方案（三选一）

### 方案 A — Lolin S2 Mini 手工排线

| 物料 | 数量 | 说明 |
| --- | --- | --- |
| Lolin / WeMos ESP32-S2 Mini | 1 | 原生 USB-C，DIY 推荐主控 |
| 5×7 cm 左右洞洞板 | 1 | 制作排针矩阵与电源 / 地总线 |
| 3-pin 直针排针 | 8 | 适配 MG90 舵机插头 |
| 5–12 V 转 5 V/3 A 降压模块 | 1 | 电池供电时使用 |

### 方案 B — Sesame Distro Board V2（Build Kit 已含）

| 物料 | 数量 | 说明 |
| --- | --- | --- |
| Sesame Distro Board V2 PCB | 1 | 全 SMD 设计；建议 PCBway 贴片，详见 [`hardware/pcb/README.md`](../pcb/README.md) |

> 购买官方 Build Kit 时，V2 已组装并预烧录固件，无需另行采购。

### 方案 C — Sesame Distro Board V1 / ESP32-DevKitC-32E（旧版，仍兼容）

| 物料 | 数量 | 说明 |
| --- | --- | --- |
| ESP32-DevKitC-32E（ESP32-WROOM-32） | 1 | 32E 自带 PCB 天线；用 32U 需自行接外置天线 |
| Sesame Distro Board V1 PCB | 1 | Gerber：`Gerber_Sesame-Distro-Board_PCB_Sesame-Distro-Board_V1.zip`（PCBway 下单） |
| 5 V/3 A 降压模块 | 1 | 焊接到 V1 PCB 预留位 |
| 1000 µF 电解电容（≥10 V） | 1 | 降压输出滤波 |
| JST-XH / PH 4-pin 排座 | 1 | 可选外接连接器 |
| 2-pin 2.54 mm 接线端子 | 1 | 可选电池输入端子 |
| M2.5 × 5 mm 公母铜柱 | 4 | 抬高 PCB 至 DevKit 安装孔 |

> V1 不能仅靠 USB-C 供电，必须电池 + 降压模块组合。

---

## 3. 电源与连接器

| 物料 | 数量 | 说明 |
| --- | --- | --- |
| 3S 450 mAh LiPo（XT30 接口） | 1 | 推荐无线方案；务必选高放电倍率 |
| 2× AAA 电池仓 | 1 | 容纳 2 节 10440 锂电（约 7.4 V 标称），需配降压 |
| 10440 锂电池（350–400 mAh） | 2 | 10×44 mm 标准锂电；建议买备件 |
| 10440 双槽锂电充电器 | 1 | 务必从仓中取出后单独充电 |
| XT30 母头延长线 | 1 | 接入开关 / PCB，避免剪掉电池原厂接头 |

---

## 4. 紧固件 / 机械件

| 物料 | 数量 | 用途 |
| --- | --- | --- |
| M2 × 5 mm 自攻螺丝 | ~40 | 塑件连接、OLED、舵机座、外壳（推荐买杂规格套装） |
| M2.5 × 5 mm 机械螺丝 | 10 | 舵机摇臂固定（原配螺丝通常过短） |

---

## 5. 3D 打印件

材料：**PLA / PLA+**；填充 8–10% 蜂窝；2 层墙。
共 11 件，STL 位于 [`hardware/printing/stl/`](../printing/stl/)：

| 部件 | 是否需支撑 |
| --- | --- |
| Joint R1–R4 | 否 |
| Joint L1–L4 | 否 |
| Internal Frame（内骨架） | 否 |
| Bottom Cover（底盖） | 否 |
| Top Cover（顶盖，推荐 Enclosed v91） | **是**（局部手动支撑） |

---

## 6. 焊接耗材与工具

| 物料 | 备注 |
| --- | --- |
| 含铅焊锡 0.6–0.8 mm（63/37） | 洞洞板密集焊点更顺滑 |
| 助焊笔 | 保护洞洞板与 PCB 焊盘 |
| 吸锡线 / 吸锡器 | OLED 引脚返修必备 |
| 小号斜口钳 | 修剪舵机线、洞洞板、支撑 |
| 精密螺丝刀套装 | 拧 M2 自攻件 |

---

## 7. 电源与安全提示

- 电源轨须能持续提供 **≥5 V / 3 A**。
- **Lolin S2 Mini**：USB-C PD（5 V/3 A）有线供电，或电池 + 降压。
- **Distro Board V2**：同时支持 USB-C PD 与电池 + 降压（Build Kit 默认）。
- **Distro Board V1（旧版）**：因设计限制不能仅靠 USB-C 工作，必须电池 + 降压。
- 电池供电时，电池 → 船形开关 → 降压模块 → 电源轨，参见 [`docs/wiring-guide/README.md`](../../docs/wiring-guide/README.md)。
- **不要剪掉电池原厂接头**，使用 XT30 / JST-RCY 转接线，保留充电能力。
- 「2× 10440 + 2× AAA 电池仓」组合可放入机身电池仓，配套现有开关与降压模块即可工作。
- **10440 锂电必须从电池仓取出后用专用充电器单独充电**，除非电池仓明确支持锂电安全充电（多数 AAA 电池仓不支持）。

---

## 参考来源

- 英文原版 BOM：[`hardware/bom/README.md`](README.md)
- 3D 打印件清单：[`hardware/printing/README.md`](../printing/README.md)
- PCB 下单指南：[`hardware/pcb/README.md`](../pcb/README.md)
- 接线指南：[`docs/wiring-guide/README.md`](../../docs/wiring-guide/README.md)
- 装配指南：[`docs/build-guide/README.md`](../../docs/build-guide/README.md)
