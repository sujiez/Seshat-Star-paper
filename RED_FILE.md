# 红头文件 — CVPR 2027 投稿硬性要求与动笔前检查单

来源（11-16 核对）：① CVPR 2027 Author Guidelines（cvpr.thecvf.com/Conferences/2027/AuthorGuidelines，已抓全文）；
② 官方模板 author-kit tag `CVPR2027-v1` 里的 `sec/1_intro.tex`、`sec/2_formatting.tex`（格式明文）；③ 我们自己在
`Seshat-Star/docs/PAPER_FRAMING.md` / `CLAIMS.md` 里定下的写作纪律。

**用法**：每次动 `Seshat-Paper/` 下任何 `.tex` / `.bib` / 图之前，过一遍 §1–§4；动完跑 §6 的扫描命令。发现违反，
**当场 surface 给用户**，不要悄悄改句意。截止：正文 11-16 AoE（北京 11-17 19:59），补充 11-23 AoE；内部冻结 11-17 18:00 CST。

---

## §1 硬性要求（违反 = desk reject，不进评审）

| # | 要求 | 出处 | 我们的状态 |
|---|------|------|-----------|
| 1.1 | **正文 ≤ 8 页**，含图表；参考文献和 LLM Usage Statement 不计页。超页直接不审。 | AG §2；模板 1.3 | 待排版后量 |
| 1.2 | **必须有 "LLM Usage Statement"**：节名就叫这个，放正文之后、参考文献之前；披露**一切** LLM / 生成式 AI 使用（含润色、语法），写明工具名、影响的部分（文字 / 图 / 代码 / 实验 / 相关工作 / 想法）、程度；没用过就写 "No LLMs or generative AI tools were used in this work"；保持匿名。缺失即拒，漏报可转伦理委员会。 | AG §1、§2 LLM Policy | **已补 `sec/8_llm_statement.tex`**，模型名待用户确认 |
| 1.3 | **模板不得改**：不改边距、字体、字号；review 模式开 ruler + 行号（`\usepackage[review]{cvpr}`）；不要在段间加空行。 | AG §2；模板 §2 | `cvpr.sty` 与官方 kit 逐字一致 ✓ |
| 1.4 | **匿名**：无作者名、机构、致谢、基金号；不链接可识别身份的网站；引自己的工作用第三人称（"Smith et al. show"），不写 "our previous work"；**不能引用自己的公开代码库**，只能说 "code will be made publicly available"；补充材料（视频、附带论文）同样匿名。 | AG §2 Double-blind；模板 1.6 | 当前无违规 ✓；kit 已删 Paper ID 行，`main.tex` 已同步 |
| 1.5 | **外链**：正文、补充、rebuttal 都不得放"扩展内容"或"可追踪"的链接（视频页、项目页、tracker）。arXiv / 公开数据集 / 公开仓库的链接虽允许，官方建议**连参考文献里的 URL 也去掉**。→ **交互式 3D viewer 不能放外链**，只能作为补充文件打包；正文只能写 "provided as supplementary material"。 | AG §1 External links；FAQ | 当前无 URL ✓；viewer 方案改为随补充材料打包 |
| 1.6 | **引用真实性**：引用不存在的文献 / 明显事实捏造 → 拒稿，可不审。"An LLM did it" 不是辩护。占位作者（"X authors (TODO)"）提交前必须核实或删掉。 | AG §2 LLM Policy；Desk Rejection C | 11-16 核实 5 条（Disc3D、ViGiL3D++、Nanri、QuatRoPE、TDVR，标题 / 作者都有错，已改）；**3DRS、CLEVR-3D-DeRef 仍未核实** → 冻结前核实或删 |
| 1.7 | **双投**：审稿期内不得向任何会议 / 期刊 / 研讨会提交重叠 ≥ 20% 的稿件；arXiv 预印本不算发表，可以挂。 | AG §2 Dual submissions | 无 |
| 1.8 | **同期工作**：2026-09-15 之后公开的算 contemporaneous——须引用、讨论，可不比；**影响过我们的一律算 prior work**，无论何时公开。 | AG §1、§2 | TDVR (08-04)、GR3D (03-09) 都是 prior work，已引 |
| 1.9 | **数据集作为贡献**：若把数据集列为贡献，camera-ready 时必须可用；不确定就**不要**列为主要科学贡献（可以说 will be released）。 | AG FAQ Datasets | 我们是改写四个公开基准 → 要么确认能发（含 ScanNet / ReferIt3D 许可），要么贡献写成"方法 + 测量"，数据写 will be released |
| 1.10 | **无 prompt injection**（含白字、隐藏指令）。 | AG §2 | 无 |
| 1.11 | **作者名单**：abstract deadline（11-10）后不可增删；paper deadline 后不可换序；每位作者 OpenReview profile 完整、冲突填全。 | AG §2 | 用户侧 |
| 1.12 | **人类 / 个人数据**：用公开数据集时鼓励（非强制）说明采集 / 同意情况；无 IRB 需求。 | AG §2 | 可在补充材料一句话 |

## §2 模板格式明文（软性，但模板写明；审稿人会挑）

- 标题 Times 14 pt 粗体，**Title Case**（名词 / 动词 / 形容词 / 副词首字母大写，冠词 / 介词 / 连词不大写）。
- **节标题只首词大写**（"Related work"，不是 "Related Work"）；二级同；三级标题不鼓励。— 11-16 已改全部节标题。
- 公式**全部编号**；交叉引用一律 `\cref{}` / `\Cref{}`；`\eg` `\ie` `\etal` 用模板宏，`\etal` 仅 ≥ 3 作者。
- 脚注尽量不用，能括号就括号。
- 图：`\centering`，不用 `center` 环境；**图内字号与正文相当、打印可读**，不能假定读者会放大；表题在上、图题在下；短 caption 居中；9 pt 图题模板已设。
- **颜色**：不能只靠颜色区分（红绿色盲最常见），要有第二特征（文字 / 形状 / 线型）。
- 参考文献 9 pt；一处多引按数字顺序（natbib 自动）。

## §3 补充材料 / rebuttal

- 补充 11-23 AoE；格式自由（可单栏），要整洁；鼓励附代码；**论文必须自足**，不能 "require" 审稿人去看补充；正文要恰当指向补充内容。
- Rebuttal 一页，模板给定；不加新贡献 / 新实验（除非审稿人点名要）；不放链接；匿名。

## §4 我们自己的写作纪律（PAPER_FRAMING / CLAIMS）

- **对角线数（C4：44.6 → 65.9 等）必须和 C1 / C2 一起讲**，不能单飞。
- **不并排不同协议的分数**（TDVR 的 Mask3D 框 + box IoU vs 我们的掩码 IoU；GPT-6 E5 的 GT 候选 + 最难子集 vs 它的全 val）；**不写没有证据的指控**（如"挑挑拣拣修补出来的分"）。
- 每个数字可回溯到 `Seshat-Star/RESULTS.md` 或 `_transfer/incoming/paper_materials_1113/`；写进正文的数先对一遍。
- `\TODO{}` 冻结前**逐条清零**；禁止用 `\renewcommand{\TODO}[1]{}` 一键隐藏——那是把没核的话直接交出去。
- 图字号规则：teaser 排到 6.875 in 宽缩 0.49 倍，图内 ≥ 11 pt（成稿 ≥ 5.4 pt）。**注意这低于模板"与正文相当"的要求**（正文 10 pt、图题 9 pt），审稿人可能挑；能放大就放大，密度不够就删内容。
- 措辞：尺子里 GPT 只是翻译器（句子 → 谓词），exact 由确定性求值器算，不写"再跑一遍尺子"；E5 里 GPT-6 是端到端答题者。
- 信息密度递增：teaser caption 最简 → intro → related → method / experiment；凡图里能直接看出的，caption 不写。
- **层级不复述**：上一层（摘要 → intro → related → method / 实验）说过的话，下一层不重说——原句不许，同义句也不许；一个小从句带过，然后给上一层没有的细节。唯一例外：重大数据结果可在 method / 实验节再出现，用来带出更细的数（总数 → 分层 / 拆分项）。
- 细微的措辞强弱不必逐条 surface（用户 11-16）；只报 §1 硬性项和本节纪律项。
- **全篇英式拼写**（用户 11-16）：colour / centre / neighbour / metre / grey / labelled / judgement / learnt / towards，-ise 不用 -ize。例外只有两类原样保留：引用的数据原句（如 teaser 里模型写的 "neighboring"）和参考文献标题。

## §5 当前稿件检查结果（11-16，按 §1–§2 扫）

| 项 | 结果 | 处置 |
|----|------|------|
| LLM Usage Statement | **缺失** | 已加 `sec/8_llm_statement.tex`，`main.tex` 已挂；模型名待确认 |
| 参考文献占位作者 | 7 条含 TODO | 5 条已核实改正；3DRS、CLEVR-3D-DeRef 未核实 → 冻结前处理 |
| Paper ID 行 | kit 已删 | `main.tex` 已删 |
| 节标题大小写 | 6 处 Title Case | 已改首词大写 |
| URL / 外链 | 无 | ✓（viewer 方案见 1.5） |
| 匿名用语 | 无 "our previous" 等 | ✓ |
| `\TODO` 数 | 正文 12 处 + bib 若干 | 冻结前清零 |
| 图内字号 | teaser 最小 ≈ 5.4 pt 成稿 | 已知偏小，接受或再删内容 |
| 页数 | 未量（正文未写完） | 排版后量；参考文献不计 |
| 数据集贡献措辞 | intro 贡献项待定 | 见 1.9 |

## §6 动笔后扫描命令（在 `Seshat-Paper/` 下）

```bash
rg -n -i 'http|\\url|github|website' sec main.tex fig/*.tex main.bib          # 外链
rg -n -i 'acknowledg|our (previous|prior|earlier) (work|paper)|we previously|under submission|grant' sec   # 匿名
rg -n -i 'LLM Usage Statement' sec main.tex                                      # 声明在
rg -n -i 'TODO' main.bib; rg -c 'TODO' sec/*.tex fig/*.tex                       # 占位 / 待核
rg -n '\\(sub)*section\{[a-z]*[ -][A-Z]' sec                                    # 节标题多余大写
rg -n 'e\.g\.|i\.e\.|et al\.' sec                                                # 应改用 \eg \ie \etal
rg -n -i -w 'colors?|colored|centers?|neighbors?|neighboring|meters?|gray|labeled|judgments?|learned|toward|analyze[sd]?|behaviors?|[a-z]{3,}(ize[sd]?|izing|ization)' sec fig/*.tex tab | rg -v ':[0-9]+:%'   # 美式拼写（全篇英式；有输出即异常）
```
