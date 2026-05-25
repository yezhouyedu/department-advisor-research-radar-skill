# Department Advisor Research Radar

[中文版](./README.md)

`department-advisor-research-radar` is a reusable Codex/Claude-style skill for investigating the latest public research directions of all faculty members or advisors in a target university department, program, major, or discipline cluster.

It is especially useful when official faculty pages are still good enough for roster and identity verification, but too stale to answer the real question: what is each faculty member actively working on in recent years?

Instead of copying faculty bios, this skill triangulates across multiple public evidence sources, including:
- papers and journal pages from the last 3-5 years
- ORCID / Google Scholar / lab pages
- school news, publication highlights, talks, and project pages
- secondary aggregators such as X-MOL, ResearchGate, AMiner, and Baidu Scholar when needed

## What It Produces

The skill is designed to generate a structured Markdown report with:
- a verified faculty roster
- one evidence-based current research profile per faculty member
- research keywords
- representative recent evidence
- explicit caution notes when evidence is sparse
- traceable source links

## Why This Skill Exists

Many department websites are not useless, just limited:
- they are often still good roster anchors
- they are often not reliable as the final authority on current research direction

This skill formalizes a better workflow:
use the official site to lock scope and identity, then reconstruct each faculty member's current active topics from newer and stronger public evidence.

## Repository Structure

```text
department-advisor-research-radar/
  SKILL.md
  assets/
  references/
dist/
  department-advisor-research-radar.skill
```

## Repository Contents

- `department-advisor-research-radar/SKILL.md`
  Core skill definition, trigger conditions, and execution workflow

- `department-advisor-research-radar/references/source-priority.md`
  Evidence ranking, conflict handling, and sparse-evidence rules

- `department-advisor-research-radar/references/report-format.md`
  Final Markdown report format

- `department-advisor-research-radar/references/fudan-psychology-example.md`
  A real example based on Fudan University psychology faculty mapping

- `department-advisor-research-radar/assets/department_advisor_research_radar_input_template.md`
  Reusable input template

- `department-advisor-research-radar/assets/department_advisor_research_radar_report_template.md`
  Reusable output template

- `dist/department-advisor-research-radar.skill`
  Packaged skill artifact ready for sharing or installation

## Use Cases

- Survey all faculty members in a department and map their latest research directions
- Build an advisor-targeting report for graduate applications
- Understand topic clusters within a program
- Update stale official faculty profiles with recent public evidence

## Revalidate And Repackage

If you have the local skill-creator toolchain, you can rebuild with:

```powershell
$env:PYTHONUTF8='1'
python C:\Users\ASUS\.agents\skills\skill-creator-0.1.0\scripts\quick_validate.py .\department-advisor-research-radar
python C:\Users\ASUS\.agents\skills\skill-creator-0.1.0\scripts\package_skill.py .\department-advisor-research-radar .\dist
```

## Notes

- This skill reconstructs current research directions from public evidence; it does not guarantee recruitment status.
- For admissions-related decisions, always verify current recruiting status through official notices or direct faculty contact.
