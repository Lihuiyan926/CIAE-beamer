# CIAE Beamer 幻灯片模板

适用于中国原子能科学研究院（CIAE，及通用学术场合）的 LaTeX Beamer 演示模板，支持中文排版，内置配色、文本框、代码高亮等常用元素。

---

## 效果预览

编译 `slide.tex` 后即可得到示例 PDF，包含封面、目录、内容页、章节过渡页和致谢页。

---

## 文件结构

```
.
├── slide.tex          # 主文档，在此编辑演示内容
├── DLUT.sty           # 主题样式（一般无需修改）
├── ref.bib            # 参考文献数据库
├── logo.png           # 封面 & 致谢页右上角徽标
├── background1.png    # 封面 & 致谢页背景横幅
├── seccon.png         # 章节过渡页背景
└── pic/
    └── logo_ciae.png  # 页眉左侧小徽标
```

---

## 环境要求

| 依赖 | 说明 |
|------|------|
| XeLaTeX | 必须使用 XeLaTeX 编译，不支持 pdfLaTeX |
| 微软雅黑字体 | Windows 系统自带；Linux/macOS 需手动安装或替换字体 |
| latexmk（推荐） | 自动处理多次编译，省去手动重复执行 |

---

## 编译方式

**推荐：使用 latexmk 自动编译**

```bash
latexmk -xelatex slide.tex
```

**手动编译（需执行三次）**

```bash
xelatex slide.tex
xelatex slide.tex
xelatex slide.tex
```

> 目录、TikZ 覆盖层等交叉引用需多次编译才能完全正确定位。

**含参考文献时的完整流程**

```bash
xelatex slide.tex
bibtex slide
xelatex slide.tex
xelatex slide.tex
```

---

## 快速上手

### 1. 修改封面信息

编辑 `slide.tex` 头部：

```latex
\author[简称]{汇报人全名}
\title{报告主标题}
\subtitle{报告副标题}
\institute[单位简称]{单位全称}
\date{\today}
```

### 2. 添加章节与内容

```latex
\setsectionsubtitle{English Subtitle}   % 章节过渡页副标题（可选）
\section{章节名称}

\begin{frame}{幻灯片标题}
    % 在此编写内容
\end{frame}
```

### 3. 使用高亮文本框

```latex
\begin{aim*}{框标题}{}
    内容……
\end{aim*}
```

### 4. 致谢页

```latex
\makethankspage                    % 默认文字
\makethankspage[自定义感谢语]      % 自定义文字
```

---

## 配色说明

主题色 `deepblue` 取自院徽 `logo.png` 的主色调。

| 颜色名 | RGB 值 | 用途 |
|--------|--------|------|
| `deepblue` | (51, 70, 139) | 文本框边框、列表符号、关键词高亮 |
| `deepred` | (153, 0, 0) | 强调词、代码自定义高亮 |
| `deepgreen` | (0, 128, 0) | 代码字符串 |
| `halfgray` | gray 55% | 代码行号 |
| `tsinghua` | (0, 78, 162) | 页脚、页眉、结构色 |

如需添加自定义颜色，在 `slide.tex` 头部追加：

```latex
\definecolor{mycolor}{RGB}{r,g,b}
```

然后在正文中通过 `\textcolor{mycolor}{文字}` 调用。

---

## 替换为其他单位的视觉形象

| 文件 | 作用 | 建议尺寸 |
|------|------|----------|
| `logo.png` | 封面 & 致谢页右上角徽标 | 高度约 1.4 cm，透明背景 |
| `background1.png` | 封面 & 致谢页横幅背景 | 与幻灯片等宽（16:9） |
| `seccon.png` | 章节过渡页背景 | 与幻灯片等宽（16:9） |
| `pic/logo_ciae.png` | 每页页眉左侧小图标 | 高度约 0.6 cm，透明背景 |

替换图片后重新编译即可。

---

## 常见问题

**Q: 编译报错"字体找不到"**  
A: 确认系统已安装微软雅黑字体，或在 `DLUT.sty` 中将 `微软雅黑` 替换为已安装的中文字体（如 `Noto Sans CJK SC`）。

**Q: 目录 / 页码显示不正确**  
A: 确保执行了至少三次 XeLaTeX 编译，或使用 `latexmk -xelatex`。

**Q: 特殊字符编译出错**  
A: `%`、`$`、`&`、`#` 等字符需转义，写作 `\%`、`\$`、`\&`、`\#`。

---

## 许可

本模板仅供学习与非商业用途，图片资源（徽标、背景）版权归中国原子能科学研究院所有，使用前请替换为您有权使用的素材。
