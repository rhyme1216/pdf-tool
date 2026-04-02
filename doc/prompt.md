# 批量文档转 PDF 桌面工具 — 开发提示词手册

> 从第 1 条开始，按顺序一条一条复制执行，不要跳过。
>
> 每条提示词是一个独立的对话输入，复制代码块中的全部内容粘贴到对话框执行。

---

## 第 1 条 — 写实现计划：项目脚手架与 ZIP 解压

```
superpowers:writing-plans

请读取 doc/需求文档.md，为「项目脚手架与 ZIP 解压」编写详细实现计划。

范围包括：
- Electron 项目初始化（Main Process + Renderer Process 基本结构）
- package.json 配置（electron、electron-builder 依赖）
- 用户通过 UI 上传 .zip 文件后，在本地临时目录解压
- 递归扫描解压目录，按扩展名分类出待转换文件列表（.doc/.docx/.xls/.xlsx/.html/.md/.txt）
- 串行转换队列的骨架代码（先不实现具体转换，只搭调度框架）
- 转换完成后将输出目录重新打包为 zip 供下载

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 2 条 — 创建隔离工作空间：项目脚手架与 ZIP 解压

```
superpowers:using-git-worktrees

为「项目脚手架与 ZIP 解压」创建隔离工作空间，分支名 feature/scaffold-and-unzip
```

## 第 3 条 — 执行实现计划：项目脚手架与 ZIP 解压

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 4 条 — 代码审查：项目脚手架与 ZIP 解压

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 5 条 — 完成分支：项目脚手架与 ZIP 解压

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 6 条 — 沉淀规范：项目脚手架与 ZIP 解压

```
/opsx:propose scaffold-and-unzip-specs

将已完成的「项目脚手架与 ZIP 解压」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：ZIP 上传解压、目录递归扫描、文件分类、串行队列调度、输出打包的行为。
```

## 第 7 条 — 归档规范：项目脚手架与 ZIP 解压

```
/opsx:archive
```

---

## 第 8 条 — 写实现计划：Markdown 和 TXT 转 PDF

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §5.2 和 §5.3，为「Markdown 和 TXT 转 PDF」编写详细实现计划。

范围包括：
- Markdown 渲染为 HTML（使用 marked 或类似库），附带默认 CSS 样式保证可读性
- TXT 按每 1000 字符硬分页，包装为等宽字体 HTML，使用 CSS page-break-after 分页
- 通过 Electron 隐藏窗口加载 HTML，调用 webContents.printToPDF() 生成 PDF
- 转换成功后删除解压目录中的源文件，生成同名 .pdf
- 集成到模块 1 的串行转换队列中

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 9 条 — 创建隔离工作空间：Markdown 和 TXT 转 PDF

```
superpowers:using-git-worktrees

为「Markdown 和 TXT 转 PDF」创建隔离工作空间，分支名 feature/md-txt-to-pdf
```

## 第 10 条 — 执行实现计划：Markdown 和 TXT 转 PDF

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 11 条 — 代码审查：Markdown 和 TXT 转 PDF

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 12 条 — 完成分支：Markdown 和 TXT 转 PDF

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 13 条 — 沉淀规范：Markdown 和 TXT 转 PDF

```
/opsx:propose md-txt-to-pdf-specs

将已完成的「Markdown 和 TXT 转 PDF」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：Markdown 渲染为 HTML、TXT 按 1000 字符硬分页、Chromium printToPDF 生成 PDF、转换后删除源文件的行为。
```

## 第 14 条 — 归档规范：Markdown 和 TXT 转 PDF

```
/opsx:archive
```

---

## 第 15 条 — 写实现计划：HTML 转 PDF

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §4.2 HTML 相关部分，为「HTML 转 PDF」编写详细实现计划。

范围包括：
- 通过 Electron 隐藏窗口加载本地 HTML 文件（需处理 file:// 协议和相对路径资源引用）
- 调用 webContents.printToPDF() 生成 PDF
- 处理 HTML 中引用的本地 CSS、图片等资源的路径解析
- 转换成功后删除源文件，生成同名 .pdf
- 集成到串行转换队列

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 16 条 — 创建隔离工作空间：HTML 转 PDF

```
superpowers:using-git-worktrees

为「HTML 转 PDF」创建隔离工作空间，分支名 feature/html-to-pdf
```

## 第 17 条 — 执行实现计划：HTML 转 PDF

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 18 条 — 代码审查：HTML 转 PDF

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 19 条 — 完成分支：HTML 转 PDF

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 20 条 — 沉淀规范：HTML 转 PDF

```
/opsx:propose html-to-pdf-specs

将已完成的「HTML 转 PDF」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：加载本地 HTML、解析相对路径资源、Chromium printToPDF 生成 PDF 的行为。
```

## 第 21 条 — 归档规范：HTML 转 PDF

```
/opsx:archive
```

---

## 第 22 条 — 写实现计划：Word 和 Excel 转 PDF

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §3.3 和 §4.2，为「Word 和 Excel 转 PDF（LibreOffice headless）」编写详细实现计划。

范围包括：
- 检测本地 LibreOffice 安装路径（开发阶段先用系统安装的 LibreOffice，后续模块 9 再处理内置 Portable 版本）
- 通过 Node.js child_process 调用 soffice --headless --convert-to pdf
- 处理 .doc/.docx/.xls/.xlsx 四种格式
- 处理 LibreOffice 的超时、崩溃、非零退出码等异常情况
- 转换成功后删除源文件，生成同名 .pdf
- 集成到串行转换队列

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 23 条 — 创建隔离工作空间：Word 和 Excel 转 PDF

```
superpowers:using-git-worktrees

为「Word 和 Excel 转 PDF」创建隔离工作空间，分支名 feature/office-to-pdf
```

## 第 24 条 — 执行实现计划：Word 和 Excel 转 PDF

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 25 条 — 代码审查：Word 和 Excel 转 PDF

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 26 条 — 完成分支：Word 和 Excel 转 PDF

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 27 条 — 沉淀规范：Word 和 Excel 转 PDF

```
/opsx:propose office-to-pdf-specs

将已完成的「Word 和 Excel 转 PDF」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：LibreOffice headless 调用、超时处理、异常退出处理的行为。
```

## 第 28 条 — 归档规范：Word 和 Excel 转 PDF

```
/opsx:archive
```

---

## 第 29 条 — 写实现计划：Excel 多 Sheet 拆分

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §5.1，为「Excel 多 Sheet 拆分」编写详细实现计划。

范围包括：
- 使用 exceljs 或 xlsx 库预读 Excel 文件的 Sheet 列表
- UI 开关：关闭时整个工作簿导出为一个 PDF；开启时按 Sheet 拆分
- 拆分时命名规则：{原文件名}_{SheetName}.pdf
- SheetName 文件名安全清洗（非法字符替换为 _）
- 清洗后重名时追加 (1)、(2) 保证唯一性
- 按 Sheet 拆分时调用 LibreOffice 分别导出每个 Sheet

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 30 条 — 创建隔离工作空间：Excel 多 Sheet 拆分

```
superpowers:using-git-worktrees

为「Excel 多 Sheet 拆分」创建隔离工作空间，分支名 feature/excel-sheet-split
```

## 第 31 条 — 执行实现计划：Excel 多 Sheet 拆分

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 32 条 — 代码审查：Excel 多 Sheet 拆分

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 33 条 — 完成分支：Excel 多 Sheet 拆分

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 34 条 — 沉淀规范：Excel 多 Sheet 拆分

```
/opsx:propose excel-sheet-split-specs

将已完成的「Excel 多 Sheet 拆分」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：Sheet 预读、UI 开关控制、拆分命名规则、文件名清洗与去重的行为。
```

## 第 35 条 — 归档规范：Excel 多 Sheet 拆分

```
/opsx:archive
```

---

## 第 36 条 — 写实现计划：字体兜底与国际化

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §6 全部内容，为「字体兜底与国际化」编写详细实现计划。

范围包括：
- 内置 Google Noto 字体族（Noto Sans CJK SC、Noto Sans Latin Extended、Noto Sans Thai、Noto Sans Arabic）
- 内置 Liberation Sans/Serif/Mono、Carlito、Caladea 字体用于 LibreOffice 回退
- Electron Chromium 链路的字体注册（确保 printToPDF 时使用内置字体）
- LibreOffice 字体配置（将内置字体目录加入 LibreOffice 字体搜索路径）
- PDF 字体嵌入检测：转换完成后检查输出 PDF 是否嵌入了字体，未嵌入时生成告警日志
- 覆盖中文、英文、泰语、阿拉伯语、葡萄牙语、印尼语、越南语、匈牙利语、马来语

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 37 条 — 创建隔离工作空间：字体兜底与国际化

```
superpowers:using-git-worktrees

为「字体兜底与国际化」创建隔离工作空间，分支名 feature/font-fallback-i18n
```

## 第 38 条 — 执行实现计划：字体兜底与国际化

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 39 条 — 代码审查：字体兜底与国际化

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 40 条 — 完成分支：字体兜底与国际化

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 41 条 — 沉淀规范：字体兜底与国际化

```
/opsx:propose font-fallback-i18n-specs

将已完成的「字体兜底与国际化」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：内置字体注册、字体回退、PDF 字体嵌入检测与告警的行为。
```

## 第 42 条 — 归档规范：字体兜底与国际化

```
/opsx:archive
```

---

## 第 43 条 — 写实现计划：失败处理与日志

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §2.6，为「失败处理与日志」编写详细实现计划。

范围包括：
- 任一文件转换失败不中断批量任务，继续处理后续文件
- 失败文件在输出目录中保留原始源文件不删除
- 在输出 zip 根目录生成 error.log
- 每条失败记录包含：失败文件相对路径、文件类型、使用的转换引擎、错误信息（含堆栈/退出码/时间戳）
- 整合到已有的串行转换队列中，为每种转换引擎的错误做统一的 try-catch 和日志记录

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 44 条 — 创建隔离工作空间：失败处理与日志

```
superpowers:using-git-worktrees

为「失败处理与日志」创建隔离工作空间，分支名 feature/error-handling-logging
```

## 第 45 条 — 执行实现计划：失败处理与日志

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 46 条 — 代码审查：失败处理与日志

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 47 条 — 完成分支：失败处理与日志

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 48 条 — 沉淀规范：失败处理与日志

```
/opsx:propose error-handling-logging-specs

将已完成的「失败处理与日志」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：失败不中断、源文件保留、error.log 生成与内容格式的行为。
```

## 第 49 条 — 归档规范：失败处理与日志

```
/opsx:archive
```

---

## 第 50 条 — 写实现计划：前端 UI

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §1.2 和 §2.1，为「前端 UI」编写详细实现计划。

范围包括：
- Electron Renderer Process 中的 Web UI
- 上传 .zip 文件的拖拽/点击上传区域
- 转换进度展示（当前文件名、已完成/总数、进度条）
- 配置开关：是否按 Excel Sheet 拆分、是否保留非转换文件
- 转换完成后提供输出 zip 下载按钮
- 错误摘要展示（失败文件数量，可展开查看 error.log 内容）
- Main Process 与 Renderer Process 之间通过 IPC 通信

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 51 条 — 创建隔离工作空间：前端 UI

```
superpowers:using-git-worktrees

为「前端 UI」创建隔离工作空间，分支名 feature/frontend-ui
```

## 第 52 条 — 执行实现计划：前端 UI

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 53 条 — 代码审查：前端 UI

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 54 条 — 完成分支：前端 UI

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 55 条 — 沉淀规范：前端 UI

```
/opsx:propose frontend-ui-specs

将已完成的「前端 UI」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：ZIP 上传、进度展示、配置开关、结果下载、IPC 通信的行为。
```

## 第 56 条 — 归档规范：前端 UI

```
/opsx:archive
```

---

## 第 57 条 — 写实现计划：桌面打包与 CI/CD

```
superpowers:writing-plans

请读取 doc/需求文档.md 中 §7 全部内容，为「桌面打包与 CI/CD」编写详细实现计划。

范围包括：
- electron-builder 配置（Windows EXE/MSI、macOS DMG/APP）
- LibreOffice Portable 版本内置打包（作为 extraResources 随应用分发）
- Noto 字体包和 Liberation/Carlito/Caladea 字体包内置打包
- 应用启动时自动检测并配置内置 LibreOffice 和字体路径
- GitHub Actions CI 配置：Windows 和 macOS 双平台构建
- 构建产物自动发布到 GitHub Releases
- 预估安装包体积约 500-900MB，确认打包后各组件完整可用

要求 TDD，每个任务带完整代码、测试命令和预期结果。
```

## 第 58 条 — 创建隔离工作空间：桌面打包与 CI/CD

```
superpowers:using-git-worktrees

为「桌面打包与 CI/CD」创建隔离工作空间，分支名 feature/packaging-cicd
```

## 第 59 条 — 执行实现计划：桌面打包与 CI/CD

```
superpowers:executing-plans

执行 docs/plans/ 下最新的实现计划。每 3 个任务一批，完成后等我审核再继续。
```

## 第 60 条 — 代码审查：桌面打包与 CI/CD

```
superpowers:requesting-code-review

请对当前分支相比 main 的所有改动做一次代码审查。重点关注：安全性、错误处理、测试覆盖、与 doc/需求文档.md 的一致性。
```

## 第 61 条 — 完成分支：桌面打包与 CI/CD

```
superpowers:finishing-a-development-branch

当前模块已实现完成，请验证测试并引导我完成分支收尾。
```

## 第 62 条 — 沉淀规范：桌面打包与 CI/CD

```
/opsx:propose packaging-cicd-specs

将已完成的「桌面打包与 CI/CD」模块的行为规范沉淀为 OpenSpec specs。基于实际代码和测试，用 Given/When/Then 格式描述：electron-builder 打包、LibreOffice Portable 内置、字体内置、GitHub Actions 构建发布的行为。
```

## 第 63 条 — 归档规范：桌面打包与 CI/CD

```
/opsx:archive
```

---

## 全部完成

63 条全部执行完毕，项目开发结束。

如果后续有需求变更，从这里开始：

## 需求变更时

```
/opsx:explore

需求文档有变更：（在这里写具体变更内容）。请对照 openspec/specs/ 中已有的行为规范，分析影响范围和需要修改的模块。
```

确认影响范围后，为变更的模块重新从「写实现计划」开始走一遍同样的 7 步循环。
