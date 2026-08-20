# Job Application Manage Skill

[简体中文](README.md) | [English](README.en.md)

![Job application management workflow hero](assets/job-application-manage-hero.jpg)

A reusable Codex skill for turning recruiting emails, applicant portals, job pages, and user notes into one prioritized application pipeline.

## What it does

- Reconciles and deduplicates job applications from multiple sources.
- Ranks records as P0–P3 and puts important active items first.
- Separates upcoming actions, overdue follow-ups, active applications, offers, not-matched results, closed cases, expired cases, and planned applications.
- Preserves exact official status wording and asks the user instead of inventing missing facts.
- Syncs or exports to Feishu, Notion, Excel, GitHub Markdown, portable Markdown, and other cloud spreadsheets, databases, or documents.
- Supports Chinese, English, or optional bilingual presentation.
- Enforces deterministic category order, two-row spacing where supported, and a restrained single-color layout.

## Tracker example

The following table uses fictional companies and example dates:

| Category | Company | Target Role | Priority | Status & Next Action | Location | Application Date | Key Timeline |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Priority Actions | Example Tech | AI Algorithm Engineer | P0 / Urgent | Interview invitation; confirm and prepare | Guangzhou | 2026-08-01 | 2026-08-25 14:00 video interview |
| Upcoming Actions | Example Bank | Backend Engineer | P2 / Normal | Assessment confirmed; attend on time | Shenzhen | 2026-08-08 | 2026-08-28 19:00 online assessment |
| Not Matched | Example Retail | Data Engineer | P3 / Low | Not matched; no action required | Guangzhou | 2026-08-03 | 2026-08-20 portal status update |
| Planned Applications | Example Energy | Digital Engineer | P2 / Normal | Not submitted; verify role and deadline | Guangzhou | — | Deadline to confirm |

When writing to a cloud document, the skill uses category rows, grouped views, or an explicit Category field according to the target platform. It keeps exactly two blank rows between categories when physical rows are supported.

## Examples

### Update a tracker from recruiting email

```text
Use $job-application-manage-skill to check recruiting emails from the last 14 days, deduplicate the applications, rank important actions first, and update my Feishu tracker.
```

### Reconcile official portal statuses

```text
Check the application statuses in these official applicant portals. Preserve the exact official wording, move not-matched applications into their own category, and ask me about anything uncertain before editing the tracker.
```

### Build a city-first application plan

```text
Add my planned applications to the tracker and recommend suitable roles. Prioritize Guangzhou and roles with a calmer work pace. Mark workload judgments as inference.
```

### Separate urgent, upcoming, and overdue actions

```text
Reorganize the tracker by importance. Put interviews and deadlines within seven days under priority actions, separate future events from overdue follow-ups, and keep exactly two blank rows between categories.
```

### Export to multiple formats

```text
Synchronize the normalized tracker to Notion and export copies as Excel, GitHub-flavored Markdown, and portable Markdown. Keep the current Feishu tracker as the canonical source.
```

### Use optional bilingual labels

```text
Update the tracker using optional Chinese/English labels, while preserving the original language of official application statuses.
```

## Install

Copy the `job-application-manage-skill` folder into your Codex skills directory:

```text
~/.codex/skills/job-application-manage-skill
```

Then ask Codex to use `$job-application-manage-skill` to inspect recruiting updates and maintain your tracker.

## Privacy

The repository contains no personal tracker URLs, mailbox addresses, credentials, or application records. Keep private values in your local `references/user-config.md` and review repository visibility before publishing any generated tracker.
