# HW_WS_Template

一个轻量级的 LaTeX 类，用于创建数学练习表，支持可选的答案版本。一个源文件即可生成学生版和教师版。

## 特性

- **单一源文件**：一个 `.tex` 文件生成学生版和答案版
- **切换答案**：使用 `[answers]` 选项显示/隐藏答案
- **自动页眉**：自动显示课程/机构信息的页眉
- **智能间距**：`\blankspace` 在学生版显示空白，在答案版自动隐藏
- **子问题**：`parts` 环境支持 a), b), c) 编号
- **简洁样式**：蓝色问题标签 (Q1, Q2...)，红色答案标签
- **页码**：页脚自动显示页码
- **无段落缩进**：文本左对齐，整洁美观

## 快速开始

```latex
\documentclass{worksheet}  % 学生版
% \documentclass[answers]{worksheet}  % 答案版

\coursename{Linear Algebra}
\coursecode{Math 257}
\institution{Your University}
\professor{Prof. Name}
\semester{Fall 2026}
\wsnumber{1}

\begin{document}
\makeworksheettitle

\begin{question}
    What is $2+2$?
    \blankspace{5em}
\end{question}

\begin{answer}
    The answer is 4.
\end{answer}

\end{document}
```

## 命令

| 命令 | 说明 |
|---------|-------------|
| `\coursename{...}` | 设置课程名称 |
| `\coursecode{...}` | 设置课程代码 |
| `\institution{...}` | 设置机构名称 |
| `\professor{...}` | 设置教授姓名 |
| `\semester{...}` | 设置学期 |
| `\wsnumber{...}` | 设置练习表编号 |
| `\makeworksheettitle` | 生成标题 |
| `\blankspace{length}` | 添加空白（答案版自动隐藏） |

## 环境

```latex
% 问题环境
\begin{question}
    问题内容...
\end{question}

% 带副标题的问题
\begin{question}[Bonus]
    问题内容...
\end{question}

% 子问题
\begin{parts}
    \item 第 a 问
    \item 第 b 问
    \item 第 c 问
\end{parts}

% 答案环境
\begin{answer}
    答案内容...
    % 答案中也可以使用子问题
    \begin{parts}
        \item 第 a 问答案
        \item 第 b 问答案
    \end{parts}
\end{answer}
```

## 与系统 `homework` 类的对比

TeX Live 自带的 `homework` 类有不同的样式：

| 特性 | `worksheet.cls` (本模板) | 系统 `homework` |
|---------|----------------------|-------------------|
| 问题标签 | Q1, Q2, Q3 (蓝色) | Problem 1, 2, 3 |
| 答案标签 | Answer: (红色) | Solution (下划线) |
| 标题位置 | 居中 | 右上角 |
| QED 符号 | 无 | 方形标记 |
| 页码 | 底部中央 | 底部右侧 |
| 切换答案 | `[answers]` 选项 | `[hide-solution]` 选项 |
| 答案中的子问题 | ✅ 支持 | ✅ 支持 |

查看 `example_hw.tex` 了解系统 `homework` 类的格式。

## 文件结构

```
.
├── worksheet.cls      # 主练习表类文件
├── example_ws.tex     # 练习表示例
├── example_ws.pdf     # 编译后的练习表
├── example_hw.tex     # 系统 homework 类示例
├── example_hw.pdf     # 编译后的 homework
├── README.md          # 英文文档
└── README_zh.md       # 中文文档
```

## 编译

```bash
pdflatex example_ws.tex
pdflatex example_hw.tex
```

## 依赖

- LaTeX 发行版 (TeX Live, MiKTeX 等)
- 宏包：`amsmath`, `amssymb`, `amsthm`, `xcolor`, `geometry`, `fancyhdr`, `enumitem`

## 许可证

MIT
