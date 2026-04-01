# pdf-tool

批量文档转 PDF 桌面工具。

## 架构概览

![架构概览](doc/images/architecture-overview.png)

## 技术选型

### 桌面框架：Electron

Electron 自带 Chromium，可直接复用 `printToPDF()` 完成 HTML / Markdown / TXT → PDF 转换，无需额外打包 headless Chrome。Tauri 目前没有 `printToPDF` API（feature request 自 2022 年至今未实现），不适合本项目。

### Office 文档转换：LibreOffice headless（全平台统一）

所有平台（Windows / macOS）统一使用 LibreOffice headless 转换 Word 和 Excel 文件，不走 Windows COM 自动化路径。原因：

- 微软官方不推荐、不支持非交互环境下的 Office COM 自动化
- COM 自动化存在模态对话框挂死、单线程不可重入、需要 Office 授权等问题
- LibreOffice 在 Windows 上可直接使用系统已安装的 Microsoft 字体，转换效果接近原生 Office
- 统一引擎 = 一份代码路径，维护成本大幅降低

纯库方案（pandas、python-docx、Node.js docx-pdf 等）均无法满足排版保真度要求：它们是数据解析器而非渲染引擎，无法保留格式、图表、合并单元格、图片等。

### HTML / Markdown / TXT 转换：Electron 内置 Chromium

利用 Electron 的 `webContents.printToPDF()`，字体自动嵌入（Skia PDF 后端自动子集化嵌入）。PRD 要求串行队列不并发，恰好避开了 Electron 在并发场景下的性能劣势。

### 引擎选择决策

![引擎选择决策](doc/images/engine-decision-tree.png)

### 内置字体：Google Noto 字体族

| 语言 | 字体 | 大小估算 |
|------|------|----------|
| 中文 | Noto Sans CJK SC | ~16MB |
| 英文 / 葡萄牙语 / 越南语 / 印尼 / 马来 / 匈牙利 | Noto Sans (Latin Extended) | ~1MB |
| 泰语 | Noto Sans Thai | ~0.5MB |
| 阿拉伯语 | Noto Sans Arabic | ~0.5MB |

LibreOffice 字体回退补充（macOS / Linux）：

| 缺失的 Microsoft 字体 | 替代字体（度量兼容） |
|------------------------|---------------------|
| Calibri | Carlito |
| Cambria | Caladea |
| Arial | Liberation Sans |
| Times New Roman | Liberation Serif |
| Courier New | Liberation Mono |

### 转换流程

![转换流程](doc/images/conversion-flowchart.png)

## 支持的文件类型

| 类别 | 扩展名 | 转换引擎 |
|------|--------|----------|
| Word | `.doc` `.docx` | LibreOffice headless |
| Excel | `.xls` `.xlsx` | LibreOffice headless |
| HTML | `.html` | Electron Chromium printToPDF |
| Markdown | `.md` | Markdown → HTML → Chromium printToPDF |
| 纯文本 | `.txt` | 1000 字符分页 → HTML → Chromium printToPDF |

## 文档

- [产品需求文档 (PRD)](doc/需求文档.md)
