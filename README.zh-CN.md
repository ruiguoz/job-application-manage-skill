# Job Application Manage 求职申请管理 Skill

[English](README.md) | [简体中文](README.zh-CN.md)

一个可复用的 Codex Skill，用于将招聘邮件、招聘官网、岗位页面和用户补充信息整理成统一、按优先级排序的求职申请流程。

## 功能

- 汇总并去重来自多个来源的求职申请。
- 使用 P0–P3 重要性等级排序，将重要且仍需处理的事项放在最前面。
- 区分未来安排、逾期跟进、进行中、Offer、暂不匹配、流程结束、已过期和投递意向。
- 保留招聘方的官方状态原文；信息缺失时询问用户，不编造日期或结果。
- 支持同步或导出到飞书、Notion、Excel、GitHub Markdown、通用 Markdown，以及其他云表格、云数据库和云文档。
- 支持中文、英文，以及可选的中英双语展示。
- 固定类目顺序；在支持的文档中，类目之间保持两行空白，并采用克制统一的单色样式。

## 安装

将 `job-application-manage-skill` 文件夹复制到 Codex 的 Skills 目录：

```text
~/.codex/skills/job-application-manage-skill
```

然后让 Codex 使用 `$job-application-manage-skill` 检查招聘动态并维护求职进度表。

## 隐私

本仓库不包含个人求职表链接、邮箱地址、账号凭据或真实投递记录。请将私人配置保存在本地的 `references/user-config.md` 中，并在公开任何生成的求职表之前检查仓库可见性。
