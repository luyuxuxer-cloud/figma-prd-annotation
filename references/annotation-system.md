# Figma Annotation System

Use this system when adding PRD-based annotations to Figma. Default to concise annotations that reduce ambiguity without creating reading friction.

## Annotation Principle

Annotate only what changes understanding, implementation, review, or risk.

Do annotate:

- Critical behavior that cannot be inferred from the UI.
- Important state or exception handling.
- Permission, data, metric, or business rule that affects the screen.
- PRD ambiguity that must be confirmed before handoff.

Do not annotate:

- Obvious static UI.
- Every field, label, or component.
- Repeated rules already explained once.
- Long PRD paragraphs.
- Nice-to-have commentary that does not affect decisions.

## Default Types

Use four types by default:

| Type | ID | Use for | Accent |
|---|---|---|---|
| 规则 | R-01 | behavior, permission, data, metric, business rule | Blue |
| 状态 | S-01 | loading, empty, error, disabled, no permission, pending, rejected | Orange |
| 异常 | E-01 | fallback, recovery, risk, compliance | Red |
| 待确认 | Q-01 | missing or ambiguous PRD rules | Yellow |

Use detailed subtypes only in an external index or handoff table, not as default canvas labels.

## Density Rules

- Aim for 3-7 annotations per normal frame.
- Use at most 10 annotations on a dense frame unless the user asks for detailed handoff.
- Prefer one annotation for a repeated rule, then reference it from related modules.
- If more than 10 notes are needed, create a compact "标注索引" frame and keep the canvas callouts minimal.
- Default annotation body: one sentence.
- Maximum body length: 36 Chinese characters or 22 English words where possible.

## Visual Style

Use lightweight callouts:

- Container: white or very light neutral fill, 1px neutral border.
- Radius: 6px.
- Padding: 8px.
- Width: 180-260px.
- Title row: ID + short type label.
- Body: one concise sentence.
- Connector: thin line only when target is not obvious.
- Font: 12px body, 13px title.

Use color as a small ID chip or left border. Keep the body neutral.

## Layout Rules

- Put notes outside the product frame when possible.
- Align notes in one tidy column beside the frame.
- Do not cover product UI.
- Avoid crossing connector lines.
- Keep open questions visually distinct but not visually loud.
- For multiple frames, annotate locally and keep numbering continuous across the flow.

## Content Examples

Good:

- `R-01 仅 Admin 可编辑预算，Operator 只读。`
- `S-02 无可用账户时展示空态并引导绑定。`
- `E-01 保存失败保留输入，提示重试。`
- `Q-01 PRD 未说明预算不足是否允许提交。`

Too heavy:

- "本模块用于帮助广告主在预算不足时理解当前投放计划的预算消耗情况，并支持后续进行预算调整、账户绑定、投放策略切换等操作。"
- "这里需要注意交互。"
- "此处展示数据。"

## Optional Detailed Index

When a detailed handoff is required, keep the canvas lightweight and add a separate index:

| ID | Type | Target | Rule | Owner/Confirm With |
|---|---|---|---|---|

The index may include PRD evidence, data source, event names, or engineering notes. Do not put all of that text into callout cards.

## Verification Checklist

Before delivery:

- Notes are few enough to scan quickly.
- Every note changes a decision or reduces ambiguity.
- Text is readable at normal zoom.
- Notes do not cover the UI.
- Connectors point to the right element.
- Open questions are separated from confirmed rules.
- The screenshot matches the final Figma state.
