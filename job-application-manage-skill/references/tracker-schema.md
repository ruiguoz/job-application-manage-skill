# Tracker schema and classification

## Contents

- Normalized fields
- Bilingual field labels
- Importance levels
- Ordered category rules
- Sorting inside categories
- Deterministic table layout

## Normalized fields

Use these logical fields even when a target exposes different column or property names:

| Field | Required | Notes |
| --- | --- | --- |
| Record ID | Preferred | Stable application ID; otherwise derive from normalized company, role, business unit, location, and application date. |
| Company | Yes | Official company or recruiting entity. |
| Role | Yes | Exact role title when available. |
| Priority | Yes | `P0 / 紧急`, `P1 / 重要`, `P2 / 一般`, or `P3 / 低`, followed by a concise reason. |
| Status / Next action | Yes | Preserve official status text and add the next user action when known. |
| Location | No | City first; retain broader location if city is unknown. |
| Application date | No | Do not substitute an email date unless it is clearly the submission date. |
| Key timeline | Yes | Chronological application, test, interview, deadline, and result events. |
| Category | Yes | Exactly one category from the ordered rules below. |
| Source | Preferred | Official portal, recruiting email, job page, or user notice. |
| Source link | No | Read-only status or job link when safe to retain. |
| Last checked | Preferred | Timestamp in the configured timezone. |
| Notes | No | Preserve user-authored notes and uncertainty. |

## Optional bilingual field labels

Use these labels when bilingual output is configured:

- `公司 / Company`
- `目标岗位 / Target Role`
- `重要性 / Priority`
- `当前状态与下一步 / Status & Next Action`
- `地点 / Location`
- `投递时间 / Application Date`
- `关键时间点 / Key Timeline`
- `来源 / Source`
- `最近核对 / Last Checked`

## Importance levels

Assign the highest level supported by evidence:

1. `P0 / 紧急`
   - The user explicitly marks it urgent, or an interview, assessment, attendance decision, or application deadline is due within 48 hours.
2. `P1 / 重要`
   - The user explicitly marks it important; it is a target employer or role; it strongly matches a priority city and role preference; it is already at interview/assessment stage; or a meaningful action is due within seven days.
3. `P2 / 一般`
   - It is a viable active application or intention without strong urgency or explicit strategic importance.
4. `P3 / 低`
   - Fit, location, timing, or user interest is weak, or the record is retained mainly for reference.

Ask when the evidence cannot distinguish between P1 and P2 and the distinction would change the first category. Never use employer prestige alone as evidence.

## Ordered category rules

Assign the first matching category. A record belongs to exactly one populated category.
Treat the text before `/` as the Chinese label and the text after it as the English translation. Render Chinese only, English only, or both according to the target's language setting.

1. `待处理·重要 / Priority Actions`
   - The record is non-terminal and has priority P0 or P1. State the concrete action; if it is waiting, use a truthful task such as `重点跟进 / Priority follow-up` and ask for a follow-up date when needed.
2. `待办·未来安排 / Upcoming Actions`
   - A confirmed future interview, assessment, response deadline, document deadline, or attendance decision exists.
3. `待跟进·时间已过 / Overdue Follow-up`
   - A scheduled event or promised response date passed and the outcome remains unknown.
4. `进行中·等待反馈 / Active — Waiting`
   - The application is active, submitted, screening, or waiting without a missed dated action.
5. `结果·Offer / 已录用 / Offer or Hired`
   - An offer, acceptance, or confirmed successful outcome exists.
6. `结果·暂不匹配 / Not Matched`
   - The source explicitly says `暂不匹配` or equivalent. Preserve the exact wording.
7. `流程结束·未通过或原因未明 / Closed — Rejected or Unclear`
   - The source explicitly rejects the application, or says the process ended without a reason.
8. `已撤回·已过期·不再处理 / Withdrawn, Expired, or Dropped`
   - The user withdrew, the deadline expired before submission, or the user confirmed no further action.
9. `投递意向·尚未投递 / Planned Applications`
   - The role or employer is only a plan, recommendation, or application intention.

Do not use an undifferentiated `历史` category. Represent why a record is no longer active.

## Sorting inside categories

- Sort by priority first: P0, P1, P2, P3.
- Priority actions: due date ascending, then company and role.
- Future arrangements: next action ascending, then company and role.
- Overdue follow-ups: missed date descending, then company and role.
- Active waiting: last checked descending, then application date descending.
- Offers and closed results: result date descending.
- Intentions: priority-city match first, then application deadline ascending, then company and role.

## Deterministic table layout

- Keep one top-level column-header row.
- Render each populated category as one category-label row followed immediately by its records.
- Keep no blank rows inside a category.
- Keep exactly two completely blank rows between the final record of one populated category and the label row of the next populated category.
- Omit empty categories. Do not leave placeholder spacing for them.
- Keep no decorative blank rows before the first category. After the last category, allow only the two blank rows required by an enabled audit footer.
- Use the same single light fill for the top header and every category-label row: default `#D9EAF7`, with dark text.
- Use no fill or plain white for all data rows and separator rows. Remove legacy category colors and accidental mixed fills inside the managed range.
- Do not use alternating row colors, gradients, conditional fill colors, or one color per category.
- Use bold text only for the top header and category-label rows. Freeze the top header, wrap text, use automatic row height, and keep readable column widths.
- Preserve content and formatting outside the configured managed range.

### Audit footer

- When enabled, keep exactly one audit metadata row as the last non-empty row of the tracker view.
- Keep exactly two completely blank rows between the final application record and the audit row.
- Include the configured-timezone timestamp, application-record count, checks performed, unresolved fields, and the next dated action or calendar state.
- Use white or no fill and normal font weight so the audit row cannot be mistaken for a header, category, or application record.
- Locate an existing audit row by its stable label, such as `表格核对 / Audit`, and update it in place. Do not append multiple audit rows.
- Keep table-wide audit metadata in the footer instead of repeating the audit timestamp in every application timeline.
- When the audit footer is disabled, leave no decorative blank rows after the final application record.

After every update, re-read the managed range and verify the category sequence, zero internal blank rows, exactly two inter-category blank rows, the uniform palette, and—when enabled—exactly two blank rows before one final audit row.

