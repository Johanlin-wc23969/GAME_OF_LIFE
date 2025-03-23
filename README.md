# 项目简介
本项目旨在探索如何利用并发与分布式架构模拟简单规则下涌现出的复杂行为。我们使用 Go 语言实现核心逻辑，支持在本地多线程执行，也可扩展至多台节点联合运算。

项目特色包括：

模块化架构：分为 core, check, sdl, util, broker, awsNode 等模块

高性能调度：通过 Goroutine 实现局部区域并行计算

分布式支持：具备节点分配、通信协议与结果聚合逻辑

完善测试体系：多个 _test.go 覆盖核心功能模块

数据分析与可视化：输出 CSV 与 Python 脚本 plot.py 用于性能评估图表生成

---

## 目录结构概览
```
.
├── gol/             # 核心 Game of Life 规则实现
├── broker/          # 分布式节点协调逻辑
├── awsNode/         # 云部署节点逻辑
├── sdl/             # 使用 SDL 进行图形化渲染（可选）
├── check/           # 状态验证与规则一致性检查
├── util/            # 辅助工具函数
├── images/          # 渲染输出图像
├── out/             # 中间状态或结果文件输出
├── LICENSE
├── README.md
├── go.mod / go.sum  # Go module 配置
├── *.go             # 包括主程序和单元测试
├── plot.py          # 使用 matplotlib 绘图
├── results.csv      # 性能或状态统计

````

---

## 快速开始
依赖要求
- Go ≥ 1.17

- Python ≥ 3.6（用于性能绘图，依赖 matplotlib）

- SDL2（如使用图形可视化）

---

## 测试
支持模块化测试，包括：
```
测试 Gol 模块（核心生命游戏逻辑）
go test -v -run TestGol/-1$

测试 Alive 状态判断逻辑
go test -v -run TestAlive

测试 PGM 图片输出
go test -v -run TestPgm/-1$

测试键盘交互
go test -v -run TestKeyboard -sdl

测试基准性能
benchmark_test.go

测试工具函数与状态跟踪
util_test.go, trace_test.go
```

---

## 可视化 & 性能分析
使用 results.csv 输出每轮模拟耗时等数据
plot.py 可将 results.csv 绘制为可视化图表

---

## 技术栈
技术栈（Tech Stack）
| 分类 | 技术 | 说明 |
|:-----|:----|:-----|
| 编程语言 |	Go|	核心逻辑、多线程、RPC 通信 |
| 可视化 |	SDL2 | 图形渲染 |
| 测试 & 性能评估 | Go Testing Framework | 单元测试 & 基准测试（Benchmark）
| 数据处理 |	Python (Matplotlib)	| 结果数据绘图
| 分布式计算 |	Goroutines + 自定义 RPC	|节点通信和状态同步
| 构建管理	 | Go Modules |	包管理与依赖版本控制
