# Synchronization targets

## Shared synchronization rules

- Prefer a purpose-built connector, API, or authenticated CLI. Use a signed-in browser only when no reliable semantic interface is available.
- Designate one canonical tracker when multiple writable targets are enabled.
- Read all writable targets before writing. Reconcile by Record ID, then by company + role + business unit + location + application date.
- Resolve status from official recruiting sources, not from whichever tracker was edited most recently.
- Preserve target-specific user notes that do not contradict the normalized record.
- Synchronize normalized records, priority, and category values, then apply each target's presentation rules and configured language.
- Do not propagate deletion automatically. Ask the user when a record exists in only one target and its intended disposition is unclear.
- Record `Last checked` when the target schema supports it.
- For another cloud platform, read `cloud-targets.md`, classify its document model, and create an explicit field and layout mapping before the first write.

## Feishu spreadsheet

Use the configured Wiki or spreadsheet URL and managed range. Confirm the sheet name before writing.

On Windows, Lark CLI may be available at:

```powershell
& "$env:APPDATA\npm\lark-cli.cmd"
```

Clear proxy variables for Feishu requests when required. Prefer the Wiki URL with `--url`; do not assume the sheet ID is the spreadsheet token.

Useful operations:

- Read: `sheets +cells-get`
- Locate: `sheets +cells-search`
- Write tabular data: `sheets +csv-put`
- Style: `sheets +cells-set-style`
- Resize: `sheets +rows-resize`, `sheets +cols-resize`
- Structure: `sheets +dim-insert`, `sheets +dim-delete`

Check `--help` before unfamiliar operations. Use payload files for CSV or JSON to avoid shell quoting damage. Preview destructive commands, then confirm exact targets immediately before execution.

Represent category labels as ordinary rows within the managed columns. Keep all cells after the label in that row blank unless the configured template explicitly requires otherwise.

Map `Status query URL` to a dedicated URL or text column when available. Prefer a stable official applicant portal or application center. Do not store accept, reject, withdraw, submit, attendance-confirmation, one-time token, or credential-bearing links as query addresses.

When the audit footer is enabled, locate the existing `表格核对 / Audit` row and update it instead of appending another one. Keep exactly two blank rows after the final application record, then write the audit row as the last non-empty row with white or no fill and normal font weight.

## Notion database

Use a Notion database with properties mapped to the normalized fields. Prefer these property types:

- Company or Role: title property, according to the existing database.
- Priority: select, using P0 through P3 with bilingual labels when configured.
- Status / Next action: rich text.
- Category: select.
- Location: select or rich text.
- Application date and Last checked: date.
- Key timeline and Notes: rich text.
- Source link: URL.
- Status query URL: URL.
- Record ID: rich text.

Do not recreate a database or change property types without explicit approval. Ask for the database URL and property mapping when unavailable.

Use the fixed category order for a grouped view when the interface supports it. Notion views do not require physical blank rows; represent the same separation through category grouping and keep a single uniform light visual treatment. Do not add multicolor category options unless the user asks.

## Excel workbook

Use the `spreadsheets` skill when creating or editing `.xlsx` files. Ask for the workbook path and sheet mapping when unknown.

- Keep a normalized `Applications` worksheet as a continuous rectangular data table with one row per record and labels in the configured language.
- Include Priority and Category as explicit columns so the table can sort and filter reliably.
- Create or refresh a `Tracker View` worksheet for the human-readable categorized layout when requested.
- In `Tracker View`, use the fixed category order, exactly two blank rows between populated categories, one uniform light-blue fill for headers and category labels, and white data rows.
- Keep formulas, unrelated worksheets, named ranges, and user formatting outside the managed sheets intact.
- Read the saved workbook back and verify values, formulas, category spacing, widths, wrapping, and absence of mixed fills.

## GitHub-flavored Markdown

Ask for the repository and target `.md` path when unknown. Use this form when the tracker will be viewed or reviewed on GitHub.

- Write one level-one title and one section per populated category in the configured language.
- Under each category heading, write a GitHub-flavored Markdown table with the configured visible fields.
- Escape pipe characters and normalize embedded line breaks so every record remains one valid table row.
- Use relative repository links when appropriate; never expose private status URLs or personal data in a public repository without explicit approval.
- Keep exactly two blank lines between the end of one category table and the next category heading.
- Produce deterministic ordering and minimal diffs; update matching rows instead of rewriting unrelated prose.

## Portable Markdown

Ask for the target `.md` path when unknown. Use this form when the file must render well outside GitHub.

- Avoid GitHub-only tables, task-list semantics, HTML, and color markup.
- Write one heading per populated category and one compact record block per application in the configured language.
- Render fields as bold labels followed by plain text values. Use bilingual labels only when bilingual presentation is enabled.
- Keep exactly two blank lines between category sections and one blank line between application records.
- Preserve any user prose outside the managed tracker markers. Add stable start/end markers only with the user's approval when editing an existing document.

## Conflict handling

Ask the user when:

- Two records may describe the same application but differ in role, location, or date.
- Two writable targets contain conflicting user-authored notes.
- An official status is older than a newer user-provided update.
- A target requires an unmapped mandatory property.
- A structural change could delete or overwrite unrelated content.

