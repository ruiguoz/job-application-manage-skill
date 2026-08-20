# Job Application Manage Skill

[English](README.md) | [简体中文](README.zh-CN.md)

A reusable Codex skill for turning recruiting emails, applicant portals, job pages, and user notes into one prioritized application pipeline.

## What it does

- Reconciles and deduplicates job applications from multiple sources.
- Ranks records as P0–P3 and puts important active items first.
- Separates upcoming actions, overdue follow-ups, active applications, offers, not-matched results, closed cases, expired cases, and planned applications.
- Preserves exact official status wording and asks the user instead of inventing missing facts.
- Syncs or exports to Feishu, Notion, Excel, GitHub Markdown, portable Markdown, and other cloud spreadsheets, databases, or documents.
- Supports Chinese, English, or optional bilingual presentation.
- Enforces deterministic category order, two-row spacing where supported, and a restrained single-color layout.

## Install

Copy the `job-application-manage-skill` folder into your Codex skills directory:

```text
~/.codex/skills/job-application-manage-skill
```

Then ask Codex to use `$job-application-manage-skill` to inspect recruiting updates and maintain your tracker.

## Privacy

The repository contains no personal tracker URLs, mailbox addresses, credentials, or application records. Keep private values in your local `references/user-config.md` and review repository visibility before publishing any generated tracker.
