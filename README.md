# 冯如杯创意赛道 $\LaTeX$ 模板 （非官方）

本项目由 [Pannenets.F](https://github.com/PannenetsF) 创建，目前由[zyy](https://github.com/ZouYuyang)维护，适用于32届冯如杯创意赛道，经过修改后应也适用于之后届次比赛。

- [冯如杯创意赛道 $\\LaTeX$ 模板 （非官方）](#冯如杯创意赛道-latex-模板-非官方)
  - [项目起源](#项目起源)
  - [项目 Flag（原文）](#项目-flag原文)
  - [使用平台（原文）](#使用平台原文)
  - [编译方式（原文）](#编译方式原文)
  - [文件组织（原文）](#文件组织原文)
  - [冯如杯格式审查（原文）](#冯如杯格式审查原文)
  - [Bug 反馈](#bug-反馈)
  - [License](#license)

## 项目起源

原文：本人曾基于 [Someday-XeLaTex-Template](https://github.com/Somedaywilldo/Someday-XeLaTex-Template) 进行调整，最终完成 [FRB Template](https://github.com/PannenetsF/FRB-Template) ，并且借此通过了学院初审以及学校审核，未出现格式问题。

![](figures/pass.png)

但是由于该项目未完成类文件 `.cls` ，并且使用大量未经注释的命令，存在较多的问题，调整较为耗时耗力，并且存在在某些时候通过该模板进行基础物理实验报告的重写需求，出于以上目的对其进行**完全**重构。

修改者zyy使用本模板参加了第三十二届冯如杯创意赛道竞赛，未出现格式问题。

## 项目 Flag（原文）

1. 完成基本的 `.cls` `.bib` 文件，规范冯如杯格式与引用 (已完成)
2. 提供一些简单的 trick (已完成)

## 使用平台（原文）

测试平台为 Manjaro 网络安装 TeX Live 2020 ，基于 `xelatex` 与 `bibtex`。

## 编译方式（原文）

请注意本步骤需要您先将相关字体复制到 `fonts` 文件夹内，请参考下一小节。

zyy注：建议使用Overleaf进行在线编辑。TeX Live版本2019-2021测试均无较大问题。

原文：

- 通过 `xelatex -> bibtex -> xelatex * 2`
- 直接 `latexmk -xelatex frb.tex` （简单，推荐）
- 直接使用脚本/批处理文件
  - Windows：双击 `compile.bat`
  - Linux/Mac: `chmod +x compile.sh && ./compile.sh` 

## 文件组织（原文）

以下是本项目需要的文件结构。

- 图片：放在 `figures` 文件夹下可以直接 `\figref` ，如 `\figref{buaa.png}`而无需`\figref{figures/buaa.png}` 
- 章节：如有分章节需要，将单独的 section 放在 `chap` 文件夹下，通过 `\input` 导入主文档。
- 引用：在 `frbrefer.bib` 中添加 bib 条目

```
.
├── chap
├── figures
│   ├── buaa.png
│   ├── buaa-symbol.png
│   └── pass.png
├── fonts
│   ├── FZCSK.TTF
│   ├── FZFSK.TTF
│   ├── FZHTK.TTF
│   ├── FZKTK.TTF
│   ├── FZSSK.TTF
│   ├── HWXW.TTF （请自行复制到本文件夹并重命名）
│   └── HWZS.TTF （请自行复制到本文件夹并重命名）
├── frbpaper.cls
├── frb.pdf
├── frbrefer.bib
├── frb.tex
├── gbt7714-plain.bst
├── gbt7714.sty
├── gbt7714-unsrt.bst
├── LICENSE
└── README.md
```


## 冯如杯格式审查（原文）

| 项目     | 要求                                                                   | 检查 |
| -------- | ---------------------------------------------------------------------- | ---- |
| 论文题目 | 二号 华文中宋 加粗 居中                                                | 完成 |
| 副标题   | 三号 华文新魏 居右 可省略                                              | 完成 |
| 章节标题 | 三号 黑体 居中                                                         | 完成 |
| 小节标题 | 四号 黑体 居左                                                         | 完成 |
| 小条标题 | 小四号 黑体 居左                                                       | 完成 |
| 正文     | 小四号 宋体 Times New Roman 首行缩进 两端对齐                          | 完成 |
| 页码     | 五号 数字字母 Times New Roman                                          | 完成 |
| 页边距   | 上下左右 25 25 30 20 mm                                                | 完成 |
| 标题行距 | 三级标题为单倍行距，段前段后各 0.5 行                                  | 完成 |
| 正文行距 | 1.5 倍行距 段前段后无空行                                              | 完成 | 
| 页眉     | 小五 宋体 居中 正文开始                                                |完成      |
| 页码     | 正文开始 页脚居中 五号 摘要目录 图表清单 符号表用5号罗马数字           |    完成  |
| 图表附注 | 题目五号宋体/TNR加粗 图编号与图题直接空半角2格 ，若有附注，注明 附注1: | 附注可在提供的环境中自行设置     |
| 封面     | 主题不超过25汉字，副标题加破折号                                       |  完成    |
| 摘要     | 摘要正文，关键词                                                       | 完成     |
| 目录     | 三级/二级 包括绪论，主体，附录，参考文献                               |  完成    |
| 主体     | 三层，一、 (一) 1.                                                     | 目前来看很少有用这种形式的，大多用 第一章 1.1 1.1.1 这种（并且都过了）     |
| 结论     | 单独分一章，但是不加章节号                                             | 用`\section*{}`即可     |
| 参考文献 | 不需要标注文献标识码                                                   | 在 bib 中去掉即可     |
| 正文引用 | 小四号上标 [1]                                                         |  很不理解，正文是小四，上标也是小四？欢迎讨论    |


## Bug 反馈

请提 Issue （推荐） 或者邮件联系原作者： [pannenets.f@foxmail.com](mailto:pannenets.f@foxmail.com)，或修改者：[zouyuyang@buaa.edu.cn](mailto:zouyuyang@buaa.edu.cn)

## License

本项目采用 BSD 3-Clause License .


