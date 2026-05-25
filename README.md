# 院系导师研究方向雷达

[English Version](./README.en.md)

`department-advisor-research-radar` 是一个可复用的 Codex/Claude 风格 skill，用来调研某个大学、院系、专业或学科方向下全部教师/导师的最新公开研究方向。

它特别适合这种场景：官网教师页还能拿来确认名单和身份，但内容已经偏旧，真正想知道的是“这些老师最近几年到底在做什么研究”。

这个 skill 的核心思路不是照抄官网简介，而是综合多源公开证据进行校正，包括：
- 近 3-5 年论文与期刊页
- ORCID / Google Scholar / 实验室主页
- 学院新闻、论著报道、讲座和项目页面
- 必要时参考 X-MOL、ResearchGate、AMiner、百度学术等二级聚合源

## 它能产出什么

这个 skill 目标是生成一份结构化 Markdown 报告，包含：
- 已核实的教师 roster
- 每位老师一段基于证据的“当前研究方向画像”
- 关键研究关键词
- 代表性近年证据
- 信息不足时的明确保守提示
- 可追溯的来源链接

## 为什么这个 skill 有价值

很多院系官网并不是“完全没用”，而是：
- 适合做 roster anchor 和身份确认
- 不适合直接当成“当前研究方向”的最终结论

这个 skill 把更稳妥的流程固定下来：
先用官网锁定边界和名单，再用更新、更强的一手公开证据去重建每位老师当前真正活跃的研究主题。

## 仓库结构

```text
department-advisor-research-radar/
  SKILL.md
  assets/
  references/
dist/
  department-advisor-research-radar.skill
```

## 仓库内容

- `department-advisor-research-radar/SKILL.md`
  核心 skill 定义、触发条件与执行工作流

- `department-advisor-research-radar/references/source-priority.md`
  信息源优先级、冲突处理与弱证据处理规则

- `department-advisor-research-radar/references/report-format.md`
  最终 Markdown 报告格式规范

- `department-advisor-research-radar/references/fudan-psychology-example.md`
  复旦大学心理学系案例，用来展示这个 skill 在真实院系上的执行方式

- `department-advisor-research-radar/assets/department_advisor_research_radar_input_template.md`
  可复用输入模板

- `department-advisor-research-radar/assets/department_advisor_research_radar_report_template.md`
  可复用输出模板

- `dist/department-advisor-research-radar.skill`
  已打包好的 skill 文件，可直接分发或安装

## 适用场景

- 调研某个学校某个专业全部老师最近的研究方向
- 做申请季导师筛选或套磁前的信息整理
- 理解一个院系内部的研究主题分布
- 用近年公开证据修正官网过旧的教师画像

## 重新校验与打包

如果你本地也有 skill-creator 工具链，可以这样重新校验和打包：

```powershell
$env:PYTHONUTF8='1'
python C:\Users\ASUS\.agents\skills\skill-creator-0.1.0\scripts\quick_validate.py .\department-advisor-research-radar
python C:\Users\ASUS\.agents\skills\skill-creator-0.1.0\scripts\package_skill.py .\department-advisor-research-radar .\dist
```

## 使用提醒

- 这个 skill 做的是“公开证据下的当前研究方向重建”，不是招生承诺判断。
- 是否当年招生、是否收推免/直博/RA，仍应以最新招生通知或老师回复为准。
