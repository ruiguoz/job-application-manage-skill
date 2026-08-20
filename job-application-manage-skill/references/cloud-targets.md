# Generic cloud-document targets

Use this adapter for a cloud service that is not covered by a dedicated section in `sync-targets.md`.

## Supported document models

Classify the target before mapping it:

1. **Cloud spreadsheet**
   - Examples: Google Sheets, Microsoft Excel Online in OneDrive or SharePoint, Tencent Docs spreadsheets, DingTalk spreadsheets, and similar grid-based services.
2. **Cloud database or smart table**
   - Examples: Airtable, Feishu Bitable, Coda tables, Notion databases, DingTalk smart tables, and similar property-based services.
3. **Cloud rich-text document**
   - Examples: Google Docs, Microsoft Word Online, Feishu Docs or Wiki pages, Yuque, Tencent Docs documents, DingTalk Docs, and similar block or page editors.

Examples indicate document models, not guaranteed installed integrations. Use only capabilities actually available in the current environment.

## Discovery and configuration

Resolve or ask for:

- Platform and target URL.
- Document model: spreadsheet, database, or rich-text document.
- Desired operation: create, update, one-way export, or two-way synchronization.
- Canonical tracker when more than one writable target exists.
- Target sheet, database, table, page, or managed section.
- Field or property mapping and presentation language.
- Sharing scope and whether the document may contain private recruiting links or personal data.

Inspect the target first and ask only about unresolved or ambiguous settings. Never assume that a shared link grants edit permission.

## Access method

Use this order:

1. Purpose-built connector or app.
2. Official API or authenticated CLI already configured by the user.
3. Signed-in browser session.

Do not install an integration, request broader permissions, or create credentials without the user's approval. Stop at login, CAPTCHA, access-request, payment, sensitive-data submission, and final-publish boundaries.

## Cloud spreadsheet mapping

- Map one application to one row and preserve the configured visible columns.
- Read headers and the managed range before writing; do not assume Excel-style column letters when the platform uses named fields.
- Apply the standard category order in the human-readable view.
- Keep exactly two blank rows between populated category blocks when the platform supports physical rows.
- If the platform has a separate structured data view, keep it continuous and place the spaced layout in a presentation view or sheet.
- Use one uniform light header/category fill and white data rows. If styling is unsupported, preserve structure without simulating colors with symbols.

## Cloud database or smart-table mapping

- Store Priority and Category as explicit select-like properties when possible.
- Store dates as date properties, links as URL properties, and timeline or notes as text properties.
- Prefer views grouped by Category and sorted by Priority, then the category-specific date.
- Do not create blank records to imitate category spacing. Use grouping or view separators instead.
- Do not add multiple category colors unless the user requests them.

## Cloud rich-text document mapping

- Maintain one managed tracker section with one heading per populated category.
- Render records as a native table when stable table editing is available; otherwise use compact labeled record blocks.
- Use two blank paragraphs or equivalent section spacing between categories. Do not add empty application records.
- Preserve user prose, comments, embeds, and blocks outside the managed section.
- Add managed-section markers only when the platform supports them safely or the user approves them.
- Use the configured language and a single restrained heading style; avoid mixed text or background colors.

## Verification

After every write:

- Read back every changed record and its Record ID or identity fields.
- Verify priority and category order, dates, language, links, and deduplication.
- Verify the platform-appropriate spacing rule and absence of accidental mixed styling.
- Report unsupported formatting or synchronization limitations instead of pretending they were applied.

