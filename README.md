![微信图片_20250301131222](https://github.com/user-attachments/assets/bd506944-e216-4023-9da1-2796e536883c)![image](https://github.com/user-attachments/assets/bdcd85df-dc9c-4c98-8f42-9ae367ea8b09)以下是README.md的内容建议，采用简洁清晰的结构：

# 日志查看器 - LogViewer

一个基于Qt开发的轻量级日志查看工具，支持实时监控、关键词过滤和错误高亮功能。

![界面截图](截图URL) <!-- 建议实际运行时补充截图 -->

## 主要功能

✅ **核心特性**
- 实时监控日志文件变化（支持.log和任意文本文件）
- 三列式解析显示（时间 | 等级 | 内容）
- 关键词即时过滤（支持回车或按钮触发）
- 错误日志行自动红色高亮
- 自适应窗口大小调整
- 多线程文件读取（UI无卡顿）

📊 **数据显示**
- 自动截断长路径显示（鼠标悬停查看完整路径）
- 支持10行缓冲加载（优化大文件性能）
- 分页显示过滤结果

## 快速开始

### 预编译版本
1. 从[Release页面](链接)下载对应系统的压缩包
2. 解压后运行：
     Windows下
   双击LogViewer.exe
   # Linux下
   ./LogViewe

### 从源码构建
**环境要求**：Qt 5.15+ 且包含C++17编译器

  ```bash
git clone https://github.com/yourusername/LogViewer.git
cd LogViewer
qmake && make

## 使用指南

### 界面布局
```
[打开文件按钮] [路径显示标签]      [过滤按钮]
+------------------------------------------+
|              日志表格视图                |
| (时间列 | 等级列 | 内容列)               |
+------------------------------------------+
[过滤输入框]
```

### 操作说明
1. **打开文件**：点击左上角按钮选择.log文件
2. **实时监控**：文件修改后自动加载新内容
3. **过滤日志**：
   - 在底部输入框键入关键词（如"ERROR"）
   - 点击过滤按钮或按回车执行
   - 清空输入框并回车显示全部内容
4. **错误识别**：包含"ERROR"的行自动红色背景高亮

## 技术实现

### 架构设计
graph LR
A[FileReader线程] -->|推送新日志| B(LogModel)
B -->|数据更新| C[TableView]
D[文件监控] -->|变化通知| A
E[过滤输入] -->|关键词| B
```

        ### 关键技术
- **Qt框架**：信号槽机制实现组件通信
- **Model-View架构**：自定义LogModel处理数据逻辑
- **多线程**：QThread分离文件I/O与UI操作
- **文件监控**：QFileSystemWatcher实时检测变更

      ## 注意事项

       **已知限制**
1. [时间] | [等级] | [内容]
2. 超大文件（>1GB）可能影响性能

         **使用建议**
- 对持续增长的日志文件支持最佳
- 过滤时使用明确关键词提升性能
- 支持文本复制操作

From：
  争当牛马的hahazz！！

---
