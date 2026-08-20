# User configuration

Keep user-specific defaults here. Ask before changing a confirmed preference, and never commit real private tracker URLs, mailbox addresses, credentials, or recruiting links to a public repository.

## Sources

- Recruiting email: enable only when the user provides or connects a mailbox.
- Official applicant portals and job pages: enable when the user provides URLs or a signed-in browser is available.
- Default email lookback: 14 days unless the user chooses another period.
- Timezone: unknown; infer from reliable context or ask when date classification depends on it.

## Preferences

- Priority cities: unknown; ask the user.
- Location constraints: unknown; ask the user.
- Work-style preference: unknown; ask before using it for recommendations.
- Presentation language: preserve an existing target's language. For a new target, use the user's language unless they choose English-only or bilingual presentation.
- Importance: rank P0 through P3; move every non-terminal P0 or P1 record to the priority-actions category.

## Synchronization targets

No target is enabled by default. Enable only the targets the user supplies.

### Feishu spreadsheet

- URL, sheet, managed range, and field mapping: unknown; inspect or ask.
- Recommended visible fields: Company, Role, Priority, Status / Next Action, Location, Application Date, and Key Timeline.
- Represent Category with label rows unless the existing table uses a dedicated column.

### Notion database

- Database URL and property mapping: unknown; inspect or ask.

### Excel workbook

- Workbook path: unknown; ask when requested.
- Recommended normalized worksheet: `Applications`.
- Recommended human-readable worksheet: `Tracker View`.

### GitHub-flavored Markdown

- Repository and target path: unknown; ask when requested.
- Treat visibility as private until the user confirms the content is safe for a public repository.

### Portable Markdown

- Target path: unknown; ask when requested.

### Other cloud documents

- Platform, URL, document model, mapping, and synchronization direction: unknown; inspect or ask.
- Preserve the target's existing language and layout unless the user requests a migration.

## Presentation

- Use the fixed category order in `tracker-schema.md`.
- Keep exactly two blank rows between populated categories when the target supports physical rows.
- Use one uniform light header/category fill and white data rows; avoid mixed category colors.
- Preserve content and formatting outside the configured managed range or section.

