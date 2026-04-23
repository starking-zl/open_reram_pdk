# 鸣蛇 / Ming She

**面向多模态感知的开源存算一体AI推理芯片**  
**An Open‑Source Compute‑In‑Memory AI Inference Chip for Multi‑Modal Sensing**


## 项目简介 / Introduction

**中文**  
鸣蛇是一颗纯虚拟的、理论极限探索型存算一体（CIM）AI推理芯片。项目源自《山海经》：“有蛇焉，四翼，其音如磬。”蛇身蜿蜒暗合多通道传感器阵列的布线美学，四翼象征多模态感知，其音如磬隐喻确定性推理唤醒。

本项目不追求商业量产，不依赖闭源IP，不进行实际流片。其唯一目标为：在理想工艺假设下，探索基于ReRAM的存算一体架构在多模态端侧推理场景中的理论能效极限与设计方法学。

**English**  
Ming She is a purely virtual, theoretical‑limit‑exploring compute‑in‑memory (CIM) AI inference chip. The name originates from the *Classic of Mountains and Seas*: “There is a serpent with four wings, and its sound is like a chime stone.” The serpentine body evokes the routing aesthetics of multi‑channel sensor arrays; the four wings symbolize multi‑modal perception; and the chime‑like sound metaphorically represents deterministic inference wake‑up.

This project does not target commercial production, relies on no closed‑source IP, and will **not undergo physical tape‑out**. Its sole purpose is: under idealized process assumptions, to explore the theoretical energy‑efficiency limits and design methodology of ReRAM‑based CIM architectures for multi‑modal edge inference scenarios.


## 项目状态 / Project Status

**中文**  
本项目已完成全部理论设计与文档编写，包含完整的RTL源码、自建开源PDK骨架、仿真验证环境以及详尽的中英文设计文档。**所有设计均未经硅验证，性能数据为理论推算值，仅供学术研究与架构探索使用。**

**English**  
This project has completed all theoretical design and documentation, including full RTL source code, a self‑built open‑source PDK skeleton, a simulation verification environment, and comprehensive bilingual design documents. **None of the designs have been silicon‑verified; all performance figures are theoretical estimates and are intended solely for academic research and architectural exploration.**


## 快速导航 / Quick Navigation

| 文档 / Document | 描述 / Description |
|:---|:---|
| [芯片规格书 / Specification](docs/SPECIFICATION.md) | 功能特性与指标定义 |
| [架构设计 / Architecture](docs/ARCHITECTURE.md) | 模块划分、接口、状态机 |
| [寄存器手册 / Register Map](docs/REGISTER_MAP.md) | 完整寄存器位域定义 |
| [理论性能分析 / Performance Analysis](docs/PERFORMANCE_ANALYSIS.md) | 算力、能效、延迟推算 |
| [免责声明 / Disclaimer](docs/DISCLAIMER.md) | 未测试声明与法律条款 |


## 目录结构 / Directory Structure

**中文**  
下载并解压 `open_reram_pdk.zip` 后，目录组织如下。核心设计文件位于 `design/rtl/`，文档位于 `docs/`。

**English**  
After downloading and extracting `open_reram_pdk.zip`, the directory structure is as follows. Core design files reside under `design/rtl/`, and documentation under `docs/`.

```

open_reram_pdk/
├── sky130/                   # 基础CMOS工艺骨架 (基于SKY130)
├── reram/                    # ReRAM器件模型与宏单元
├── scripts/                  # 辅助脚本
├── docs/                     # 全套中英文设计文档
├── design/                   # 芯片设计核心目录
│   ├── rtl/                  # 11个Verilog RTL源文件
│   ├── testbench/            # 仿真测试平台
│   ├── constraints/          # 时序约束占位
│   ├── run_sim.sh            # Icarus Verilog仿真脚本
│   └── Makefile              # 仿真自动化Makefile
└── LICENSE                   # MIT开源协议

```

补充说明：`sky130/` 下为开源工艺基础骨架，`reram/` 下为ReRAM器件模型与宏单元，`design/` 下为RTL源码与仿真环境，`docs/` 下为全套中英文设计文档。

Note: The `sky130/` directory contains the open‑source process foundation, `reram/` contains ReRAM device models and macros, `design/` holds RTL source and simulation environment, and `docs/` contains complete bilingual design documentation.


## 获取项目 / Getting the Project

**中文**  
本项目以 ZIP 压缩包形式发布。请从 [Releases](https://github.com/yourusername/ming-she/releases) 页面下载最新版本的 `open_reram_pdk.zip`，解压后即可获得全部设计文件。

**English**  
This project is distributed as a ZIP archive. Download the latest `open_reram_pdk.zip` from the [Releases](https://github.com/yourusername/ming-she/releases) page and extract it to obtain all design files.


## 使用前必读 / Before You Start

**中文**  
1. **未硅验证**：本项目的全部器件模型、工艺规则和性能数据均为理论值，未经任何晶圆厂实际制造测试。  
2. **仅供研究**：生成的所有GDSII版图文件**不得直接提交给代工厂生产**。若需流片，必须使用官方商用PDK替换全部模型与规则。  
3. **开源协议**：本项目采用 [MIT License](LICENSE) 授权，允许自由使用、修改和分发，但需保留原始版权声明与免责条款。

**English**  
1. **Not Silicon‑Verified**: All device models, process rules, and performance data are theoretical and have not been fabricated or tested by any foundry.  
2. **Research Use Only**: Any GDSII files generated from this project **must not be submitted for physical manufacturing**. For tape‑out, you must replace all models and rules with official commercial PDKs.  
3. **License**: This project is licensed under the [MIT License](LICENSE), permitting free use, modification, and distribution, provided the original copyright notice and disclaimer are retained.


## 快速开始 / Quick Start

**中文**  
本项目已包含一套基于 Icarus Verilog 的功能仿真环境。

进入 `design/` 目录，执行以下命令即可运行基础功能仿真：

1. 确保已安装 Icarus Verilog (iverilog)。
2. 运行命令：`./run_sim.sh`
3. 仿真通过后将输出 `TEST PASSED` 提示，并生成 `tb_top.vcd` 波形文件。
4. 使用 GTKWave 查看波形：`gtkwave tb_top.vcd`

**English**  
The project includes a functional simulation environment based on Icarus Verilog.

Navigate to the `design/` directory and run the following command to start functional simulation:

1. Ensure Icarus Verilog (iverilog) is installed.
2. Run: `./run_sim.sh`
3. Upon success, `TEST PASSED` will be displayed and a `tb_top.vcd` waveform file is generated.
4. View waveform with GTKWave: `gtkwave tb_top.vcd`


## 贡献与反馈 / Contributing

**中文**  
本项目为理论探索型开放设计，欢迎通过 Issue 或 Pull Request 提出改进建议。请注意：所有贡献内容需遵循 MIT 协议，且不得引入闭源商业IP。

**English**  
This is an exploratory open‑source design. Suggestions and improvements are welcome via Issues or Pull Requests. Note that all contributions must comply with the MIT license and must not introduce closed‑source commercial IP.


## 许可证 / License

**中文**  
本项目采用 [MIT License](LICENSE) 开源协议。  
版权所有 (c) 2026 鸣蛇项目作者

**English**  
This project is open‑sourced under the [MIT License](LICENSE).  
Copyright (c) 2026 Ming She Project Authors


*最后更新 / Last Updated: 2026-04-23*
